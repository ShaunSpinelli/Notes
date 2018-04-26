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

```python
md = ColumnarModelData.from_data_frame(PATH, val_idx, df, yl.astype(np.float32), cat_flds=cat_vars, bs=128, test_df=df_test)
```
* ```md``` = model data

* ```df ```= data frame -> independant variable

* ```yl``` = dependent

* ```cat_flds=cat_vars ``` = what do we want treated as catorgarical data

```python
m = md.get_learner(emb_szs, len(df.columns)-len(cat_vars),0.04, 1, [1000,500], [0.001,0.01], y_range=y_range)
```

* ```m``` is our model

* emb_szs is see **catergorical** section

* **num of continous variables**, just pass in all the df coloumns and subtract the catorigicl varibles

* 0.04 is drop out for embediding matrix

* 1 is how many outputs do we want (we want sales)

* activations in [first,second] linear layer

* drop out in [first,second] linear layer



**Catergorical**
create a new matrix *53:36min lesson 4* eg: days of the weeek. if we created a new 4x7 vectore matrix. Sunday will be represented by 4 floating point numbers, initially picked at random.

turned catogericl in a floating point vector  so we can update them when we use back prob

this is called an **embedding matrix** distributed representation.

finding the right embedding size. cardiality/2 but less then 50 . Which means, however many catogories you have divide by two, if its greater then 50 , make it 50.



49 drw some iamges from that

# Naturaltal Langauge Processing(NLP)

Tokenization breaks words into tokens.

fastai uses [spacy tokenisor](https://spacy.io/usage/spacy-101).

create a field, how we will preprocess text.

```python
    TEXT = data.Field(lower=True, tokenize="spacy")
```

```lower``` lower case

```tokenize``` what tokenizer we are using

while creating our model data

```min_freq=n``` is any words the occur less then ```n``` times dont treat as work.

```bptt``` baack propagation through time . how long of a sentence do we send through to the gpu each time.

***vocab***, what are the list f unique words that appear.

map a word to an integer

#restart lesson at 1:50