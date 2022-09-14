---
title: 'Topic : Data Manipulation'
author: "Kamlesh Pandey"
date: "9/14/2022"
output: 
  html_document:
    toc : true
    toc_float: true
    code_folding: show
---

# Objective

The overall objective of this project report is to manipulate data that might come in several format like csv, excel and share some key finding to the audience based on the data wrangling steps you perform on the dataset. For this project we have used a csv dataset, but similar steps can be cascaded to other type of data storage format.

# Importing Library

For this project, I have used following R libraries for my data pre processing, manipulation and visulaization purpose. 

```{r, eval=FALSE, include=TRUE}

library(readr)
library(readr)
library(dplyr)
library(tidyr)

```

# Data Pre-processing

Data pre-processing can be a daunting task as we have to analyse the dataset in every aspect. First, we need to check the type of data we are importing either from a URL or from local directory. After that one need to check the metadata provided along the dataset. Analyzing metadata information is crucial as it gives direction for data manipulation steps involved. 
Our dataset has one categorical feature which describe the state in the United State and rest are numerical features describe several type of enrollment value for respective states.

Data pre-processing can have several steps based on the data we are processing, but in this case our pre processing is limited to few steps.

1. First step is getting data, for this part we are using *readr* library from dplyr package. The read_csv function will take a URL as an argument and save that csv file into a tibble format.

2. For our analysis purpose we are only considering limited feature columns sucn as *area_name, STCOU, and all columns ending with 'D'*.

3. Third step in the pre processing part is to extract valuable information from each columns such as Survey, value and year.

4. For later visualization purpose we are extracting some numerical characters (which are years of measurement in YY format). Later with those extracted key we are creating a features columns for ears of measuremnt in YYYY format.

```{r, eval=FALSE, include=TRUE}
sheet1 <- readr::read_csv("https://www4.stat.ncsu.edu/~online/datasets/EDU01a.csv")
sheet1 <- sheet1 %>% select(ends_with("D"), 'Area_name', 'STCOU') %>%
                     rename(area_name = 'Area_name')%>%
                     mutate_at('STCOU', as.numeric)

# Converting data into long format
sheet1 <- sheet1 %>% 
          pivot_longer(cols = ends_with('D'),
                       names_to = 'Item_id', values_to = 'Value')

# Year Extraction
last_Two_Digit      <- as.numeric(substr(sheet1$Item_id, 8,9))
sheet1$Survey       <- substr(sheet1$Item_id,1,3)
sheet1$ValueType    <- substr(sheet1$Item_id,4,7)
sheet1$Year         <- NA

# Loop to get year column in YYYY format
for (i in 1:length(last_Two_Digit)){
  if (last_Two_Digit[i] < 22){
    sheet1[i,7] <- paste0(200, last_Two_Digit[i])
  }
  else if (last_Two_Digit[i] > 22){
    sheet1[i,7] <- paste0(19, last_Two_Digit[i])
  }
  
}
```





