## Exercises and solutions for Chapter 5

### Classification 
For this set of exercises we will be using the gene expression and patient annotation data from the glioblastoma patient. You can read the data as shown below:
```{r,readMLdataEx,eval=FALSE}
library(compGenomRData)
# get file paths
fileLGGexp=system.file("extdata",
                      "LGGrnaseq.rds",
                      package="compGenomRData")
fileLGGann=system.file("extdata",
                      "patient2LGGsubtypes.rds",
                      package="compGenomRData")
# gene expression values
gexp=readRDS(fileLGGexp)

# patient annotation
patient=readRDS(fileLGGann)

```

1. Our first task is to not use any data transformation and do classification. Run the k-NN classifier on the data without any transformation or scaling. What is the effect on classification accuracy for k-NN predicting the CIMP and noCIMP status of the patient? [Difficulty: **Beginner**]

2. Bootstrap resampling can be used to measure the variability of the prediction error. Use bootstrap resampling with k-NN for the prediction accuracy. How different is it from cross-validation for different $k$s? [Difficulty: **Intermediate**]

3. There are a number of ways to get variable importance for a classification problem. Run random forests on the classification problem above. Compare the variable importance metrics from random forest and the one obtained from DALEX. How many variables are the same in the top 10? [Difficulty: **Advanced**]

4. Come up with a unified importance score by normalizing importance scores from random forests and DALEX, followed by taking the average of those scores. [Difficulty: **Advanced**]

### Regression
For this set of problems we will use the regression data set where we tried to predict the age of the sample from the methylation values. The data can be loaded as shown below: 
```{r, readMethAgeex,eval=FALSE}
# file path for CpG methylation and age
fileMethAge=system.file("extdata",
                      "CpGmeth2Age.rds",
                      package="compGenomRData")

# read methylation-age table
ameth=readRDS(fileMethAge)
```

1. Run random forest regression and plot the importance metrics. [Difficulty: **Beginner**]

2. Split 20% of the methylation-age data as test data and run elastic net regression on the training portion to tune parameters and test it on the test portion. [Difficulty: **Intermediate**] 

3. Run an ensemble model for regression using the **caretEnsemble** or **mlr** package and compare the results with the elastic net and random forest model. Did the test accuracy increase?
**HINT:** You need to install these extra packages and learn how to use them in the context of ensemble models. [Difficulty: **Advanced**] 