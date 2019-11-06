# Active Learning

### Uncertainty sampling

[Human in the loop chapter](https://livebook.manning.com/book/human-in-the-loop-machine-learning/chapter-3)

**Least confidence:** where the model selects those instances with the lowest confidence level to be labelled next.

**Margin  sampling:** select instances where the margin between the two most likely labels is narrow, meaning that the classifier is struggling to differentiate between those two most likely classes.

### Representative strategy

Information density in sample mean absolute difference or standard deviation between class size in crop

## Papers

[Geometry in active learning for binary and multi-class image segmentation](https://arxiv.org/pdf/1606.09029.pdf)

(1) maximum entropy of posterior probability distribution over classes, 
(2) minimal probability of selected class and 
(3) minimal gap between the two most probable classes. 

[Article](https://www.kdnuggets.com/2018/10/introduction-active-learning.html)
