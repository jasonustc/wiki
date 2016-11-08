# Deep Learning Pratical tracks

### gradients w.r.t. input is too small

use larger loss_weights, e.g. 20, 100 ...

### training loss explods or diverges

use clip_gradients, usually 10~100, the absolute value does not really matters

