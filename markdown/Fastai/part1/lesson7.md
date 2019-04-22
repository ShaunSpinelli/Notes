# Lesson 7

[Lesson 7 Wiki](http://forums.fast.ai/t/wiki-lesson-7/9405)

* fist half in rnn


batch normalization

semantic segmentation

## Computer vision - starts at 1:02

Cifar 10 - small data set of images with images of small sizes

stats - mean and standard deviation of channel (we need this no normalise data)

tfms - transform data

line 9 - creating a customer learner just a fully connected model

---
fully convelutional network

create a CNN- convolution

stride 2 conv. we move the kernel by two so we end up halving the resolution

adaptive max pool- last layer we do a maxpool just specify what size we want the output image second last we make a 1x1 max pool

then put it in a linear layer with output to amount of classes

---

padding- so we can get the feature at the edges of the image

---

[Batch norm](https://www.youtube.com/watch?v=dXB-KQYkzNU)

pick up lesson at 1:56

