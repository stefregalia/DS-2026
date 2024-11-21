# 2024-11-12 In-class group exercise

### Question 1

Based on the Method of Moments, find the Gamma distribution for the pendrop dataset.

Plot the pendrop histogram and the estimated gamma distribution in the same graph.

```{r}
pendrop_data <- readRDS(url("https://tgstewart.cloud/pendrop.RDS"))
```

Find the probability of a measure lower than 4.



### Question 2

#### Coin Toss - Estimating the Probability of Heads

**Problem:** You flip a coin 20 times and get 7 heads. Estimate the probability of getting heads using MLE.

Plot the estimated binomial distribution.

Find the probability of 10 or more heads in 20 flips.

## Submission instructions:

1. In Canvas, navigate to `People` then `MLE & Method of Moments Group`
2. Add yourself to the same group as your partners.
3. Submit a single quarto html report (with `embed-resources: true`) for the group in Canvas in the assignments tab.
4. Make sure every group member's name is on the report.
   
