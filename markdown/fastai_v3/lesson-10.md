# Notes

Rough notes

- overview of callbacks
- partial python function [docs](https://docs.python.org/2/library/functools.html#functools.partial)

## Variance

- how far a data point is from the mean

- Different ways to measure variance

variance - how far is the value from the mean, square that to get rid of negatives
`np.mean(np.square(x-mean))`

standard deviation (std) - more sensitive to outlier because you are squaring values
`np.sqrt(np.mean(np.square(x-mean)))

mean absolute deviation - instead of multiplying to get rid of the negatives we just take there absolute values,
`np.mean(np.absolute(x-mean))`

covarince - tells us if variables are positively or neagative correlated there is no mean atributed
to the  size of the result. `np.mean((x - xmean)*(y-ymean))` to solve this enter **correlation**

correlation - results in a number  lies in a range from -1 to 1. 1 indicates posiitve correlation, -1 a negative correlation

`np.mean((x - xmean)*(y-ymean))/ np.sqrt(np.mean(np.square(x-mean))* np.mean(np.square(y-ymean)))`

## Loss

Softmax vs binary loss

softmax assumes there is always a class present in the image and
?? will always look to maximise a prediction?? .This becomes and issue when data contains muliple classes or no classes.

muliti-label binary classification is the likelehood that data contains a class and is independent
from the other class logits. You can have two classes with the same likilehood in a sample.

## Callbacks and hooks

using callbacks and hooks to inspect model activations including the

## Nomralisation in the model

Why do we need to do it?

**Types:**
- Batch norm [Paper](https://arxiv.org/pdf/1502.03167.pdf)
- Layer norm
- Instance norm
- Group norm [Paper](https://arxiv.org/pdf/1803.08494.pdf)

Jermeys running-batch-norm