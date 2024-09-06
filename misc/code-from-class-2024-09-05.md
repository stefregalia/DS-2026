```
require(dplyr)

d1 <- expand.grid(
    suit = c("heart","diamond","spade","club")
  , value = 1:13
  , KEEP.OUT.ATTRS = FALSE
  , stringsAsFactors = FALSE
)

d1 <- d1 |> 
  mutate(face = case_when(
      value == 13 ~ "King"
    , value == 12 ~ "Queen"
    , value == 11 ~ "Jack"
    , value == 1 ~ "Ace"
    , TRUE ~ as.character(value)
  ))

deal <- function(x, k=5){
  if(is.vector(x)) return(x[1:k])
  x[1:k,]
} 

deal(d1)
deal(1:100,6)

shuffle <- function(x){
  rows <- sample.int(nrow(x),nrow(x))
  x[rows,]
} 

x[c(13,1,12),]
x[c(13,13,13),]

d1 |> shuffle() |> deal()
```