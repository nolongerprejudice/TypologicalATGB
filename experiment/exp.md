this file was created to explain the status of experiments and note the questions for meeting

q1#. how to organize this repo?

for now, the memory of GPU gets problematic becuase our memory capacity of GPUs are around 12.036~16.28GiB and will be less for actualy capacity.

For now, when I tried to plot learning rate to find out optimal learning rate, the GPU gets out of memory.(I didn't tried fine-tune withoug finding the optimal lr)

I need about 6.61GiB capacity more to finding learing rate(which runs the batches through differnt learning rates and evaluates loss)

Evaluating loss is not that heavy(because it just measures loss, not back prop)[^1], but it seems torch reserves memory for afterwards process resulting no capacity for finding learning rate. 

So the supposed solution is to reserve space before i call pytorch, or lessen the amount of reservations when pytorch trains. For example, when you do fine-tune, you don't need to back prop for the pre-trained layers.[^2]

Since I am using pytorch as a framework, I need to adjust `autograd` 

[^1]: Not sure
[^2]: But still can's sure if I can do unfreeze and learn the params     
