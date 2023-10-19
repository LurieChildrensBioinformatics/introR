---
title: "Day 1: R basics"
date: 2023-10-16
output: 
  html_document:
editor_options: 
  markdown: 
    wrap: sentence
---



## Slides <a href="../slides/Day1.pdf" target="_blank">here</a>

# Basics of R  
  
R is a programming language designed for statistical modelling and data analysis.
It is heavily supported by an active community, where new tools for data handling, visualization, and statistical analysis are constantly developed and shared.

> **The learning goals for today are:**
>  
> -   become familiar with R, its syntax and basic principles  
> -   know how to use R as a calculator  
> -   understand and write simple R scripts  
> -   perform basic operations on data  
> -   be able to make simple plots  

## First steps

R is an interpreted language meaning that you can evaluate it line by line.
Usually, code is stored in a **script**, so one does not have to retype it with each new session. However, line-by-line execution can be useful for development or debugging. Let's begin by executing code in the console.

### Comments
Comments are often used to explain R code. They are a great tool for increasing readability of your work. Comments can also be used to prevent execution when testing alternative code.  
  
All comments start with a `#`. R will ignore anything that begins with `#` when executing code.  
  
This is an example of using a comment before a line of code:  

```r
# This is a comment
"Hello World!"
```

```
## [1] "Hello World!"
```
  
Comments can also be added at the end of a line of code:

```r
"Hello World!"  # This is a comment
```

```
## [1] "Hello World!"
```
  
Note, comments do not solely have to be used to explain code, they can also be used to prevent R from executing code:

```r
#'Hello World!'
```

### Using R as a calculator

R has usual arithmetic operations (+ - * / ^).  
Practice performing the operations below.  

> **Exercise 1: Use the console to...**
>   
> -   Calculate 3 + 5
> -   Calculate 10^2
> -   Calculate 4^3 -2*7+9 /2
> 
> <details>
> <summary>Click for Answers</summary>
> 
> ```r
> 3 + 5
> ```
> 
> ```
> ## [1] 8
> ```
> 
> ```r
> 10^2
> ```
> 
> ```
> ## [1] 100
> ```
> 
> ```r
> 4^3 - 2 * 7 + 9/2
> ```
> 
> ```
> ## [1] 54.5
> ```
> </details>

-------------

### Coding in a script

Now let's explore writing code in a script...
  
**Creating a new script** file is simple:  
  
-   select File -> New File -> R Script  
  
**Typing code** in the script:  
  
-   type each R command on its own line  
-   use `#` to convert text to comments  

**Select** code you want to execute:   
  
-   place the cursor in the line of code you want to execute  
-   *or* highlight the code you want to execute  
  
**Execute code** in the script:  
  
-   click on the `Run` button in the top right corner of the scripting window  
-   *or* type one of the following  
      +   Windows: cntrl + return
      +   Mac: command + return

> **Exercise 2**
>   
> Open a new R script and save it as Practice1.R
>  

-------------

## Functions
In Session 1 we were introduced to **functions**. R has many built-in functions. Functions are commonly called by their name followed by round brackets that enclose the function's arguments (where multiple arguments are separated by commas). For example, the function `log()` takes a number and returns the log value of that number. Practice using the following functions below:

> **Exercise 3: In your `Practice1.R` script...**
>  
> -   Find the **log** of 100  
> -   Find the **mean** of all values between 1 and 100  
> -   **Round** 0.958 to the nearest integer  
>  
> <details>
> <summary>Click for Answers</summary>
> 
> ```r
> log(100)
> ```
> 
> ```
> ## [1] 4.60517
> ```
> 
> ```r
> mean(1:100)
> ```
> 
> ```
> ## [1] 50.5
> ```
> 
> ```r
> round(0.958)
> ```
> 
> ```
> ## [1] 1
> ```
> </details>

Many functions allow several arguments. Take `round()` for example. It takes as input the number `x` to be rounded *as well as* another integer number, `digits`, which gives the number of digits after the comma to which `x` should be rounded.  

```r
# round the number `x` to the assigned number of `digits`
round(x = 0.958, digits = 2)
```

```
## [1] 0.96
```

**Of Note:**
If all arguments are named, their order does not matter. However, it is good practice to maintain the positions expected by the function. These positions are detailed for every function under `help`. Functions can also have default values. In the case of `round`, the default value is `digits = 0`. `help` can also provide clarity as to default values.  
  
