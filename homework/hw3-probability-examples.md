HW: Examples of Uncertainty
========

## Instructions

Create an .rmd or .qmd script file called `hw3.rmd` or `hw3.qmd` with responses for each question.  After completing the report, you will render a report to PDF.  Be sure to use `\newpage` to separate each question.

Please read chapter 1 of Understanding Uncertainty.

## Q1 

Generate 3 additional examples of uncertainty.  Make sure one of the examples represent different types of uncertainty.

## Q2 

Please write a short summary of what the author means with the statement *Probability does not exist.*

## Q3 

Please write a short summary of what it means to *organize beliefs*.

## Q4

Probability can represent a long-run proportion, an expression of personal belief, or the combination of data and belief.  In the question, you will use R to estimate via simulation the probability (in the long-run proportion sense of the word) of a *flush* in the card game poker, specifically 7 card stud.  In 7 card stud, players are dealt 7 cards and then pick the best 5 cards in create a hand.  The code below creates `d1`, a deck of 52 cards, `shuffle`, a function which shuffles the deck, and `deal`, a function which deals the first $k$ cards from the deck.

```
# Create a deck of 52 cards
d1 <- expand.grid(
      suit = c("heart","diamond","spade","club")
    , value = 1:13
    , KEEP.OUT.ATTRS = FALSE
    , stringsAsFactors = FALSE
  ) 

deal <- function(x, k=5){
  # x = deck of cards
  # k = number of cards to deal
  if(k > nrow(x)) stop("Number of cards to deal exceeds size of deck")
  x[1:k,]
} 

shuffle <- function(x){
  # x = deck of cards
  idx <- sample.int(nrow(x), nrow(x))
  x[idx,]
}
```

To show how these functions might be combined to estimate a probability, here is some code which estimates the probability of a *straight*, which occurs if at least 5 of the 7 cards are sequential.  For example, the 7 cards dealt to the player were the following, 

```
    suit value
 diamond     5
   spade     8
   spade    10
   spade     6
   heart     7
    club     9
 diamond    13
```

the player would have a straight because there are at least 5 cards with sequential value.

```
    suit value
 diamond     5
   spade     6
   heart     7
   spade     8
    club     9
   spade    10
 diamond    13
```

The command `check_straight` will return a `TRUE` if the cards can be ordered to a *straight*.  Otherwise, the command will return `FALSE`.

```
check_straight <- function(x){
  # x = hand of cards
  r1 <- x[,2] |> unique() |> sort() |> diff() |> rle()
  if(min(r1$values)>1) return(FALSE)
  max_run <- r1$lengths[r1$values == 1] |> max()
  max_run >= 4
}
```

To estimate the probability of a *straight*, the following steps are repeated 10000 times:

A. The deck is shuffled  
B. The top 7 cards are dealt  
C. The hand of 7 cards is checked to see if at least 5 cards can be ordered into a straight  
D. The outcome of is recorded.

Once all 10000 outcomes are recorded, the proportion which resulted in a straight is calculated.

```
out <- replicate(10000, d1 |> shuffle() |> deal(7) |> check_straight())
mean(out)
```

As noted above, you will use R to estimate via simulation the probability of a *flush* in 7 card stud.  To accomplish this, write a function called `check_flush` which determines if at least 5 of the 7 cards are of the same suit.  Write the function so that `TRUE` is returned when the hand is a flush and `FALSE` otherwise.  The replicate command will repeat the process 10000 times.  The mean of the output vector is the estimate of the probability.

```
check_flush <- function(x){
  # x = hand of cards
  # ... complete this function ...
}

out <- replicate(10000, d1 |> shuffle() |> deal(7) |> check_flush())
mean(out)
```

## Q5

Explain in English how the `check_straight` command determines the hand is a straight.
