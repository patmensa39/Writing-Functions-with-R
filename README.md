# Writing-Functions-with-R
Writing functions, control structures, Loop, Nested loops, While loop and looping on the command line. 

---
title: ""
output:
  pdf_document: default
  html_document: default
  word_document: default
date: ""
theme: cerulean
---


## Name: 

### Writing of functions, control structures, Loop, Nested loops, While loop and looping on the command line. 


```{r}
library(tidyverse)
Philant.players <- read.csv("Players-1920.csv", header = TRUE, sep = ",")
### Separating the players names  in the "Player" variable into two and keeping ONLY the first version of the name.
Philant.players2<- Philant.players %>% separate(Player, into = c("Player_Name_1", "Player_Name_2"), sep = "\\\\") %>% select(-Player_Name_2)

### Mean of the players age and stripping of all the NA's
mean(Philant.players2$Age, na.rm = TRUE)

```

```{r}
### Other functions to add numbers
philant.function <- function(a=NULL, b=2, c=3){a+b+c}
philant.function <- function(a=3, b=2, c=3){a+b+c}
philant.function()
```

```{r}
### Lazy functions to evaluate arguments as needed and ignornig the ones that was not called. 
philant.function2 <- function(c, d) {5*c}
philant.function2(4)
### Remember the function did not call for d.
```

## CONTROL STRUCTURES

```{r}
## If else statements 
if (x<= 4){y<-3*x} else {y<-x}
if (x<9) {print("x is not a single number")} else {print("x is a single number")}
pat<- if (x<=4) {3*x} else {x}
```

## For Loops
```{r}
### this allow us to run a code for a fixed number of times. 
y<- c(8,6,12)
x<-4
for (i in y) (x<-x+i)
```

### Nested Loop
```{r}
pat<- matrix(1:10, nrow = 2, ncol = 5)
```

## Multiple conditions with while loops. 
```{`r}
set.seed(1200)
z<- 5
while (z<=3 && z>=10) {print(z)
}
coin<- rbinom(1,1,0.5)
if (coin==1){z<- z+1} else (z<- z-1)
```

```{r}
### running mean on c and d 
philant<-list(c=runif(50), d= rnorm(10))
lapply(philant, mean)

### returning a list with elements containing 1,2,3 uniform random variables
kay<- 1:3
lapply(kay, runif)
### returning a list with elements containing 1,2,3 uniform (1,5)  random variables
lapply(kay, runif, min=1, max=5)
```

```{r}
### Using apply function, finding the mean of rows of patrick matrix
patrick<- matrix(1:12, 4,3)
apply(patrick, 1,mean)

### finding the sum of colums of patrick matrix
apply(patrick, 2,sum)


### Using tapply
### finding means
jem<- c(rnorm(10,2,1), runif(10), rexp(10,0.1))
jem.factors<- gl(3,10, labels = c("Group1", "Group2", "Group3"))
tapply(jem, jem.factors, mean)

### Finding the ranges
tapply(jem, jem.factors, range)


### Spliting the factotrs
split(jem, jem.factors)
lapply(split(jem, jem.factors), mean)
sapply(split(jem, jem.factors), mean)
```