-------------
  
## Assignment
We can assign values to variables using `<-`

```r
x <- 9
8 -> y
```

By assigning a value to a variable, that variable then appears in the environment panel. We can now ask R what that variable is:


```r
x
```

```
## [1] 9
```

It is always good practice to give your variables meaningful names.

```r
body_temp <- 98.6

# a few side notes: 1. Try to avoid using spaces in variable names. R will have
# a hard time deciphering these.  2. You can also assign variables with `=`,
# however it is better practice to use `<-`
```

> **Exercise 4**
>  
> Create two variables, `a` and `b` by assigning the values 60 and 31 to them respectively.
> Next, divide variable `a` by variable `b` and prodice an output with **three** decimal places.
> <details>
> <summary>Click for Answer</summary>
> 
> ```r
> a <- 60
> b <- 32
> round(x = a/b, digits = 3)
> ```
> 
> ```
> ## [1] 1.875
> ```
> </details>
  
  
### Variable types

Variables in R can exist in one of several types:
  
-   **numeric** - holds numeric values
-   **integer** - holds whole numbers exclusively
-   **character** - holds string values (ie "hello", "R is fun")
-   **logical** - holds TRUE or FALSE values (sometimes called boolean)
-   **NA** - denotes a missing value
  
You can find out what type of value something is with the function `class()`:  

```r
class(123.4)
```

```
## [1] "numeric"
```

```r
class(56L)
```

```
## [1] "integer"
```

```r
class("hello world")
```

```
## [1] "character"
```

```r
class(TRUE)
```

```
## [1] "logical"
```

-------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------

# Objects
  
Variables can be organized into data structures, or objects.  
  
-   **Vector** - a one-dimensional data set of *one* data type  
-   **Matrix** - a two-dimensional data set of *one* data type  
-   **Data frame** - a two-dimensional data set of *any* data type  

## Vectors

Vectors are a sequence of elements all having the same type (ie c(1,2,3) or c("one","two","three")). Vectors in general can be declared with the built-in function c(). Think of this as meaning "concatenate" or "combine". We will spend some time exploring numeric vectors.  
  

```r
x <- c(4, 7, 1, 1)  # this is now a 4-place vector
x
```

```
## [1] 4 7 1 1
```

You can get the length of a vector using `length()`.  


```r
length(x)
```

```
## [1] 4
```


There are also helpful functions to generate sequences of numbers:  


```r
1:10  # returns 1, 2, 3, ..., 10
seq(from = 1, to = 10, by = 1)  # returns 1, 2, 3, ..., 10
seq(from = 1, to = 10, by = 0.5)  # returns 1, 1.5, 2, ..., 9.5, 10
seq(from = 0, to = 1, length.out = 11)  # returns 0, 0.1, ..., 0.9, 1
```

Something to note, unlike some programming languages, indexing in R starts with 1, not 0!


```r
x <- c(4, 7, 1, 1)  # this is now a 4-place vector
x[2]
```

```
## [1] 7
```

As discussed in Session 1, mathematical operations can be applied to vectors. Most functions in R operate elementwise, meaning they apply to all elements of a vector.  


```r
x <- c(4, 7, 1, 1)  # 4-placed vector as before
x + 1
```

```
## [1] 5 8 2 2
```

Some functions operate on the complete vector:  


```r
sum(x)
```

```
## [1] 13
```

> **Exercise 5**
> -   Create a vector that contains all even numbers from 0 to 20 and assign it to a variable. 
> -   Now transform the variable such that it contains only odd numbers up to 20 using mathematical operation. 
> -   Bonus: Ensure that numbers above 20 are not included! [Hint: use indexing.]
> <details>
> <summary>Click for Answer</summary>
> 
> ```r
> a <- seq(from = 0, to = 20, by = 2)
> a <- a + 1
> # bonus below
> a <- a[1:10]
> a
> ```
> 
> ```
> ##  [1]  1  3  5  7  9 11 13 15 17 19
> ```
> </details>
  
-------------

## Matrices

Matrices are declared with the function `matrix`. This function takes, for instance, a vector as an argument.  


```r
x <- c(4, 7, 1, 1)  # A 4-element vector
m <- matrix(x)  # Make x into a matrix
```

