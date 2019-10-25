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
##   [1]  0.626668368 -0.452540823 -1.343096122 -1.338523794 -0.367438831
##   [6] -1.633349770 -0.210874275 -1.728224100 -0.083045232 -0.396222468
##  [11]  2.246969640  0.022033606 -0.863631195 -1.325385634  0.256046362
##  [16] -0.244269260 -0.784786194 -0.131510969 -0.403911574  0.160815925
##  [21]  0.153484606 -0.554388277 -0.617125442  0.071722618 -1.090166880
##  [26] -0.901826369 -0.335061756  0.008732935  0.339989480  0.497959182
##  [31] -0.596777910  0.265303424 -0.300056844  1.252499301  0.382100661
##  [36]  1.326128720 -0.889031068  0.026857020  0.307053356  0.409220200
##  [41] -0.355682668 -0.014562431 -0.358201310 -1.495028532 -1.517146314
##  [46] -0.084463024  0.711344791 -0.078715604 -0.190293024  0.487128572
##  [51] -0.525750523  0.268679719 -1.627650777 -0.173101800  0.225928006
##  [56] -0.366239148 -1.301055154 -2.369231692 -1.071188681 -2.324405499
##  [61]  0.312597771  1.445983136 -0.703684775 -0.163354083  0.863965414
##  [66]  0.631576397 -0.983114246  0.493256575  0.731977315  0.095529623
##  [71] -0.622219450 -0.420345267  1.127861180 -0.234844699  0.177597988
##  [76]  1.128157777  0.503290062 -1.031638344 -0.097988166  0.992251873
##  [81] -0.521572496 -1.575758915 -0.500857301  1.604691662  1.705448558
##  [86] -0.202787858  0.039223912  1.109624168 -0.483585169 -0.666202269
##  [91]  1.919577103  0.311366966 -0.387674125  0.979445601  0.452559503
##  [96] -0.592148810  0.411525325  0.595982603 -0.524270324 -0.688160865
```

We can combine objects, variables and functions to do more complex stuff in R, here's how we get the mean of 100 random numbers.


```r
numbers <- rnorm(100)
mean(numbers)
```

```
## [1] 0.06197864
```

Here we created a vector object with `rnorm(100)` and assigned it to the variable `numbers`. We than used the `mean()` function, passing it the variable `numbers`. The `mean()` function returned the mean of the hundred random numbers.

>## Bracket notation in this document
> I'm going to use the following descriptions for the symbols `()`, `[]` and `{}`: 
>
> `()` are brackets,
> `[]` are square brackets
> `{}` are curly brackets


## Quiz
1. Create two variables, `a` and `b`: Add them. What happens if we change a and then re-add a and b?
2. We can also assign `a + b` to a new variable, `c`. How would you do this?
3. Try some R functions: `round()`, `c()`, `range()`, `plot()` hint: Get help on a function by typing `?function_name` e.g `?c()`. Use the `mean()` function to calculate the average age of everyone in your house (Invent a housemate if you have to).
