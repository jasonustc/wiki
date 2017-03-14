# Deep Learning Practical Tricks

Any suggestion please contact <shenxuustc@gmail.com>

### gradients w.r.t. input is too small

use larger loss_weights, e.g. 20, 100 ...

### training loss explods or diverges
use clip_gradients, usually 10~100, the absolute value does not really matters.

randomly reorder samples. 

check the network settings, e.g. data and label correctness, whether number of output is right.

set debug_info: true in solver to monitor the progress of gradients and data.

smaller learning rates.

### training loss is not stable

randomly reordering the input samples in each epoch.

### how many epoch is enough for training

generally 4-100 epoches is enough, we can mainly refer to training loss and validation accuracy curves.

for fine-tuning, we need less epoches and smaller learning rate.

- training

> **MNIST**  10,000 iterations * 64 batch_size / 60,000 = 6.4 epochs

> **ImageNet** 450,000 iterations * 256 batch_size / 1,280,000 = 22.5 epochs

- fine-tuning

### training loss oscillation

gradient clip, random permutation of samples, smaller learning rate.


### general setting of learning parameters

learning rate: 1e-1 ~ 1e-6

momentum: 0.9 ~ 1

weight_decay: 1e-4 - 1e-6

### general pre-processing tricks

whitening, local contrast normalization, scaling, cropping, rotation, clipping, ZCA normalization

### the scale of the model

usually, # of parameters should be in the same order of magnitudes as the # of samples.

halve the size of feature maps, double the # of feature maps.

### how to set kernel size and stride in deconvolution layer

kernel size should be twice as much as the stride.

### help model to converge faster

weights of innerproduct layers should be initialized 10 times of convolutional layers.

weight_decay and momentum also helps.

bias of last inner_product layer should be initialized with non-zeros.

### convolutional filter size selection
3, 5, 7, 9, 11, which is better? maybe a compromise between local patch size and input size, maybe a constant ratio.
From VGG net we can see that, 3 is OK for deep enough models.

### usage of validation set

first use validation accuracy for parameter selection, then incorporate it into training until training loss restores to that of no-validation training. 

iterate the model for at most 1 epoch, you can determine how this setting works.

### momentum
when input data have random things, smaller or no momentum is better, otherwise, we should use regular momentum.

### batch_size 
not the bigger the better, maybe there is a balance between the times of update of model for each epoch and the involved number of samples for each update.

> **MNIST** 60,000 / 64 =  937.5 / 64 = 14.65

> **ImageNet** 1,280,000 / 256 = 5000 / 256 = 19.53

smaller batch size incooperate more stochasitic things, which acts as a type of noise regularization. Could be better.

### weird crash of executable
recompile the exe first.

index out of range for GPU memory visiting.

### with nans
log(0) or a / 0

### overfitting?
reduce the # of parameters in fc layers, try mean-pooling to reduce the size of a single feature map, and 1x1 convolution to reduce the # of feature maps.

### fast way to check if the model is reasonable
random sample a small portion of dataset, see if the model can overfitting on it.
