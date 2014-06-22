# Practical Machine Learning - Human Activity Recognition
[Author: Prashant Ratnaparkhi]


```
## [1] "Sun Jun 22 07:57:06 2014"
```

```
## Warning: package 'caret' was built under R version 3.0.3
```

```
## Loading required package: lattice
```

```
## Warning: package 'lattice' was built under R version 3.0.3
```

```
## Loading required package: ggplot2
```

```
## [1] 19622    60
```

```
## [1] 20 60
```

```
## [1] 11776    53
```

```
## [1] 7846   53
```

```
## [1] "Sun Jun 22 07:57:25 2014"
```

```
## Loading required package: randomForest
```

```
## Warning: package 'randomForest' was built under R version 3.0.3
```

```
## randomForest 4.6-7
## Type rfNews() to see new features/changes/bug fixes.
```

```
## Warning: package 'e1071' was built under R version 3.0.3
```

```
## [1] "Sun Jun 22 09:53:26 2014"
```

```
## [1] "Sun Jun 22 11:48:00 2014"
```

```
##           
## predTrain1    A    B    C    D    E
##          A 3348    0    0    0    0
##          B    0 2279    0    0    0
##          C    0    0 2054    0    0
##          D    0    0    0 1930    0
##          E    0    0    0    0 2165
```

```
## [1] 0
```

```
##        
## predCV1    A    B    C    D    E
##       A 2231    7    0    0    0
##       B    1 1503   13    0    0
##       C    0    8 1353   35    3
##       D    0    0    2 1249    4
##       E    0    0    0    2 1435
```

```
## [1] 0.009559
```

```
##          
## predTrain    A    B    C    D    E
##         A 3348    0    0    0    0
##         B    0 2279    0    0    0
##         C    0    0 2054    0    0
##         D    0    0    0 1930    0
##         E    0    0    0    0 2165
```

```
## [1] 0
```

```
##       
## predCV    A    B    C    D    E
##      A 2231    7    0    0    0
##      B    1 1503   13    0    0
##      C    0    8 1352   37    3
##      D    0    0    3 1247    3
##      E    0    0    0    2 1436
```

```
## [1] 0.009814
```

```
## [1] "Sun Jun 22 11:48:07 2014"
```


The goal of the project is to predict the manner in which the participants did the 
exercise. This is the "classe" variable in the training set.

## Pre-processing of the input data.  
Remove records with NA values from both training and test datasets. 
Create the required subset of data - many columns (specifically, the derived ones) are empty or NA in the test data set. So remove such columns from both - training & 
test data sets.  These columns can not be used as features for traininig, as they are 
derived and are absent from the given test data.
The first 7 columns are - X, user_name, raw_timestamp_part_1, raw_timestamp_part_2, cvtd_timestamp, new_window, and num_window. These are not the actual readings/measurements and so not used as features for training. Hence, remove first 7 columns, as they will not be part of the model.

This gives 52 features (13 readings each, from the four - arm, belt, forearm and dumbbell - sensors). 

Out of this trainig set, keep aside 40% for cross validation/evaluation, and to calculate the out of sample error rate. 

## Training and model selection. 
First train a linear model (lm) using train function. 
Then train a random forest model using train function.
Comapre the two models for in-sample and out-of-sample errors.
Here the out-of-sample error rates are calculated using the cross validation 
data set - set aside from the training data set itself.

Note: Both the models are trained using all the 52 features to predict 'classe'

1) Comparison of the two models

The in-sample error rate for linear model is 0.

The out-of-sample error rate for linear model is 0.0096.

The prediction table for linear model on cross validation set is printed below:


The in-sample error rate for random forest model is 0.

The out-of-sample error rate for random forest model is 0.0098.

The prediction table for random forest model on cross validation set is printed below:


Both the models have same in-sample error rates. However, out-of-sample error rate for random forest model is lower than liner model. Hence random forest model is used for our purposes here. This, rf model is then used to predict the values of classe on the test dataset. 

