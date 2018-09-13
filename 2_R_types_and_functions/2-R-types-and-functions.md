Lesson 2: R simple types and functions
========================================================
author: Mate Csaba Sandor
date: 2018 September
autosize: true


About R
========================================================

> R is a programming language and free software environment for statistical computing and graphics 

> R is a GNU package The source code for the R software environment is written primarily in C, Fortran, and R. R is freely available under the GNU General Public License, and pre-compiled binary versions are provided for various operating systems.

> *Wikipedia*


Interpreter langage
========================================================


```r
2 + 2
```

```
[1] 4
```

```r
"Hello world"
```

```
[1] "Hello world"
```

```r
2 < 1
```

```
[1] FALSE
```

Variables
========================================================


```r
a <- 2
b <- 3
a ^ b
```

```
[1] 8
```

```r
c <- a ^ b - a == a * b
c
```

```
[1] TRUE
```

Mathematical operators
========================================================


```r
0 + 1 - 2 * 3 / 4
```

```
[1] -0.5
```

```r
(2 ^ 3)**.5
```

```
[1] 2.828427
```

```r
13 %% 4
```

```
[1] 1
```

```r
17 %/% 5
```

```
[1] 3
```

Logical operators
========================================================


```r
(5 < 4)
```

```
[1] FALSE
```

```r
!(5 <= 5)
```

```
[1] FALSE
```

```r
(3 != 4) & FALSE
```

```
[1] FALSE
```

```r
(3 != 4) | FALSE
```

```
[1] TRUE
```

Functions
========================================================


```r
log10(10)
```

```
[1] 1
```

```r
isTRUE(TRUE | FALSE)
```

```
[1] TRUE
```

```r
paste("apples","oranges","cacti",sep = " & ")
```

```
[1] "apples & oranges & cacti"
```

Creating functions
========================================================


```r
myFirstFunction <- function(name){
  paste0("Hi ",name,"! Nice to meet you!")
}
myFirstFunction("Mate")
```

```
[1] "Hi Mate! Nice to meet you!"
```

Creating better functions
========================================================


```r
myFirstFunction <- function(name, day = FALSE){
  if(day){
    paste0("Hi ",name,"! Nice to meet you!")
  }else{
    paste0("Hi ",name,"! Nice to meet you! It's ",format(Sys.Date(),"%A"))
}}
myFirstFunction("Mate")
```

```
[1] "Hi Mate! Nice to meet you! It's Thursday"
```

```r
myFirstFunction(name = "Mate",day = TRUE)
```

```
[1] "Hi Mate! Nice to meet you!"
```

Watch out! Functions ARE variables!
========================================================


```r
a <- function(){"Yo dawg!"}
a
```

```
function(){"Yo dawg!"}
```

```r
a()
```

```
[1] "Yo dawg!"
```

```r
a <- 2
a
```

```
[1] 2
```


Exercise time!
========================================================

1. Write a finction that greets you, but if your name is longer than 10 characters, also says "What a nice name of yours!"
2. Create a function that solves a second-order equation (in real space)! Look out for input defaults and determinants!
3. Create both scripts in different files and then upload them to your git repo!
