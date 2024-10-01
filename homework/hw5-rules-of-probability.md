# HW: Rules of probability for two variables (Chapter 4)

## Submission instructions

*  Please submit a reproducible report in .pdf format to Gradescope.  
*  When you submit, you will indicate the location of each question and response in the report.  (This means you do not need to use `\newpage` to separate questions.)
*  In your response, please include the text of the question.

## Questions 

1. Machines A, B, and C generate widgets with a defect rate of 0.1, 0.01, and 0.001, respectively. Machine A generates twice as many widgets as B, and machine B generates twice as many widgets as machine C. Please complete the cross table below based on the information above.

Hints:
* What type of probability is the defect rate?  Where does this probability appear in the table?

|            |  A  |  B  |  C  |     |
|:-----------|:---:|:---:|:---:|:---:|
| Defective  |     |     |     |     |
| → cell     |     |     |     |     |
| → row      |     |     |     |     |
| → col      |     |     |     |     |
| Functional |     |     |     |     |
| → cell     |     |     |     |     |
| → row      |     |     |     |     |
| → col      |     |     |     |     |
|            |     |     |     |     |

2. If you did not know if a widget was functional or defective, what would be the probability that the widget is from machine A?  Write the solution using mathematical notation, as in P(???) = ???.

3. How would you update the probability from 2 if you knew the widget was defective? Write the solution using mathematical notation, as in P(???) = ???.

4. The following function simulates the widget problem from 2.2.  Create the cross table from question 1 empirically, using the function to mimic the manufacture of many widgets and generating the resulting cross table.  Be sure to use `set.seed`.

```
widgets <- function(R){
    machine <- sample(c("A","B","C"), R, replace=TRUE,prob=c(4,2,1)/7)
    defect <- rbinom(R,1,0.1*(machine=="A")+0.01*(machine=="B")+0.001*(machine=="C"))
    data.frame(machine=machine, defect=defect)
}
```

5. What is simulation error for P(machine A & defective)?

6. Here is the data from the in-class survey about soft drinks which you
will use in the following problems. *For the moment, we will exclude
reponses with missing values. (But, missing data is something we will
touch on in the future.)*

    require(dplyr)
    require(pander)

    d1 <- read.csv("https://tgstewart.cloud/soda.csv") |>
      filter(!is.na(cola) & !is.na(sugar))
    descr::CrossTable(
          d1$sugar
        , d1$cola
        , prop.chisq = FALSE
    ) |>
    pander(split.table=Inf)

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 31%" />
<col style="width: 19%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: center;"> <br />
d1$sugar</th>
<th style="text-align: center;">d1$cola<br />
Cola (Coke, Pepsi, etc.)</th>
<th style="text-align: center;"> <br />
Something else</th>
<th style="text-align: center;"> <br />
Total</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: center;"><strong>Regular (full
sugar)</strong><br />
N<br />
Row(%)<br />
Column(%)<br />
Total(%)</td>
<td style="text-align: center;"> <br />
10<br />
25.0000%<br />
50.0000%<br />
15.1515%</td>
<td style="text-align: center;"> <br />
30<br />
75.0000%<br />
65.2174%<br />
45.4545%</td>
<td style="text-align: center;"> <br />
40<br />
60.6061%<br />
<br />
</td>
</tr>
<tr class="even">
<td style="text-align: center;"><strong>Zero sugar or
diet</strong><br />
N<br />
Row(%)<br />
Column(%)<br />
Total(%)</td>
<td style="text-align: center;"> <br />
10<br />
38.4615%<br />
50.0000%<br />
15.1515%</td>
<td style="text-align: center;"> <br />
16<br />
61.5385%<br />
34.7826%<br />
24.2424%</td>
<td style="text-align: center;"> <br />
26<br />
39.3939%<br />
<br />
</td>
</tr>
<tr class="odd">
<td style="text-align: center;">Total<br />
</td>
<td style="text-align: center;">20<br />
30.303%</td>
<td style="text-align: center;">46<br />
69.697%</td>
<td style="text-align: center;">66<br />
</td>
</tr>
</tbody>
</table>

If the proportions in the contingency table represented
    probabilities, would drink preference and sugar preference be
    independent?

7. Is a preference for Cola positively or negatively or not associated
    with a preference for regular sugar?

8. Consider the population of individuals who suffer from migraine
    headaches.

<table>
<thead>
<tr class="header">
<th></th>
<th>Fewer than 3 migraines per month</th>
<th>3 or more migraines per month</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Less toxic treatment</td>
<td>.4</td>
<td>.1</td>
</tr>
<tr class="even">
<td>More toxic treatment</td>
<td>.3</td>
<td>.2</td>
</tr>
</tbody>
</table>

What can you conclude from this data about the effectiveness of the more
toxic treatment? (Hint: Section 4.7)