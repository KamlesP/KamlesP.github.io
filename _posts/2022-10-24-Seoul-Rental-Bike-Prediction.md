# Data Import
This dataset belongs to the bike demand in Seoul. In Seoul city, for the enhancement of public mobility rental bikes are introduced. The bike demand depend upon several factor like season, temperature etc. This datasets has 8760 observations and 13 predictors to predict the renatal bike demand in the city. 

```{r}
library(dplyr)
library(readr)
library(gmodels)
library("viridis")
library(tidyr)
library(PerformanceAnalytics)
library(ggplot2)
library(car)
library(gridExtra )
library (leaps)
library(glmnet)
library('caret')
df <- readr::read_csv('SeoulBikeData.csv', locale = locale(encoding = 'latin1'))
head(df,8)
```
# Exploratory Data Analysis
Following exploratory data analysis applied on the dataset:

## Missing Values
Renaming predictors and checking if missing values are present in the observations.
```{r}
# renaming predictor name 
df <- df%>%rename(rented_bike_count = `Rented Bike Count`,
                   temperature_c = `Temperature(°C)`,
                   hour = Hour,
                   humidity_percent = `Humidity(%)`,
                   wind_speed_ms = `Wind speed (m/s)`,
                   visibility_10m = `Visibility (10m)`,
                   dew_point_c = `Dew point temperature(°C)`,
                   solar_rad = `Solar Radiation (MJ/m2)`,
                   rainfall_mm = `Rainfall(mm)`,
                   snowfall_cm = `Snowfall (cm)`,
                   seasons = Seasons,
                   holiday = Holiday,
                   func_day = `Functioning Day`,
                   )
paste0("Total number of missing values in the dataset " , sum(is.na(df)))

# removing date predictor from the dataset
df <- df %>% select(everything(), -Date)

```
## Correlation Plot  
Correlation plot is to check how predictor are related with the response variable. Ideally, there should not be a correlation among the predictors. When multicollinearity is present, other predictor will not provide unique or independent information in the regression model.  
From the plot, hours, temperature has strong positive correlation with the number of rental bike. Also rainfall has a negative correlation with the response variable which is very well estimation of real life scenario.
We can also estimate that some predictor variables are highly correlated with wach other such as temperature and dew point.  
Common way to detect multidisciplinary among the variable is VIF(variable inflation factor). From the bar plot Temperature, Humidity and Dew point has very high vif. This behavior we can be corroborated from the correlation plot where Temperature, Humidity and Dew Point are strongly correlated to each other.  

## Histogram Plot  
To understand the distribution of numerical features and to generate a frequency table for all numeric variable.
```{r, warning=FALSE, message=FALSE}
par(mfrow = c(4,2))
par(mar = c(3,3,3,3)) # set margin for plots
hist(df$temperature_c)
hist(df$humidity_percent)
hist(df$wind_speed_ms)
hist(df$visibility_10m)
hist(df$dew_point_c)
hist(df$solar_rad)
hist(df$rainfall_mm)
hist(df$snowfall_cm)
```
