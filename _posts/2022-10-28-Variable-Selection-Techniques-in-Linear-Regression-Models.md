# Introduction
A model servers three basic purposes, first model should aim to correctly predict an outcome value from a set of predictors. Seconly, a model should be able to explain
the differences in outcome values by differences in exploratory variables. Finally, model should be able to capture the association between the dependent and independent variables. Based on the type of required output, generally two type of regression model are often used, linear and logistic regression model. Because of linear predictor and regression coefficients, these model are very popular for any statistical study. 
Variable selection is important, but Why?
1. As universal scientist and artist Leonardo da Vinci once said "Simplicity is the ultimate shophistication", we want to make our model as simple as possible and remove reducnfdant predictor for a better interpretability, simplicity and relevance of a statistical model.
2. Redundant predictors will add noise in the model and may lead to overfitting of the model, eventaully poor performance in test / validation set
3. redundant varaible may induce collinearity in the model.
4. Cost: A model with too many redundant predictor will cost a lot in training.

# Interpretation of regression Coefficient
The fundamental interpretation of linear regression coeffieicnts in a linear regression model is that "of the expected chaneg in outcome (or log odds or log hazard) if change by a unit keeping all other predictor varibale held constant "

# Creteria for Selecting Variables

## Forward Selection
This method add variables in the model until there is no remaining predictor variable (outside the model) that can add any significanct to the dependent variable. Forward selection method starts with no variable and continuously adds new variable. A test statics is used to comapre the performance of the model. These test statistics can be a R-square for a continuous dependent variable. The model with largest test statistic value is considered as a best model. 

## Backward Selection
This method deletes variables from the model untill all variable contribute something significant to the model. A test statistics is used and and variables deleted from the model one by one. backward selection starts with all variables in first place and then variables deleted one by one untill all the varaibles remaining in the model have a test statistics value greater than the threshold.

## Information Criteria:
There is a inherent diffence between the significance and inforamtion criteria. While a significance criteria is used for decising which preditor variable should be included or excluded form the model, the focus of information criteria is on selecting a model from a set of plausible models based on the criteria. Since including more predictor in the model will slightly increase the model fit, the informaion criterias were deveoped to penalize the apperant model for the complexicity. 
AIC and BIC method are used to compare two models. These methods are also used to select one of the best model from all paussible models. For example, AIC and BIC creterias are commonly used in case of best subset selection out of 2^k models (for K number of predictor varibales).

<img
  src="/docs/assets/bic.png"
  style="display: inline-block; margin: 0 auto; max-width: auto">

## Peanalized Likelihood
Model selection using a penality methods are very popular. Two type of penalized method are common, LASSO (Least angle selection and shrinkage operator) and RIDGE. These regression model are very easy to implement PROC GLMSELECT in case of SAS and in R using glmnet package. These tools allows to fit linear model with penalties and tune the lambda (shrinkage parameter). 
Penaly methods are gemerally preferred in high dimesntionality model i.e predictor variable far exceed the number of sample size(k>>n) . In case of a low domensional problem  LASSO is not preferred, and people are more interested in interpretable regression coefficients. 

<img
  src="/docs/assets/lambda.png"
  style="display: inline-block; margin: 0 auto; max-width: auto">
  


# Conclusion
Finiding best set of subset is an expansive process in terms of time and computation. The pressing aim to have better model with good test statitics on a unseen dataset. These methods should be prmarily considered as a guiding purpose. 
