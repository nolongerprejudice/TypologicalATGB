this file was created
- explain the status of experiments
- note the questions for meeting

q1#. how to organize this repo?

### Current Issue

The memory of GPU gets problematic becuase our memory capacity of GPUs are around 12.036~16.28GiB and will be less for actualy capacity.

For now, when I tried to plot learning rate to find out optimal learning rate, the GPU gets out of memory.(I didn't tried fine-tune withoug finding the optimal lr)

I need about 6.61GiB capacity more to finding learing rate(which runs the batches through differnt learning rates and evaluates loss)

Evaluating loss is not that heavy(because it just measures loss, not back prop)[^1], but it seems torch reserves memory for afterwards process resulting no capacity for finding learning rate. 

So the supposed solution is to reserve space before i call pytorch, or lessen the amount of reservations when pytorch trains. For example, when you do fine-tune, you don't need to back prop for the pre-trained layers.[^2]

To solve the issue, need to read articles for understaning how GPU works in PyTorch, [forums - reseving gpu memories](https://discuss.pytorch.org/t/reserving-gpu-memory/25297), [docs - Augograd Mechanics](https://pytorch.org/docs/master/notes/autograd.html)


### 1. Architecture of the model

Encoder and decoder would be GRU, for light weight training

Will use fasttext, not pre-trained language model

---

Footnotes

[^1]: Not sure
[^2]: But still can's sure if I can do unfreeze and learn the params     
