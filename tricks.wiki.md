# Deep Learning Practical Tricks

### gradients w.r.t. input is too small

use larger loss_weights, e.g. 20, 100 ...

### training loss explods or diverges

use clip_gradients, usually 10~100, the absolute value does not really matters.

### training loss is not stable

randomly reordering the input samples in each epoch.

### how many epoch is enough for training

generally 4-100 epoches is enough, we can mainly refer to training loss and validation accuracy curves.

for fine-tuning, we need less epoches and smaller learning rate.

### training loss oscillation

gradient clip, random permutation of samples, smaller learning rate.


### general setting of learning parameters?

learning rate: 1e-1 ~ 1e-6

momentum: 0.9 ~ 1

weight_decay: 1e-4 - 1e-6

### general pre-processing tricks

whitening, local contrast normalization, scaling, cropping, clipping