Notice that the result is a matrix with a single column. This is important. R uses so-called column-major mode, meaning it fills columns first. For example, a matrix with three columns based on a six-element vector 1, 2, ... , 6 will be built by filling the first column from top to bottom, then the second column top to bottom, and so on.  


```r
m <- matrix(1:6, ncol = 3)
m
```

```
##      [,1] [,2] [,3]
## [1,]    1    3    5
## [2,]    2    4    6
```

As we saw in Session 1, matrix indexing starts with the row index followed by the column index:

```r
m[1, ]  # produces first row of matrix 'm'
```

```
## [1] 1 3 5
```

```r
m[, 2]  # produces second column of matrix 'm'
```

```
## [1] 3 4
```
 
-------------

## Data frames

A data frame is base R’s standard format to store data in. A data frame is a list of vectors of equal length. They can be initiated with the function `data.frame`:  

```r
# fake experimental data
exp_data <- data.frame(trial = 1:5, condition = c("C1", "C2", "C1", "C3", "C2"),
    response = c(121, 133, 119, 102, 156))
exp_data
```

```
##   trial condition response
## 1     1        C1      121
## 2     2        C2      133
## 3     3        C1      119
## 4     4        C3      102
## 5     5        C2      156
```

> **Exercise 6**
>  
> -   Create a vector named `x` that contains the names of three of your favorite months of the year 
> and a vector named `b` with their associated number of days.   
> -   Create a data frame that represents this information (one column with months and one with number of days). 
> Column names should represent the information they contain!
> <details>
> <summary>Click for Answer</summary>
> 
> ```r
> a <- c("September", "May", "June")
> b <- c(30, 31, 30)
> fav_months <- data.frame(month = a, days = b)
> fav_months
> ```
> 
> ```
> ##       month days
> ## 1 September   30
> ## 2       May   31
> ## 3      June   30
> ```
> </details>

We can access columns of a data frame using index notation, like in a matrix:

```r
# gives the values in column 2
exp_data[, 2]
```

```
## [1] "C1" "C2" "C1" "C3" "C2"
```

```r
# gives the values in the column named 'reponse'
exp_data$response
```

```
## [1] 121 133 119 102 156
```

```r
exp_data["response"]
```

```
##   response
## 1      121
## 2      133
## 3      119
## 4      102
## 5      156
```

```r
# gives the value of the cell in row 2, column 3
exp_data[2, 3]
```

```
## [1] 133
```

> **Exercise 7**  
> Display the column of *months* from the favorite months data frame.
> <details>
> <summary>Click for Answer</summary>
> 
> ```r
> fav_months$month
> ```
> 
> ```
> ## [1] "September" "May"       "June"
> ```
> 
> ```r
> fav_months["month"]
> ```
> 
> ```
> ##       month
> ## 1 September
> ## 2       May
> ## 3      June
> ```
> 
> ```r
> fav_months[1]
> ```
> 
> ```
> ##       month
> ## 1 September
> ## 2       May
> ## 3      June
> ```
> </details>  
>  
>  
> Now show only the names of months *with greater than 30 days*. 
> <details>
> <summary>Click for Answer</summary>
> 
> ```r
> fav_months[fav_months$days > 30, "month"]
> ```
> 
> ```
> ## [1] "May"
> ```
> </details>


-------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------

# Working with data

