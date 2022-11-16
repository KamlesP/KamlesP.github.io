# Predicting Article Shares : [News Popularity Dataset](https://archive.ics.uci.edu/ml/datasets/Online+News+Popularity)

## Introduction
This project is aimed at building a prediction model that can predict number of shares a article can receive based on several predictors. The news popularity dataset is available at UCI data repository. This project is based upon the type of article belongs broadly six categories (tech, entertainment, lifestyle, business, social media, and world). This project further explains the powerful **R markdown** by including six broad news categories and rendering all reports simultaneously.

## Dataset & EDA
News popularity dataset has total 7057 observations explained by 61 predictor columns. To explain the data set in a better way we used **ggplot** library to visualize the plots between the predictors and response variables. The plots generated for our analysis includes correlation between the number of shares and number of words in the article, and number of articles shared on every day of a week. Further, we also created some new columns to explain the data set in a better way such as how global negative word rate varying with global sentiment polarity across a week and number of shares based on keyword in a week. Some other plots were also generated to understand and preprocess the predictors accordingly foe the modelling.

## Models  
For this project we are trying to fit a linear regression model and tress-based model. In case of linear regression, we started with using multiple linear regression model considering null hypothesis that the coefficients of all predictors are zero. With a confidence interval of 95% we considered all significant predictors for fitting linear model. For fitting a linear model, we have used caret package with cross validation of 5.
For other linear model, we used Lasso Regression model. For lasso regression getting a perfect value of shrinkage parameter is important, so for this we used grid search approach in caret package and with best lambda, the model was trained.

For tree-based modeling we used Random Forest and Boosting. Since we have huge number of predictors to fit, we used PCA to reduce the dimensionality of the dataset. Later based on the % of variance explained by the PCs different number of PCs used for different type data channel. These PCs further used to transform training and test data for Random Forest. By using dimensionality reduction method, we were able to reduce number of predictor variables from 58 to in range of 20s.
For boosting, we used a tune grid params to get best value for number of trees, depth for a constant shrinkage parameter.


## R Markdown Automation  
Automation part of this project is a key component. Building model for one data channel and extending same of all other data channel facilitated by using powerful R markdown. Following code chunk is used for automating reports in R.

```{r}
library(rmarkdown)
library(tidyr)

dataType = c(#'data_channel_is_lifestyle',
             # 'data_channel_is_entertainment',
             # 'data_channel_is_bus',
              'data_channel_is_socmed'
             # 'data_channel_is_world',
             # 'data_channel_is_tech'
             )

outputFile <- paste0(dataType, ".html")

#create a list of data channel type
params = lapply(dataType, FUN = function(x){list(data_channel = x)})

reports <- tibble(outputFile, params)


apply(reports, MARGIN = 1, 
      FUN = function(x){
        render(input = 'ST558_Project_3.Rmd', output_file = x[[1]], params = x[[2]])
      })

```

All analysis can be found here:  
[Technology articles analysis here](https://sbgadhwala.github.io/ST558_Project3/data_channel_is_tech.html)  
[Lifestyle articles analysis here](https://sbgadhwala.github.io/ST558_Project3/data_channel_is_lifestyle.html)  
[Entertainment articles analysis here](https://sbgadhwala.github.io/ST558_Project3/data_channel_is_entertainment.html)  
[Business articles analysis here](https://sbgadhwala.github.io/ST558_Project3/data_channel_is_bus.html)  
[Social Media articles analysis here](https://sbgadhwala.github.io/ST558_Project3/data_channel_is_socmed.html)  
[World article analysis here](https://sbgadhwala.github.io/ST558_Project3/data_channel_is_world.html)  



