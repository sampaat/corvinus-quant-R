Lesson 2: R base types and functions
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
paste("apples", "oranges", "cacti",sep = " & ")
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
greetMe <- function(name, day = FALSE){
  if(day){
    paste0("Hi ", name, "! Nice to meet you!")
  }else{
    # this is a comment
    # %A is a date format for spelling out the day of the week
    paste0("Hi ", name, "! Nice to meet you! It's ", format(Sys.Date(),"%A"))
  }
}

greetMe("Mate")
```

```
[1] "Hi Mate! Nice to meet you! It's Thursday"
```

```r
greetMe(name = "Mate", day = TRUE)
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


Vectors (1) - Creation
========================================================


```r
c(1, 2, 3)
```

```
[1] 1 2 3
```

```r
seq(1, 3)
```

```
[1] 1 2 3
```

```r
rep(2, 2, 2)
```

```
[1] 2 2
```

Vectors (2) - Scalar operators
========================================================


```r
a <- c(1, 2, 3)

a * 2
```

```
[1] 2 4 6
```

```r
a + 2
```

```
[1] 3 4 5
```

```r
a ^ 2
```

```
[1] 1 4 9
```

```r
a >= 2
```

```
[1] FALSE  TRUE  TRUE
```

Vectors (3) - Addressing
========================================================


```r
a <- c(1, 2, 3)
a[2]
```

```
[1] 2
```

```r
a[c(TRUE, FALSE, TRUE)]
```

```
[1] 1 3
```

```r
a[a > 1]
```

```
[1] 2 3
```

```r
names(a) <- c('a', 'b', 'c')

a
```

```
a b c 
1 2 3 
```

```r
a['a']
```

```
a 
1 
```

Matrix (1) - Creation, scalar operators
========================================================


```r
a <- seq(1, 4)
m <- matrix(a, nrow = 2)

m
```

```
     [,1] [,2]
[1,]    1    3
[2,]    2    4
```

```r
diag(2) 
```

```
     [,1] [,2]
[1,]    1    0
[2,]    0    1
```

```r
diag(2) * 2
```

```
     [,1] [,2]
[1,]    2    0
[2,]    0    2
```

Matrix (2) - Addressing
========================================================


```r
m <- matrix(seq(1, 4), nrow = 2)

m
```

```
     [,1] [,2]
[1,]    1    3
[2,]    2    4
```

```r
m[1,2]
```

```
[1] 3
```

```r
colnames(m) <- c('a', 'b')
rownames(m) <- c('c', 'd')

m
```

```
  a b
c 1 3
d 2 4
```

```r
m['c','a']
```

```
[1] 1
```

Linear algebra
========================================================


```r
a <- c(1, 2)
b <- c(3, 4)

a * t(b)
a %*% t(b)
```

Linear algebra (1)
========================================================


```r
a <- c(1, 2)
b <- c(3, 4)

a * t(b)
```

```
     [,1] [,2]
[1,]    3    8
```

```r
a %*% t(b)
```

```
     [,1] [,2]
[1,]    3    4
[2,]    6    8
```

Linear algebra (2)
========================================================


```r
m <- matrix(seq(1, 4), nrow = 2)

m %*% diag(2)
crossprod(m, diag(2))
m * solve(m)
```

Linear algebra (2)
========================================================


```r
m <- matrix(seq(1, 4), nrow = 2)

m %*% diag(2)
```

```
     [,1] [,2]
[1,]    1    3
[2,]    2    4
```

```r
crossprod(m, diag(2))
```

```
     [,1] [,2]
[1,]    1    2
[2,]    3    4
```

```r
m %*% solve(m)
```

```
     [,1] [,2]
[1,]    1    0
[2,]    0    1
```

Exercise time!
========================================================

 $$
 \begin{matrix} 
5x_1 & + & x_2 \\
6x_1 & + & 2x_2
\end{matrix}
 \begin{matrix} 
= 5\\
= 7
\end{matrix}
 $$
 
 $$
 \begin{bmatrix} 
