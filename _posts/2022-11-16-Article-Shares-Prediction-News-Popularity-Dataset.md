# Predicting Article Shares : [News Popularity Dataset](https://archive.ics.uci.edu/ml/datasets/Online+News+Popularity)

## Introduction
This project is aimed at building a prediction model that can predict number of shares a article can receive based on several predictors. The news popularity dataset is available at UCI data repository. This project is based upon the type of article belongs broadly six categories (tech, entertaintment, lifestyle, business, social media, and world). This project further explains the powerful **R markdow** by including six broad news categories and redering all reports simultaneously. 

## Dataset & EDA
News popularity dataset has total 7057 observations expalined by 61 predictor columns. To explain the data set in a better way we used **ggplot** library to visulaize the plots betweeen the preditors and resoinse variables. The plots generated for our analysis includes correlation between the number of shares and number of words in the article, and number of article shared on every day of a week. Further, we also craeted some new columns to explain the data set in a better way such as how global negative word rate varying with golbal sentiment polarity across a week and number of shares nased on keyword in a week. Some other plots were also generated to understand and preprocess the predictors accordingly foe the modelling.

## Models  
For this project we are trying to fit a linear regression model and tress based model. 





The data set has number of shares as a predictor variable and it has negatively skewed distribution. So for preprocessing the data we consider taking log value of shares. 

