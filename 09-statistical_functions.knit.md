# Using the stats functions in R

## About this chapter
1. Questions:
- How do I do some common test?
2. Objectives:
- Using `t.test()` and calculating effect sizes
- Using `lm()` for regression
- Doing ANOVA with a linear model
3. Keypoints: 
- There are a range of functions for doing every statistical test in R.


R is built for statistics so in this section we'll look at some common statistics functions. 

First just getting the summary or descriptive statistics. 

## Summary Statistics 

Earlier we saw that R has very many ways to get summary statistics like the mean and standard deviation from entire datasets. These ranged from the `summary()` function. 


```r
 summary(iris)
```

```
##   Sepal.Length    Sepal.Width     Petal.Length    Petal.Width   
##  Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100  
##  1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300  
##  Median :5.800   Median :3.000   Median :4.350   Median :1.300  
##  Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199  
##  3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800  
##  Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500  
##        Species  
##  setosa    :50  
##  versicolor:50  
##  virginica :50  
##                 
##                 
## 
```

But a better way to summarise by factor is with the `describeBy()` function in the `psych` package. Note you need to use `$` notation to describe the column with the factor you want to subset with. 


```r
library(psych)
describeBy(iris, iris$Species)
```

```
## 
##  Descriptive statistics by group 
## group: setosa
##              vars  n mean   sd median trimmed  mad min max range skew
## Sepal.Length    1 50 5.01 0.35    5.0    5.00 0.30 4.3 5.8   1.5 0.11
## Sepal.Width     2 50 3.43 0.38    3.4    3.42 0.37 2.3 4.4   2.1 0.04
## Petal.Length    3 50 1.46 0.17    1.5    1.46 0.15 1.0 1.9   0.9 0.10
## Petal.Width     4 50 0.25 0.11    0.2    0.24 0.00 0.1 0.6   0.5 1.18
## Species*        5 50 1.00 0.00    1.0    1.00 0.00 1.0 1.0   0.0  NaN
##              kurtosis   se
## Sepal.Length    -0.45 0.05
## Sepal.Width      0.60 0.05
## Petal.Length     0.65 0.02
## Petal.Width      1.26 0.01
## Species*          NaN 0.00
## -------------------------------------------------------- 
## group: versicolor
##              vars  n mean   sd median trimmed  mad min max range  skew
## Sepal.Length    1 50 5.94 0.52   5.90    5.94 0.52 4.9 7.0   2.1  0.10
## Sepal.Width     2 50 2.77 0.31   2.80    2.78 0.30 2.0 3.4   1.4 -0.34
## Petal.Length    3 50 4.26 0.47   4.35    4.29 0.52 3.0 5.1   2.1 -0.57
## Petal.Width     4 50 1.33 0.20   1.30    1.32 0.22 1.0 1.8   0.8 -0.03
## Species*        5 50 2.00 0.00   2.00    2.00 0.00 2.0 2.0   0.0   NaN
##              kurtosis   se
## Sepal.Length    -0.69 0.07
## Sepal.Width     -0.55 0.04
## Petal.Length    -0.19 0.07
## Petal.Width     -0.59 0.03
## Species*          NaN 0.00
## -------------------------------------------------------- 
## group: virginica
##              vars  n mean   sd median trimmed  mad min max range  skew
## Sepal.Length    1 50 6.59 0.64   6.50    6.57 0.59 4.9 7.9   3.0  0.11
## Sepal.Width     2 50 2.97 0.32   3.00    2.96 0.30 2.2 3.8   1.6  0.34
## Petal.Length    3 50 5.55 0.55   5.55    5.51 0.67 4.5 6.9   2.4  0.52
## Petal.Width     4 50 2.03 0.27   2.00    2.03 0.30 1.4 2.5   1.1 -0.12
## Species*        5 50 3.00 0.00   3.00    3.00 0.00 3.0 3.0   0.0   NaN
##              kurtosis   se
## Sepal.Length    -0.20 0.09
## Sepal.Width      0.38 0.05
## Petal.Length    -0.37 0.08
## Petal.Width     -0.75 0.04
## Species*          NaN 0.00
```
With this you can get a nice, comprehensive table of summary statistics across all the numerical columns, divided by the chosen factor.

For combinations of factors, you can use the `ddply()` function in the `plyr` package. Here you can choose a list of factors to summarise, but you must name the output columns and the R function to use. Helpfully the R function for a mean is `mean()` and the function for standard deviation is `sd()`.

Here, we divide up on `cut` and `colour` using the make-a-list function `c()`, we tell `ddply` we want to `summarise` and that it should add a `mean` column using the `mean()` function and an `sd` column using the `sd(function)`



























