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

``