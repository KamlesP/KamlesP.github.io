---
title: 'Data Manipulation Project'
author: "Kamlesh Pandey"

---

# Objective

The overall objective of this project report is to manipulate data that might come in several format like csv, excel and share some key finding to the audience based on the data wrangling steps you perform on the dataset. For this project we have used a csv dataset, but similar steps can be cascaded to other type of data storage format.

# Importing Library

For this project, I have used following R libraries for my data pre processing, manipulation and visualization purpose. 


# Data Pre-processing

Data pre-processing can be a daunting task as we have to analyse the dataset in every aspect. First, we need to check the type of data we are importing either from a URL or from local directory. After that one need to check the metadata provided along the dataset. Analyzing metadata information is crucial as it gives direction for data manipulation steps involved. 
Our dataset has one categorical feature which describe the state in the United State and rest are numerical features describe several type of enrollment value for respective states.

Data pre-processing can have several steps based on the data we are processing, but in this case our pre processing is limited to few steps.

1. First step is getting data, for this part we are using *readr* library from dplyr package. The read_csv function will take a URL as an argument and save that csv file into a tibble format.

2. For our analysis purpose we are only considering limited feature columns such as *area_name, STCOU, and all columns ending with 'D'*.

3. Third step in the pre processing part is to extract valuable information from each columns such as Survey, value and year.

4. For later visualization purpose we are extracting some numerical characters (which are years of measurement in YY format). Later with those extracted key we are creating a features columns for ears of measurement in YYYY format.

5. After setting all relevant feature columns it is important to make one dataset for each data type (county and non-county in this case).


# Functions

For all pre processing step, if we have a single data source it is convenient to write simple line of R code for each step. But the same process becomes a mammoth task once we have more datasets and all need to go through same pre processing step. In that case writing R code individually is not a viable option and also not a *Good Programming Practice (GPP)*.

So to provide a scalable factor  in the model I have used function for each pre processing step so that in future if I need to go through the exploratory data analysis of any other similar kind of dataset I don't have to write similar code again.  


# Result & Conclusion

This project will help in writing efficient code in R language. Additionally, this project will also introduce about writing functions in R language.
Other potential takeaways from the project is the concept of making customized plots for a particular type of dataset with *class*.



[Link to my project report](https://kamlesp.github.io/Pandey_Kamlesh_ST558_Project1.html)


Thank You for checking my work!!!!
