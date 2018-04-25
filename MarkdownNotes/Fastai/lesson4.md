# Lesson 4

We've been added two fully connected layer by default

If we want to add a custom amount we can by adding ```xtra_fc=[]``` when we set up our learn model.

```python
learn = ConvLearner.pretrained(arch,data, xtra_fc[])
```

**DROP OUT**

Default is 0.25 for first and 0.5 by second

* solved genrealising

* each mini bacth throw a random set of activations

when setting up our learn model

```python
learn = ConvLearner.pretrained(arch,data, ps=0.5, precompute=True)
``` 

In this example ```ps = 0.5``` the probability of deleting activation is 50% (turn off half) can pass in array for ps value for each layer.

* higher vs lower p value


**Structured Data**
Stuff youd find in data tables
catergorical vs continuous 

better to change to catergorical



## Readings
[Learnig rates](https://techburst.io/improving-the-way-we-work-with-learning-rate-5e99554f163b)

[Gradient Decent with restarts](https://medium.com/38th-street-studios/exploring-stochastic-gradient-descent-with-restarts-sgdr-fa206c38a74e)

[Transfer Learning/Differential LR](https://towardsdatascience.com/transfer-learning-using-differential-learning-rates-638455797f00)