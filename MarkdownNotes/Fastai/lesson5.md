# Lesson 5

[Lesson 5 Wiki](http://forums.fast.ai/t/wiki-lesson-5/9403)

## Topics

* Matrix's Decomposition

* weight decay

Collaborative filter in movies example. Trying to find out if a user_1 would like a movie. Did other people who like similar movies to user_1 like this movie and  movies that were liked by people like user_1.

pytorch module

create a torch tensor **what is a torch tensor**

```python
a = T([[1.,2],[3,4]])
b = T([[2.,2],[10,10]])
```

where ```a``` and ```b``` are torch tensors

 building a neural net layer , **pytorch module**

```python
class DotProduct(nn.Module):
    def forward(self, u, m): return (u*m).sum(1)

model=DotProduct()

model(a,b)
```

```DotProduct``` is inheriting from ```nn.Module```

## Movie Example using Collaborative Filtering

User ids may not be continuos ie: could have ids ranges from 1 to 100 but there may be some missing.So we not want to use the user id to look up the matching tensor column. So instead we  use the uniq user ids and match them to a new set of continuos user ids._The same process and be used for movies_

```python

u_uniq = ratings.userId.unique()
user2idx = {o:i for i,o in enumerate(u_uniq)}
ratings.userId = ratings.userId.apply(lambda x: user2idx[x]) #replace user_id column with continuous index

m_uniq = ratings.movieId.unique()
movie2idx = {o:i for i,o in enumerate(m_uniq)}
ratings.movieId = ratings.movieId.apply(lambda x: movie2idx[x])

n_users=int(ratings.userId.nunique())
n_movies=int(ratings.movieId.nunique())

```

Our user and movie id's have no been mapped to continuos integers

Creating he embedding matrix

```python

class EmbeddingDot(nn.Module):
    def __init__(self, n_users, n_movies):
        super().__init__()
        self.u = nn.Embedding(n_users, n_factors)#(rows,columns)
        self.m = nn.Embedding(n_movies, n_factors)
        self.u.weight.data.uniform_(0,0.05) #setting the values in the embedding matrix
        self.m.weight.data.uniform_(0,0.05) #randomly initalized embbede weight matrices

    def forward(self, cats, conts):
        users,movies = cats[:,0],cats[:,1]
        u,m = self.u(users),self.m(movies)
        return (u*m).sum(1)

```

using [Kaiming He initializing](http://www.jefkine.com/deep/2016/08/08/initialization-of-deep-networks-case-of-rectifiers/) to find the starting values for the embedding matrix.

Actual embedding matrix is not a tensor but a variable but it also does automatic differentiation

Creating our data

```python

x = ratings.drop(['rating', 'timestamp'],axis=1)
y = ratings['rating'].astype(np.float32)
data = ColumnarModelData.from_data_frame(path, val_idxs, x, y, ['userId', 'movieId'], 64)

```
Setting our model and opt.

```python

wd=1e-5
model = EmbeddingDot(n_users, n_movies).cuda()
opt = optim.SGD(model.parameters(), 1e-1, weight_decay=wd, momentum=0.9)

```
where

* model is our embedding matrix

* opt is updated our weights

* ``wd`` weight decay , change loss function


fastai fit function

```python

fit(model, data, 3, opt, F.mse_loss)

```

We can set our own learning rate annealing  ```set_lrs(opt, 0.01)```

Adding a bias 1:02:40

```.squeeze``` adds an additional unit axis. (pytorch function) Called broadcasting (we add a vector to a matrix) google **numpy broadcasting**
