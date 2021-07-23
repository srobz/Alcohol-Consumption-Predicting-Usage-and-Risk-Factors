
# Alcohol Consumption: Predicting Usage and Risk Factors
## Module 3 Final Project



## Introduction

The purpose of this project was to build a classification regression model identifying the likelihood of an individual being a user of alcohol. It is my hope that the results of this can benefit community outreach programs so that they may better identify and assist those at risk.

Following the Data Science approach of OSEMN, as outlined and detailed below, I was able to determine a final model that accurately identifies users of alcohol as well as the most important features in those identified users.


## The Data Science Process: OSEMN

### Obtain

The data used for this project was obtained from UC Irvine's Machine Learning Repository at https://archive.ics.uci.edu/ml/datasets/Drug+consumption+%28quantified%29 it should be noted that the dataset was broadly about Drug Consumption, not just alcohol.

### Scrub

When the data was received it was filled with placeholder values, all of which was changed based on information provided from the UCI repository. It is during this part of OSEMN that I converted the datatypes appropriately. I also decided to make this a binary classification and change the type of drug user from how often the individual used (daily, weekly, monthly, etc.) to user/non-user.

### Explore

During this step I looked at all the continuous features as well as the categorical features. While looking at personality score measurements, I found that Neuroticism and Conscientiousness incited further questions. I also wanted to know more about if level of education had an effect on whether or not one uses drugs. It was during this time that I did some further exploration and sought to answer some questions based on the data about what might make one more likely to be not just an alcohol user but a user of multiple drugs:

* Are those who score higher on Neuroticism more likely to be drug users than those who score lower?
    
![graph](https://raw.githubusercontent.com/srobz/Module-3-Project/main/Visualizations/DrugUsagexNeuroticism.png)
    
* Are those who score lower on Conscientiousness more likely to use drugs than those who score higher?

![graph](https://raw.githubusercontent.com/srobz/Module-3-Project/main/Visualizations/DrugUsagexConscientiousness.png)
    
* Which makes you more likely to be a drug user, having a Doctorate or a Masters degree?
    
![graph](https://raw.githubusercontent.com/srobz/Module-3-Project/main/Visualizations/DrugUsagexEducation.png)

Following my further exploration, I did a check for multicollinearity as well as created dummy variables for all the categorical variables, which for this dataset was most of the features. Upon feature selection using Statsmodel's Ordinary Least Squares (OLS), I ended up removing all the personality score measurements (which were all of the continuous features), as well as twelve of the categorical features.

### Model

I took a brute force approach and tried six different models, then compared their ROC curves and model scores. This approach allowed me to determine two top models, Logistic Regression and AdaBoost. They both had training and test accuracies around 92-93% and AUC values around 0.68. To find the best model, I tuned these two multiple times.

I tuned the Logistic Regression model a total of five times, implementing a different value for C each time. I tuned the AdaBoost model 8 times, varying the number of estimators, learning rate, and mixing and matching the two changed values. Again, I compared the tuned model ROC curves and scores to find my best and final model.

### iNterpret

The final model is the AdaBoost model with the number of estimators set to 100. This model accurately predicts whether or not an individual is a user of alcohol with a cross validation score of 99.4% and training and teseting accuracy between 92 and 93%.

![graph](https://raw.githubusercontent.com/srobz/Module-3-Project/main/Visualizations/TunedAda2.png)

    

## Conclusion

After selecting features during exploratory data analysis, fitting multiple models, and tuning the best of those models, it was determined that the AdaBoost model with the number of estimators set to 100 performs the best. This model accurately predicts whether or not an individual is a user of alcohol with a cross validation score of 99.4% and training and testing accuracy between 92 and 93%. 

The top five features in order are:

* Age_18-24
* Age_25-34
* Caffeine
* Country_UK
* Ethnicity_Other

This means that these features are most important in determining whether or not an individual is a user of alcohol. During the EDA I had postulated that personality measurement scores would indicate a stronger likelihood of usage but those features were dropped during feature selection. I had also looked into whether higher levels of education made one more likely to be a drug user (not just alcohol) however based on these results it appears as though the level of education is not as important in determining alcohol usage.



## Citation

1. Drug Consumption (quantified) Data Set. Available at: https://archive.ics.uci.edu/ml/datasets/Drug+consumption+%28quantified%29


## Repository Organization

- ['Module 3 Project - 1. Data Cleaning.ipynb'](https://github.com/srobz/Module-3-Project/blob/main/Module%203%20Project%20-%201.%20Data%20Cleaning.ipynb) : Jupyter notebook of Data Cleaning with code and comments
- ['Module 3 Project - 2. Data Exploration.ipynb'](https://github.com/srobz/Module-3-Project/blob/main/Module%203%20Project%20-%202.%20Data%20Exploration.ipynb) : Jupyter notebook of Data Exploration with code and comments
- ['Module 3 Project - 3. Data Modeling.ipynb'](https://github.com/srobz/Module-3-Project/blob/main/Module%203%20Project%20-%20%203.%20Data%20Modeling.ipynb) : Jupyter notebook of Data Modeling with code and comments
- [Module 3 Presentation.pdf](https://github.com/srobz/dsc-mod-2-project-v2-1-online-ds-sp-000/blob/master/Module%202%20Presentation.pdf) : Project presentation
- ['Visualizations'](https://github.com/srobz/Module-3-Project/tree/main/Visualizations) : Folder containing graphs used in ReadME
- ['drug_consumption.data'](https://github.com/srobz/Module-3-Project/blob/main/drug_consumption.data) : Original dataset used for project
- ['UpdatedDF.csv'](https://github.com/srobz/Module-3-Project/blob/main/UpdatedDF.csv) : Updated dataset from the end of Module 3 Project - 1. Data Cleaning
- ['ModelDF.csv'](https://github.com/srobz/Module-3-Project/blob/main/ModelDF.csv) : Updated dataset from the end of Module 3 Project - 2. Data Exploration
- [README.md] : ReadMe