We will now explore actual data! Say hello to the [`palmerpenguins`](https://allisonhorst.github.io/palmerpenguins/)

![](https://allisonhorst.github.io/palmerpenguins/reference/figures/lter_penguins.png)

These data contain size measurements for three penguin species observed on three islands in the Palmer Archipelago, Antarctica. The `palmerpenguins` data were collected by Dr. Kristen Gorman with the Palmer Station Long Term Ecological Research Program from 2007 - 2009.

## Load in data

<a href="../../penguins.xlsx">Download excel file here</a>

> **Exercise 8**
>    
> Load in the penguins.xlsx file using the Environments window
> How would you load this data using code?
>  


```r
library(readxl)
penguins <- read_excel("penguins.xlsx")
```


(Note: this data is also available in R as a package)

## Work with the data

We will focus on a curated subset of the raw data. This subset contains 8 variables for a total of 342 penguins. Let's explore the data through code.

> **Exercise 9**
>    
> Select the columns `species`, `island`, `body_mass_g`, and `year`. Save this as a variable named `penguins_subset`.
>
> <details>
> <summary>Click for Answer</summary>
> 
> ```r
> penguins_subset <- penguins[, c("species", "island", "body_mass_g", "year")]
> penguins_subset
> ```
> 
> ```
> ## # A tibble: 342 × 4
> ##    species island    body_mass_g  year
> ##    <chr>   <chr>           <dbl> <dbl>
> ##  1 Adelie  Torgersen        3750  2007
> ##  2 Adelie  Torgersen        3800  2007
> ##  3 Adelie  Torgersen        3250  2007
> ##  4 Adelie  Torgersen        3450  2007
> ##  5 Adelie  Torgersen        3650  2007
> ##  6 Adelie  Torgersen        3625  2007
> ##  7 Adelie  Torgersen        4675  2007
> ##  8 Adelie  Torgersen        3475  2007
> ##  9 Adelie  Torgersen        4250  2007
> ## 10 Adelie  Torgersen        3300  2007
> ## # ℹ 332 more rows
> ```
> </details>
>  
>  
> Create a new column in `penguins_subset` that takes `body_mass_g` and generates `body_mass_kg`
>  
> <details>
> <summary>Click for Answer</summary>
> 
> ```r
> penguins_subset$body_mass_kg <- penguins$body_mass_g/100
> penguins_subset
> ```
> 
> ```
> ## # A tibble: 342 × 5
> ##    species island    body_mass_g  year body_mass_kg
> ##    <chr>   <chr>           <dbl> <dbl>        <dbl>
> ##  1 Adelie  Torgersen        3750  2007         37.5
> ##  2 Adelie  Torgersen        3800  2007         38  
> ##  3 Adelie  Torgersen        3250  2007         32.5
> ##  4 Adelie  Torgersen        3450  2007         34.5
> ##  5 Adelie  Torgersen        3650  2007         36.5
> ##  6 Adelie  Torgersen        3625  2007         36.2
> ##  7 Adelie  Torgersen        4675  2007         46.8
> ##  8 Adelie  Torgersen        3475  2007         34.8
> ##  9 Adelie  Torgersen        4250  2007         42.5
> ## 10 Adelie  Torgersen        3300  2007         33  
> ## # ℹ 332 more rows
> ```
> </details>
>  
>  
> Filter `penguins_subset` to include data only from the *year 2009*
>  
> <details>
> <summary>Click for Answer</summary>
> 
> ```r
> penguins_subset <- penguins_subset[penguins_subset$year == 2009, ]
> penguins_subset
> ```
> 
> ```
> ## # A tibble: 119 × 5
> ##    species island body_mass_g  year body_mass_kg
> ##    <chr>   <chr>        <dbl> <dbl>        <dbl>
> ##  1 Adelie  Biscoe        3725  2009         37.2
> ##  2 Adelie  Biscoe        4725  2009         47.2
> ##  3 Adelie  Biscoe        3075  2009         30.8
> ##  4 Adelie  Biscoe        4250  2009         42.5
> ##  5 Adelie  Biscoe        2925  2009         29.2
> ##  6 Adelie  Biscoe        3550  2009         35.5
> ##  7 Adelie  Biscoe        3750  2009         37.5
> ##  8 Adelie  Biscoe        3900  2009         39  
> ##  9 Adelie  Biscoe        3175  2009         31.8
> ## 10 Adelie  Biscoe        4775  2009         47.8
> ## # ℹ 109 more rows
> ```
> </details>


## Graphical exploration

Let's explore the penguins data set using visualizations. In session 1 we were introduced to histograms and boxplots. Here's a quick summary of a few plotting functions that may be useful:
  
`hist(data$x)` creates a histogram  
`barplot(data$x)` creates a barplot  
`plot(data$x, data$y)` creates a scatterplot  
`boxplot(data$y ~ data$x)` creates a boxplot  

*For additional base R plotting resources, check out [this page](http://www.sthda.com/english/wiki/r-base-graphs).*  

> **Exercise 10**
>    
> Explore the `penguins` data set with plots! Feel free to add customizations to the plot (ie update the main figure title, change the axes labels). For help doing so, check out the help page for each function using `?function`.
>


-------------
Some content adapted from: https://michael-franke.github.io/intro-data-analysis/