5 & 1\\
6 & 2
\end{bmatrix}
\begin{bmatrix} 
x_1\\
x_2
\end{bmatrix} =
 \begin{bmatrix} 
5\\
7
\end{bmatrix}
 $$
 
 $$
 A x = b
 $$
 
 $$
 A^{-1} b = x
 $$
 
 $$
 x = ?
 $$
 
List (1) - Creation
========================================================


```r
a <- list("apples", "oranges")

a
```

```
[[1]]
[1] "apples"

[[2]]
[1] "oranges"
```

```r
list(TRUE, 0, "saywhat?", rep(1, 3), a)
```

```
[[1]]
[1] TRUE

[[2]]
[1] 0

[[3]]
[1] "saywhat?"

[[4]]
[1] 1 1 1

[[5]]
[[5]][[1]]
[1] "apples"

[[5]][[2]]
[1] "oranges"
```

List (2) - Inspection
========================================================


```r
a <- list(TRUE, 0, "saywhat?", rep(1, 3), list("apples", "oranges"))

str(a)
```

```
List of 5
 $ : logi TRUE
 $ : num 0
 $ : chr "saywhat?"
 $ : num [1:3] 1 1 1
 $ :List of 2
  ..$ : chr "apples"
  ..$ : chr "oranges"
```

List (3) - Access
========================================================


```r
a <- list(TRUE, 0, "saywhat?", rep(1, 3), list("apples", "oranges"))

a[[1]]
```

```
[1] TRUE
```

```r
a <- list(logic = TRUE, num = 0, "Text me" = "or call", vec = rep(1, 3), list = list("apples", "oranges"))

a$logic
```

```
[1] TRUE
```

```r
a[["Text me"]]
```

```
[1] "or call"
```

List (4) - Typical usage
========================================================


```r
eigen(matrix(seq(1, 4), nrow = 2))
```

```
eigen() decomposition
$values
[1]  5.3722813 -0.3722813

$vectors
           [,1]       [,2]
[1,] -0.5657675 -0.9093767
[2,] -0.8245648  0.4159736
```

```r
powers <- function(a){
  list(square = a ^ 2, root = a ^ .5)
}

powers(4)
```

```
$square
[1] 16

$root
[1] 2
```

Loops - for, while
========================================================


```r
a <- seq(1, 4)

for(i in a){
  print(2 * i)
}
```

```
[1] 2
[1] 4
[1] 6
[1] 8
```

```r
j <- 1
while(j <= 4){
  print(2 * a[j])
  j <- j + 1
}
```

```
[1] 2
[1] 4
[1] 6
[1] 8
```


Use vectors properly!
========================================================


```r
a <- seq(1, 4)

a * 2
```

```
[1] 2 4 6 8
```

```r
sqrt(a)
```

```
[1] 1.000000 1.414214 1.732051 2.000000
```

```r
seq(1, 7) + a
```

```
[1]  2  4  6  8  6  8 10
```

```r
sapply(a, function(x) (x + 1) ^ 2)
```

```
[1]  4  9 16 25
```

Use lists properly!
========================================================


```r
b <- list(list(name = "Adam",sex = "M"), list(name = "Eve", sex = "F"))

c <- lapply(b, function(x) if(x$sex == "M"){
    paste(x$name, "is a man.")
  }else{
    paste(x$name, "is a woman.")
  })

c
```

```
[[1]]
[1] "Adam is a man."

[[2]]
[1] "Eve is a woman."
```

```r
unlist(c)
```

```
[1] "Adam is a man."  "Eve is a woman."
```

Exercise time!
========================================================

- Write a function that generates an integer of length n (use `runif`).
- Write a pnohebook of names and randomly generated telephonnumbers with a function.
- Inputs should be a vector of strings, output should be a list of entries, it should use our first function.
- Write another function that takes the output of the previous and adds a country code before all numbers

Exercises for home
========================================================

[R-bloggers](https://www.r-bloggers.com/) features R related posts regularly. Worth a follow.

Check out exercise 1-7 [here](https://www.r-bloggers.com/functions-exercises/)
