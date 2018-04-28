# Lesson 4

We've been added two fully connected layer by default

If we want to add a custom amount we can by adding ```xtra_fc=[]``` when we set up our learn model.

```python
learn = ConvLearner.pretrained(arch,data, xtra_fc[])
```

**DROP OUT**

Default is 0.25 for first and 0.5 by second

* solved genrealising

* each mini bacth switch off a random set of activations

setting up our learn model looks like

```python
learn = ConvLearner.pretrained(arch,data, ps=0.5, precompute=True)
``` 

In this example ```ps = 0.5``` the probability of deleting activation is 50% (turn off half). We can pass in array for ps value for each layer.

* higher vs lower p value


**Structured Data**, data you would find in tables or data bases.

Catergorical vs Continuous 

better to change to catergorical

Setting up our model data looks like

```python
md = ColumnarModelData.from_data_frame(PATH, val_idx, df, yl, cat_flds=cat_vars, bs=128, test_df=df_test)
```

where

* ```md``` = model data

* ```df ```= data frame -> independant variable

* ```yl``` = dependent

* ```cat_flds=cat_vars ``` = what do we want treated as catorgarical data

setting up leaner model

```python
m = md.get_learner(emb_szs, len(df.columns)-len(cat_vars),0.04, 1, [1000,500], [0.001,0.01], y_range=y_range)
```
where

* ```m``` is our learning model

* emb_szs is see **catergorical** section

* **num of continous variables**, just pass in all the df coloumns and subtract the catorigicl varibles

* 0.04 is drop out for embediding matrix

* 1 is how many outputs do we want (we want sales)

* activations in [first,second] linear layer

* drop out in [first,second] linear layer



**Catergorical**

Create a new matrix *53:36min lesson 4* eg: days of the weeek. if we created a new 4x7 vectore matrix. Sunday will be represented by 4 floating point numbers, initially picked at random.

Turned catogericl in a floating point vector  so we can update them when we use back prob

This is called an **embedding matrix** distributed representation.

Finding the right embedding size. cardiality/2 but less then 50 . Which means, however many catogories you have divide by two, if its greater then 50 , make it 50.



49min draw some iamges from that

# Naturaltal Langauge Processing(NLP)

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

**Batch size** total amount of data divded into smaller portio eg batch sixe of 64, we dived that size of our data into 64 batches.End up 64 columns by a large number 1:50

get image to display this concept

```bptt``` baack propagation through time . how long of a sentence do we send through to the gpu each time.

***vocab***, what are the list f unique words that appear.

map a word to an integer

