HW 9
======================

### Problem 1: Exponential Distribution - Estimating the Rate Parameter

**Problem:** You observe the following waiting times (in minutes) for a bus: 2.5, 5.1, 1.8, 3.6. Assuming the waiting times follow an exponential distribution, estimate the rate parameter ($\lambda$) using MLE.

### Problem 2: Normal Distribution - Estimating Mean and Variance

**Problem:** A sample of student heights (in inches) is: 65, 68, 72, 63, 70. Estimate the mean ($\mu$) and variance ($\sigma^2$) of the height distribution using MLE, assuming heights are normally distributed.

### Problem 3: Poisson Distribution - Estimating the Average Number of Events

**Problem:** You count the number of cars passing a certain point on a road per minute for 5 minutes and get: 3, 5, 2, 4, 6. Estimate the average number of cars passing per minute ($\lambda$) using MLE, assuming a Poisson distribution.

### Problem 4: Uniform Distribution - Estimating the Upper Bound

**Problem:** You have the following measurements of the length (in cm) of a manufactured part: 1.2, 1.8, 1.5, 1.7, 1.3. Assuming the lengths are uniformly distributed between 0 and $\theta$, find the MLE for $\theta$.

### Problem 5

Model the pendrop data in 3 different ways

```{r}
pendrop_data <- readRDS(url("https://tgstewart.cloud/pendrop.RDS"))
```

1)  Weibull with Method of Moments. Write the value of the parameters

2)  Weibull with MLE. Write the value of the parameters.

3)  With KDE (your choice of the kernel).

For each model compute the probability that the measure is less than 4cm, and compare them.

Plot the 3 models, and the pendrop histogram, in the same figure.
