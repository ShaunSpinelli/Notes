# Lesson 1- Images Classification using CNN

[Lesson 1 Wiki](http://forums.fast.ai/t/wiki-lesson-1/9398)

* classifier is looking at the a sqaure in the middle of the images

## Definitions

* **Training Set Loss** - Error from on training set
* **Validation Loss** -  Error from on validation set
* **Accuracy** - correct prediction from our test set
* **TTA** - test time augmentation running augmented images throw cnn to see how well its good

When we backpropagate we use our training set loss.

If our validation loss is greater then out training loss our model is **overfitting**.

### freezing layers

* **frozen** - not being updated
* **unfreeze** - being updated

Only training the last one/two layers as the first pre-trained convolution/layers have been trained already and are very good at recognising basic shapes and features. when we want to start fine tuning out network we can start un freezing layer by layer.

We can create an array of learning rates for each group of layers super low learning rates for layers at the front , middle learning rates for middle layers and bigger learning rates for the last layers.

### .fit method

**Cylcle_len**

* decrease our learning rate as we train _learning rate annealing_ we use **cosine-annealing** when ever we add ```cycle_len=``` to the .fit method params. We can use cosine-annealing to find a more generalise minima by doing _CA_ n times over a number of iterations.

* reset learning rate after _n_ number of epochs **cycle_len = n**

* If your cycle length is to short, wont find a good spot, it will keep popping out but as you go on you want it to do more and more exploring **need more research**

**_Insert Image from lesson 1_**

**cycle_mult**  doubles length of cycle after each cycle

**_Insert Image from lesson 1_**

### inputs

* inputs to model has to be square
* just using a square on the validation set, takes the height then crops out the rest

### Choosing a learning rate

_lrf_  uses mini-batches to find the optimal learning rate

### Improving Model Through Data Augmentation

### confusion matrix

* lets us compare our prediction labels and true labels

## Steps To Train an image Classifier

---

1. Enable data augmentation, and precompute=True
2. Use lr_find() to find highest learning rate where loss is still clearly improving
3. Train last layer from precomputed activations for 1-2 epochs
4. Train last layer with data augmentation (i.e. precompute=False) for 2-3 epochs with cycle_len=1
5. Unfreeze all layers
6. Set earlier layers to 3x-10x lower learning rate than next higher layer
7. Use lr_find() again
8. Train full network with cycle_mult=2 until over-fitting
