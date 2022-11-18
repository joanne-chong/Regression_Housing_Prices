# Regression Analysis for Housing Prices in Ames, Iowa

## Overview
The value of a property is based on what buyers are willing to pay for - however, these reasons are usually complex and multifaceted. Therefore, a regression analysis is used to determine the various factors and its magnitude in influencing housing prices. 

For this project, we'll be assuming the role of business analysts at a real estate company to answer these challenges:
1. What are the key predictors of housing prices? And how much influence does the variable have on prices?
2. Which regression model would predict housing prices most accurately? Will this model be generalizable to new datasets?

Based on these findings, we'll provide real estate agents recommendations on how to utilize the regression model to help homeowners get the best price for their property. 

## Dataset & Methodology

### About the dataset
The dataset contains 2,930 observations on the sale of individual residential property in Ames, Iowa from 2006 to 2010. There are a total of 80 variables involved in assessing home values, of which 23 are nominal, 23 are ordinal, 14 are discrete, and 20 are continuous factors. 

More information on the dataset can be found here. ([*source*](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt))

For this project, the data has been split into two sets:
- [`Train.csv`](../datasets/train.csv): There's a total of 80 features, 1 sale price and 2,051 observations.
- [`Test.csv`](../datasets/test.csv): There's a total of 80 features and 879 observations. The sale price is missing from this set, which we will use our model to predict. 

### Additional Reference
[Ames, Iowa Housing Set Data Information](http://jse.amstat.org/v19n3/decock.pdf)
- This guidance was written by the data owner on how educators can use the dataset for Statistics courses. 
- I referred to this guidance to better understand the dataset, how it was collected, how to best approach feature selection and implement the regression models.

### Methodology
For this project, we've conducted a thorough analysis and modeling through these steps:
1. **Data Cleaning**: We assessed the training dataset for any outliers and removed them immediately. We also checked for missing values where we've filled them or removed them if irrelevant.
2. **Exploratory Data Analysis**: We visualized the dataset through a series of graphs and plots to better understand the relationships between variables as well as its individual impact on housing price.
3. **Feature Selection & Engineering**: After evaluating specific variables, we removed variables that didn't have much impact on prices and combined variables that were relevant to each other.
4. **Data Modeling & Evaluation**: Following the selection of feature, we modeled them through three types of regression models - Linear, Lasso and Ridge. The best model will then be used to predict the sale prices in the test dataset. 

We've also uploaded the predicted prices on ([Kaggle](https://www.kaggle.com/competitions/dsi-us-11-project-2-regression-challenge)) to identify the Root Mean Square Error (RMSE) - a metric that measures how far predictions vary from true values.

## Modeling Summary
1. The differences in R2 and RMSE scores across the three models (Linear, Lasso and Ridge) are very minor, indicating that regularization models didn't make much difference to the prediction - this also means that the variables are resilient and independent of models.
2. Linear model appears to perform better on the training set, based on the `R2 Train Set` and `RMSE Train Set` scores.
3. The Ridge model has the best performance for the test set and cross-validation sets, which we would trust for higher accuracy as the model was run unseen data.

Hence we've decided to go ahead with the Ridge model produce the Sale Price on the validation set and compare it against the actual Sale Price listed. We also used the model to predict the Sale Price on test dataset which was uploaded to Kaggle.

### Modeling Results
The top five predictors are: 
1. `Total SF`: This includes living area, 1st floor and 2nd floor
2. `Overall Qual`: This refers to the overall material and finish of the house
3. `BsmtFin SF`: This refers to the finished basement area 1 in square feet
4. `Kitchen Qual`: This refers to overall kitchen quality
5. `Garage Area`: This refers to the size of the garage space

Interestingly, certain neighborhoods are also strong price predictors - these are Stone Brook and Northridge Heights. Other basement and garage features are also important price predictors, signaling that these are important factors for buyers.

On the lower end of the graph and chart, when the house was last remodeled and houses with 2-stories had a negative correlation on the price. It's also interesting to note that basement finish type 1 had a negative impact on house price, when the area of basement finishing in square feet is a strong predictor - this could be because of the way the study was done that may not have gathered accurate insight or buyers may prefer lower quality/ unfinished basement area for them to renovate to their preference later on.

## Conclusion
In summary, our model has 32 key predictors of housing prices. The coefficient value listed indicate the magnitude of influence the predictor has on housing price. Taking the top five predictors:
1. `Total SF`: With a 1 unit increase in area square feet, we can see 24,455.45 dollars increase in housing price.
2. `Overall Qual`: When the overall quality and finish of the house improves by 1 unit, housing price increase by 13,428.89 dollars.
3. `BsmtFin SF`: As finished basement area increases by 1 unit square feet, the house price will increase by 9,868.87 dollars.
4. `Kitchen Qual`: As overall kitchen quality increases by 1 unit, the house price will increase by 9,713.65 dollars.
5. `Garage Area`: When the size of the garage space increases by 1 unit square feet, the price increase by 6,714.52 dollars. 

While we selected the Ridge model due to the slight improvement in cross-validation score, our results from the three models (Linear, Lasso, Ridge) had minor differences from each other. This reaffirms that the variables selected are robust enough to predict prices regardless of the model selected - hence making the model generalizable to new datasets*.

*This model is most applicable to housing datasets for Ames, Iowa. While this model can be used in other location, but we encourage keeping in mind the different external factors present in other areas as well.

## Recommendations
Through this model, real estate agents can advise homeowners to increase their property's market value by:
- Expanding the area in the house and garage space through renovation
- Maintaining and enhancing the house exterior and finishing 
- Refresh and revamp kitchen to include newer furnishing and appliances
- While having a nice basement is a nice touch, but owners should focus on other aspects of the house as buyers are likely to prefer a bigger basement over a nice basement

Real estate agents in Ames, Iowa will also be equipped to:
- Ensure all home listings show all the top predictors in the best light to attract buyers 
- Look into the features and better understand why some of them matter and some don't
- Ensure representation in data collection (some of the neighborhoods didn't have enough data to generate mean for Lot Frontage missing values earlier)
- In the next round of data collection, define the characteristics for categorical variables better, e.g. "Average" and "Fair" can sound similar to users, and can be combined


