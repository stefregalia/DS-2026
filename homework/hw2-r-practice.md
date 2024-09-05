HW: R practice
========

### Instructions

In this assignment, you will practice some basic operations in R. Create an .rmd or .qmd script file called `hw2.rmd` or `hw2.qmd`.  After completing the report, you will render a report to PDF.  Be sure to use `\newpage` to separate each question.

### Problems

1. Working Directory

* What is the working directory?
* What are the best practices for setting and using the working directory?

2. Create a string called `name` which stores your name.

3. Run the `ls()` command to see the objects in the environment.

4. Create vectors of length 5 with the following atoms.  Call them `v1`, `v2`, ..., `v4`.

* logicals
* integers
* doubles
* characters

5. Place the vectors `v1` ... `v4` into a list called V.

6. Use `str` to inspect `V`

7. Create a matrix of size 4 x 5 of numeric values.

8. Create a sequence from 22 to 44 using the `seq` command.

9. Create an array with `cbind`

10. Grab the 3rd element of the vector `v3`

11. The Framingham Heart Study is a well-known, ongoing study of cardiovascular disease.  The following is a subset of the data collected from the study. Use the following data frame, `d1`, and grab the 4th column and assign it the name `scl`.

```
d1 <- read.csv("http://hbiostat.org/data/repo/2.20.Framingham.csv")
```

12. Use `d1` and grab the 5th row and assign it the name `id5` .

13. Use `d1` and grab the `bmi` column and assign it the object `bmi`.  Print the first 10 elements of `bmi`.

14. Add a new variable to the `d1` data frame called `bmigt30` where

$$
\text{bmigt30}_i  = \left\lbrace \begin{array}{ll} \text{NA} & \text{bmi}_i \text{ is missing} \\ 1 & \text{bmi}_i > 30 \\ 0 & \text{otherwise} \end{array} \right.
$$

15. The `chdfate` variable in `d1` is an indicator variable for coronary heart disease.  Summarize the `chdfate` column of `d1` by calculating the number and proportion of participants who developed and did not develop coronary heart disease.

16. Run the following code chunk.  Explain what the pipe operator does.

```
require(dplyr)

# Old way
sum(log(sqrt(select(d1,age)),base=10))

# OG magrittr pipe
d1 %>% 
  pull(age)  %>% 
  sqrt  %>% 
  log(base=10)  %>% 
  sum

d1 %>% 
  lm(sbp ~ dbp, data = .)  # Use the dot if the piped objects needs to go to an input other than the first

d1 %>% 
  split(.$sex) %>%  # Can use the input multiple times
  lapply(function(x){x$age %>% mean})

# New base R pipe
d1 |> 
  pull(age) |> 
  sqrt() |> # Note the parentheses have to be used
  log(base=10) |> 
  sum()

d1 |>  
  lm(sbp ~ dbp, data = _) # Use `_` instead of `.` with new pipe
```

17.  UVA phone numbers are often of the form (434) 924-????.  Modifying the code below, find the number of UVA phone numbers of the form (434) 924-???? which are prime.  (You may need to install the `primes` package.)

```
prime <- function(x){
  ps <- primes::generate_primes(min = 2, max = ceiling(sqrt(x)))
  for(i in ps) if(x%%i == 0) return(FALSE)
  TRUE
}

k <- 0
for(i in ???){
    k <- k + prime(i)
}
k
```

18. Modify the code above to find the list UVA phone numbers of the form (434) 924-???? which are prime.

19. Implement the strategies that you devised for the 1st Euler problem from HW1. [Multiples of 3 or 5](https://projecteuler.net/problem=1)