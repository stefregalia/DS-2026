HW: Data types and visualizations

## Submission instructions

*  Please submit your report in **.html** format to **Canvas**.  (Note that this is different from past assignments which were submitted to gradescope.)  


Please review the slides about [data types](https://tgstewart.cloud/compprob/datatypes.html) and the class notes on [data summaries and visualizations in R](https://tgstewart.cloud/compprob/summaries-visualizations.html).

1. Please find a publicly available dataset (or create one of your own) that includes nominal, ordinal, interval, ratio, and binary variables.  Use the [`DT` package (link)](https://rstudio.github.io/DT/) to include the data frame in your report. (You can delete any columns that you aren't using.)  If your data frame is called `my_data`, then the code chunk to include the data frame in the report is:

```
library(DT)
datatable(my_data)
```

2. Create a report that summarizes with tables and figures the variables in your dataset.