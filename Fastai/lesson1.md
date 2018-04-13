# Lesson 1


* classifier is looking at the a sqaure in the middle of the images
*


## Definitions

* **Training Set Loss** - Error from on training set
* **Validation Loss** -  Error from on validation set
* **Accuracy** - correct prediction from our test set

When we backpropagate we use our training set loss 

If our validation loss is greater then out training loss our model maybe overfitting.

## freezing layers

* frozen - not being updated
* unfreeze - being updated



only traing the last one/two layers as the first pretrained convolution/layers have been trained already and are very goood at recognising basic shapes and features. when we want to start fine tuning out network we can start un freezing layer by layer.


create an arry of learning rates for each group of layers super low learning rates for layers at the front , middle learning rates for middle layers and bigger learning rates for the last layers.


## .fit method

**Cylcle_len**- reset learning rate after _n_ number of epochs **cycle_len = n**

decrease our learning rate as we train _learning rate annealing_ we use **cosine-annealing**. We can use cosine-annealing to find a more generalise minima by doing _CA_ 3 times over a number of iterations. 
 
**_Insert Image from lesson_**.

**cycle_mult**  doubles length of cycle after each cycle

**_Insert Image from lesson_**.

## Choosing a leraning rate

_lrf_  uses minibatches to find the optimal leraning rate  

## Improving Model Through Data Augmentation

## Steps To Train Model
---

1. Enable data augmentation, and precompute=True
2. Use lr_find() to find highest learning rate where loss is still clearly improving
3. Train last layer from precomputed activations for 1-2 epochs
4. Train last layer with data augmentation (i.e. precompute=False) for 2-3 epochs with cycle_len=1
5. Unfreeze all layers
6. Set earlier layers to 3x-10x lower learning rate than next higher layer
7. Use lr_find() again
8. Train full network with cycle_mult=2 until over-fitting
