# Dog Breeds

* bacth size, start at 64 till out of memoery, then half , and half and half and so on

## Increasing size

* pass in a larger sized data (images)through a pretrained model

* starting traing on small images, then start on larger images, avoid over fitting.

* underfitting validiation loss is a lot less then training set loss => increase cycle_len

##

***tfms*** 
- how do we want to transform our model
- can change the train name ```trn_name=```  and validiation name ```val_name=``` of files in the ```tfms_from_model``` method and also include the test folder

## 

***Reading Information from csv*** _Lesson 3 34:27_

data=ImageClassifier.from_csv


***Using panads for writing txt file*** _lesson 3 35:31_