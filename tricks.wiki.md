# Deep Learning Pratical tricks

### gradients w.r.t. input is too small

use larger loss_weights, e.g. 20, 100 ...

### training loss explods or diverges

use clip_gradients, usually 10~100, the absolute value does not really matters

### training loss is not stable

randomly reordering the input samples in each epoch

