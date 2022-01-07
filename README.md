# CrabsPrediction

### Team:
- Alina Muliak
- Olexiy Hoiev
- Oleksandra Stasiuk

### Introduction
Crab farming is practiced worldwide as true crabs make up 20% of all crustaceans caught and farmed in the world, with about 1.4 million tonnes being consumed annually. But there are some restrictions and challenges in profit based on when the crabs should be farmed. For a commercial crab farmer knowing the right age of the crab helps them decide if and when to harvest the crabs. Beyond a certain age, there is negligible growth in crab's physical characteristics and hence, it is important to time the harvesting to reduce cost and increase profit.

### Aim
The main purpose of this research is to provide farmers with information on age of the crabs based on their physical attributes, to help them decide on the most suitable time to harvest the crabs. Moreover, the goal is also to make this decision as easy and realistic as possible, relying on the minimum parameters getting accurate prediction.

### Analysis of the data
The main data set for the project consist of crab's physical characteristics, farmed in Boston area, that include sex, length, diameter, height, age, weight, shucked weight, viscera weight and shell weight.

First, we download necessary library and set seed to easier work with results.
```{r}
library(ggplot2)
set.seed(125368)
```

To prepare our data, as our goal is to help farmers harvest crabs, we leave out only those parameters, which farmers can estimate without killing the crabs: sex, length, diameter, height, weight and age.</br>
All the parameters' graphs shows strong relations, but on the height's graph there is almost no changes in dependence to others.
</br>
To further prepare the data, we split it in **2 parts**. First one we will need for **building a linear regression model**, and second will be for **testing**. As they are different, it will assure us of a better accuracy in our prediction.
</br>
The data set is not ideal, and in the parameter "sex" we have three categories - M stands for male, F - for female, and I - indeterminate. 
</br>
The female category is very different in both parameters from other two, but indeterminate is almost the same as male, which make us believe that farmers couldn't determine the sex of mainly male crabs.

### ANOVA Test
For building the prediction, we first need ANOVA test.
**ANOVA**, which stands for Analysis of Variance, is an extension of a t-test. It tells if there are any statistical differences between the means of three or more independent groups. Like the t-test, ANOVA helps to find out whether the differences between groups of data are statistically significant. It works by analyzing the levels of variance within the groups through samples taken from each of them.

F-value:
F = Between group variatioin/Within group variation</br>
If most of the variation comes from within groups, then 'some component' probably does not have much of any effect, however, if the variation seems most to come from between the groups, this would indicate that 'some component' does probably have an effect.

Thus, larger F-ratios indicate there's a high probability that the groups do have different means; in other words, it does make a difference.
High f-ratio combined with a small p-value means that 'some component' most likely does have an effect and we should reject the null hypothesis that the means are the same.

We **build different linear regression models**. As our goal is to minimize the use of parameters for farmers to decide easily, we compare linear model with all parameters and some without height, length and diameter. It will help us to see which one we can ignore while getting relatively accurate results.

1. First one considers all the parameters we're have in prepared data set.
2. Second is now with all parameters except for height.
3. Without length.
4. Without diameter.
5. Without diameter and height.

### Testing linear models
Now we are going to test our regression models on real data, which we reserved for testing. With that we will see how great is the change if we ignore some of parameters, and which ones are more important.


1. First, we test the model with all parameters included.
This is our base result that we will compare to others.

2. Test model without height parameter.
The result became a little worse but is still precise, in comparison to our base model. It is also seen on the prediction graph. Therefore, we can conclude that height is not that important and can be ignored by farmers.

3. Test model without length parameter.
Without length, our results became much worse, the value is different and graphs are further from each other in predicted and actual values. Therefore, we don't want to get rid of this parameter to get accurate results.

4. Test model without diameter parameter.
From this test we can see that probably diameter is not that important either, as the prediction does not changes strongly, so we can ignore it.

5. Test model without diameter and height parameters.
Finally, the last test we run on model without diameter and height, and we can conclude that they are not very important parameters to consider in harvesting crabs.


### Conclusion

In this research we built and tested our linear regression models on different sets of data. We discovered that for harvesting crabs effectively farmers need to consider many of their physical attributes, but to minimize the effort they can neglect the diameter and height and focus on parameters which are more important in predicting their age - length, weight, and sex of the crab.
