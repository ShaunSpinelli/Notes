# Lesson 4

[Lesson 4 Wiki](http://forums.fast.ai/t/wiki-lesson-4/9402)

We've been added two fully connected layer by default

If we want to add a custom amount we can by adding ```xtra_fc=[]``` when we set up our learn model.

```python
learn = ConvLearner.pretrained(arch,data, xtra_fc=  [])
```

**DROP OUT** - Default is 0.25 for first and 0.5 for second layer.

* helps model generalise more.

* each mini batch switch off a random set of activations

setting up our learn model looks like

```python
learn = ConvLearner.pretrained(arch,data, ps=0.5, precompute=True)
``` 

In this example ```ps = 0.5``` the probability of deleting activation is 50% (turn off half). We can pass in array for ps value for each layer.

We can pass in an array for different drop on different layers eg: `ps=[0.25,0.5]`

* higher vs lower p value

## Structured Data, 

Data you would find in tables or data bases.

Categorical vs Continuous, better to change to categorical.

Setting up our model data looks like 


fastai proc_df()


```python
md = ColumnarModelData.from_data_frame(PATH, val_idx, df, yl, cat_flds=cat_vars, bs=128, test_df=df_test)
```

where

* PATH  store anything we save from our model

* ```md``` = model data

* ```df```= data frame -> independent variable

* ```yl``` = dependent

* ```cat_flds=cat_vars``` - what do we want treated as categorical data

setting up leaner model

```python
m = md.get_learner(emb_szs, len(df.columns)-len(cat_vars),0.04, 1, [1000,500], [0.001,0.01], y_range=y_range)
```

where

* ```m``` is our learning model

* emb_szs is see **categorical** section

* **num of continuous variables**, just pass in all the df columns and subtract the categorical variables

* 0.04 is drop out for embedding matrix

* 1 is how many outputs do we want (we want sales)

* activations in [first,second] linear layer

* drop out in [first,second] linear layer

## Continuous




## Categorical

Create a new matrix *53:36min lesson 4* eg: days of the week. if we created a new 4x7 vector matrix. Sunday will be represented by 4 floating point numbers, initially picked at random.

Turned categorical in a floating point vector  so we can update them when we use back propagation

This is called an **embedding matrix** distributed representation.

Finding the right embedding size. cardinality/2 but less then 50 . Which means, however many catagories you have divide by two, if its greater then 50 , make it 50.

49min draw some images from that

##

## Natural Language Processing(NLP)

**Language modelling** - a model that can predict the next word in a sentence given a few words of a sentence

torch text is pytroches nlp

Tokenization breaks words into tokens.

Fastai uses [spacy tokenisor](https://spacy.io/usage/spacy-101).

Create a field, how we will preprocess text.

```python
    TEXT = data.Field(lower=True, tokenize="spacy")
```

```lower``` lower case

```tokenize``` what tokenizer we are using

while creating our model data

```min_freq=n``` is any words the occur less then ```n``` times dont treat as work.

**Batch size** total amount of data divided into smaller portion eg batch size of 64, we dived that size of our data into 64 batches.End up 64 columns by a large number 1:50

get image to display this concept (1:48:43) Question at 1:50 about batch size and bptt

```bptt``` back propagation through time . how long of a sentence do we send through to the gpu each time.

**vocab**,  is the list of unique words that appear.

map a word to an integer
