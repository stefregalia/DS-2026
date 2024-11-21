# Clinical trial

Serum creatinine is a blood measurement.  High serum creatinine values (greater than 1.4) may indicate poor renal function.

In this group project, you will collect and analyze data from a clinical trial in which individuals with high serum creatinine are randomized to placebo or treatment.  The goal of the trial is to determine if the treatment reduced serum creatinine levels compared to placebo.  Serum creatinine is measured at baseline and after size weeks of treatment.  To collect data for the trial, navigate to [http://api.tgstewart.cloud/random](http://api.tgstewart.cloud/random).  Each time the site is refreshed, the data for a new trial participant is generated.  It may look something like this:

```
baseline	1.611
trt	        1
endpoint	1.701
```

The variables `baseline` and `endpoint` are the serum creatinine values at baseline and six weeks.  The variable `trt` is 1 if the participant was randomized to treatment or 0 if randomized to placebo.

As a group, do the following:

1. Create a dataset of trial data, collecting as many observations as you deem needful to answer the research question.
2. Create an html quarto report (with `embed-resources: true`) with the following elements:
   1. The dataset via the `datatable` command in the `DT` library.
   2. A visualization comparing the distribution of baseline serum creatinine values between treated and placebo groups.  
   3. An estimate of the endpoint distributions using maximum likelihood, method or moments, or kernel density estimation.  Create a single figure which shows the estimates of the pdf for both groups.  Use labels or a legend to identify each pdf.
   4. Create a new variable which is the difference between the endpoint and baseline measurement.  Using the new variable, repeat the previous step.
   5. Based on your visualizations, do you think the treatment works?  Why or why not?

## Submission instructions:

1. In Canvas, navigate to `People` then `MLE & Method of Moments Group`
2. Add yourself to the same group as your partners.
3. Submit a single html report for the group in Canvas in the assignments tab.
4. Make sure every group member's name is on the report.
   
