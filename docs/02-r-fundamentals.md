# R Fundamentals

## About this chapter

1. Questions:
  - How do I use R?
2. Objectives:
  - Become familiar with R syntax
  - Understand the concepts of objects and assignment
  - Get exposed to a few functions
3. Keypoints:
  - R's capabilities are provided by functions
  - R users call functions and get results

## Working with R 

In this workshop we'll use R in the extremely useful RStudio package. For the most part we'll work interactively, meaning we'll type stuff straight into the R console in RStudio (Usually this is a window on the left or lower left) and get our results there too (usually in the consoled or in a window on the right). That's what you see in panels like the ones below - first the thing to type into R, and below it, the calculated result from R. Let's look at how R works by using it for it's most basic job - as a calculator:


```r
 3 + 5
```

```
## [1] 8
```

```r
 12 * 2
```

```
## [1] 24
```

```r
 1 / 3
```

```
## [1] 0.3333333
```

```r
 12 * 2
```

```
## [1] 24
```

```r
  3 / 0
```

```
## [1] Inf
```


Fairly straightforward, we type in the expression and we get a result. That's how this whole book will work, you type the stuff in, and get answers out. It'll be easiest to learn if you go ahead and copy the examples one by one. Try to resist the urge to use copy and paste. Typing longhand really encourages you to look at what you're entering.

As far as the R ouput itself goes, it's really straightforward - its just the answer with a `[1]` stuck on the front. This `[1]` tells us how far through the output we are. Often R will return long lists of numbers and it can be helpful to have this extra information

##  Variables

We can save the output of operations for later use by giving it a name using the assignment symbol `<-`. Read this symbol as 'gets', so `x <- 5` reads as 'x gets 5'. These names are called variables, because the value they are associated with can change.

Let's give five a name, `x` then refer to the value 5 by it's name. We can then use the name in place of the value. In the jargon of computing we say we are assigning a value to a variable. 


```r
 x <- 5
 x
```

```
## [1] 5
```


```r
 x * 2
```

```
## [1] 10
```


```r
y <- 3
x * y
```

```
## [1] 15
```


This is of course of limited value with just numbers but is of great value when we have large datasets, as the whole thing can be referred to by the variable.


### Using objects and functions

At the top level, R is a simple language with two types of thing: functions and objects. As a user you will use functions to do stuff, and get back objects as an answer. Functions are easy to spot, they are a name followed by a pair of brackets
 like `mean()` is the function for calculating a mean. The options (or arguments) for the function go inside the brackets: 


```r
 sqrt(16)
```

```
## [1] 4
```


Often the result from a function will be more complicated than a simple number object, often it will be a vector (simple list), like from the `rnorm()` function that returns lists of random numbers


```r
 rnorm(100)
```

```
##   [1]  0.106196741  0.156499090  1.122751310 -0.670084081  1.224937395
##   [6] -1.560875399 -1.313092991  0.505127104 -0.002985333 -1.635503535
##  [11] -1.681296190 -0.475818156  1.235382422  0.489441128  0.673655400
##  [16] -0.431165589  0.857616170 -0.569652315 -1.476534094 -2.049646684
##  [21] -0.302794475  0.611173136 -0.339453750 -0.424469925 -0.189253132
##  [26] -1.336533625 -0.953308074 -0.601771592  1.524791685  1.233204400
##  [31]  0.473456245  1.507342016  0.308394391  0.208052966 -0.254195097
##  [36] -0.716831081 -0.205132517  0.818773004 -0.678599934  0.759109680
##  [41] -2.071864784  0.173952865 -0.623430293 -0.764205383  0.467076495
##  [46]  0.519106395  0.619915636  0.805792771 -0.818532557 -0.649019246
##  [51] -0.164240133 -1.081797662 -0.460835462 -0.109158868  0.154414095
##  [56]  0.098255915  0.457015247 -0.514360951 -1.412608766 -0.627099244
##  [61]  1.660602842  0.292732282  0.656043259  0.304681201  0.259846159
##  [66] -0.144993247  0.096204522 -1.210208474 -1.821591638 -0.923748589
##  [71]  0.987879137  0.315032569 -0.805453752  0.642979673 -0.068660768
##  [76]  1.362718943 -0.788200184 -0.004131279 -0.035227614  1.028765568
##  [81]  1.534620442 -0.464159677  0.177930818  0.199266316  0.493888580
##  [86]  0.318971864 -0.063085499 -1.350367484  0.831258662  0.849443001
##  [91]  2.060169440 -0.903562942 -0.773531228  0.501784868 -0.980087523
##  [96]  0.559917373  0.424151368 -1.974328833  0.680327029 -0.247567496
```

We can combine objects, variables and functions to do more complex stuff in R, here's how we get the mean of 100 random numbers.


```r
numbers <- rnorm(100)
mean(numbers)
```

```
## [1] -0.0815469
```

Here we created a vector object with `rnorm(100)` and assigned it to the variable `numbers`. We than used the `mean()` function, passing it the variable `numbers`. The `mean()` function returned the mean of the hundred random numbers.


## Quiz
1. Create two variables, `a` and `b`: Add them. What happens if we change a and then re-add a and b?
2. We can also assign `a + b` to a new variable, `c`. How would you do this?
3. Try some R functions: `round()`, `c()`, `range()`, `plot()` hint: Get help on a function by typing `?function_name` e.g `?c()`. Use the `mean()` function to calculate the average age of everyone in your house (Invent a housemate if you have to).
