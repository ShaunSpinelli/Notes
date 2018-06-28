# Lesson 3

[Lesson 3 Wiki](http://forums.fast.ai/t/wiki-lesson-3/9401)

* Note: content starts at 45min *

* **rectified linear unit**(relu)- max(0,sum) in excel

Takes the on the positive unit which gives it the horizontal edges

* max pull

* **tensor** - is an array with more dimensions so we can stack kernals together 

* they are multi dimensional

kernals/filters are being used on multiple the convulsions that are created before it


* **Max Pooling**- using 2 by 2 pooling we would have the half resolution(replace four (numbers) cells with the biggest number)

* **Fully connected layer** - sum product of every activation by each weight(using weight matrix). _Don't use these much anymore_


* **Activation function** - eg: softmax. Takes in 1 number spits out another number, nonlinearity **find a better definition**

**Softmax** binary classification (single label)

_insert image of softmax eq_

## Multi label Image classification

Starts lesson3 3 1:20

Satellite imagery can have things many labels like weather, agriculture, primary (rain forest) water

**Sigmoid** use for multi variable classification(multiple label)

$$s(x)= \frac{e^x}{e^x+1}$$

![Sigmoid Function Graph](https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/Logistic-curve.svg/320px-Logistic-curve.svg.png)


---

`learn.summary()` shows us our model

## Structure of Data

---

* unstructured -all the data is the same thing eg pictures sounds waves

* structured - database type of structure



## Check out

* keras lesson 1 to see lesson one written using keras
* multi dimensional array
* convolution slide
* logs rules and e
