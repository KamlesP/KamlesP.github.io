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
