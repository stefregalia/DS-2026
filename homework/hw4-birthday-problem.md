# HW: Calculus of belief & Birthday problem

### Submission instructions

*  Please submit a reproducible report in .pdf format to Gradescope.  
*  When you submit, you will indicate the location of each question and response in the report.  (This means you do not need to use `\newpage` to separate questions.)
*  In your response, please include the text of the question.

## Questions

Consider two investment opportunities. The first is a large water well
project with a potential payoff of $100. The second opportunity is an
investment series of 10 small wells, each with a potential payoff of
$10. The probability that any well (large or small) returns a payoff is
0.1.

The functions below simulate the outcomes from the two investments.

    big_well <- function(N) 100*rbinom(N, 1, 0.1)
    sma_well <- function(N)  10*rbinom(N, 10, 0.1)

For example, to simulate 10 outcomes, we can use the commands
`big_well(10)` or `sma_well(10)`.

    set.seed(23459874) # What does set.seed do?
    big_well(10)

    ##  [1] 100 100   0   0   0   0   0   0   0   0

    sma_well(10)

    ##  [1] 10  0  0 10  0  0  0  0 20  0

Thinking about probability as a long-run proportion, one can generate
many replicates and then tabulate.

    big_well(1E6) |> 
      table() 

    ## 
    ##      0    100 
    ## 899848 100152

    big_well(1E6) |>
      table() |>
      proportions()

    ## 
    ##       0     100 
    ## 0.90008 0.09992

1.  Write code that generates the long-run proportions for the small
    well investment opportunity.
2.  Create a figure which visualizes the long-run proportions. (I know
    we have not covered this in-class; I’m asking you to search online
    for how you might do this.)

Please read chapter 3 of Understanding Uncertainty.

3.  In section 3.9, the author introduces the notation *p*(*E*|*K*).
    -   What does *K* represent?  
    -   Create an example where the probability of an event is different
        when *K* is different.
4.  If *E* denotes an event, what does *E*<sup>*c*</sup> denote?
5.  Consider a potentially unfair six-sided die. Let *E* denote the
    outcome of a die roll. If *P*(*E* is even ) = .6, what must *P*(*E*
    is odd ) be? Why?
6.  Using simulation, create a script that will solve the `Birthday Problem`: In a class of 35 individuals, what is the probability that at least two individuals will share a birthday?  (The code we developed in class is below).

    a.  What does `set.seed` do in the script?  
    b.  What does `R` represent?  
    c.  Does the solution make any assumptions or simplifications?  If so, what are they?  
    d.  Run both versions of the script.  For version 1, use a class size of 35.  Do both versions give the same answer?  
    e.  Add vertical and horizontal lines to the plot generated in version 2 which show your estimated probability generated with version 1 code.  
    f.  Look at the `first_duplicate` function.  What does the function return?  Use `?which` and `?min` to read the documentation of what these commands do.  (Answer: It returns the first instance of _____.)  

## Version 1 of code

```
generate_class <- function(class_size){
  ???
  ???
}

check_birthday <- function(class){
  ???
  ???
}

set.seed(230583)
R <- 10000
replicates <- replicate(R, ???)
mean(replicates)
```

## Version 2 of code

```
first_duplicate <- function(){
    sample(1:365, 366, replace=TRUE) |>
    duplicated() |>
    which() |>
    min()
}

fd1 <- replicate(R, first_duplicate())
plot(ecdf(fd1), main = "Probability of shared birthday", xlab = "Class size")
```
