# EDA With NASA APIs

This project is based on accessing data from APIs and evetually perfoeming analysis on them. For this project, I have Asteroid data infromation from  NASA API.
This API has only one end point and two modifications. Th user can input a start and a end date and the API will retrieve data from the server between two date range.
Final project can be found at [Final Project link](https://sbgadhwala.github.io/ST558_Project2/)

I have used multiple R packages for this project, few of them are listed below:
1. [httr](https://httr.r-lib.org/) -  For web API
2. [jsonlite](https://cran.r-project.org/web/packages/jsonlite/vignettes/json-aaquickstart.html) - maping json and R data
3. [lubridate](https://lubridate.tidyverse.org/) - to handel dates in the data 
4. [ggplot](https://ggplot2.tidyverse.org/) - for visualization


# Project Workflow
The first step in data manipulation is to get data. We can get data from a csv file, a SAS dataset, or from a API. To retrive data from API we use GET request, in R GET request handeled by httr package. The data was stored in a nested dictionary format, so I need to go through nested dictionary to get desired data from the json file. Once data available one need to check if the data has any missing value and the data type so that pre processing can be applied on the dataset. In Asteroid dataset there was no missing value but the dates and other numerical features were in string format. SO to convert them into desired format I utilized the concept of explicit coercion. Once data available in correct format we can step toward EDA.

The EDA part consist of genearting a new column based on the exisiting input columns and them applying statistical technique to interpret and genearte some finding from the data. For EDA visulaization is a big tool, and in my project I have used ggplot package from R library.

# Challages and Future Approach
The biggest challange for me to select right data for the analysis. In my case Asteroid has very limited numrical features for the analysis and data points[77x8]. Other challnge was to get data and convert them into a feature vector was a challenge. As discussed the Asteroid dataset hase very limited numerical feature columnns and most of these columns are nested deep insode the json file. To correclty understand the json structure and then apply chaning to get desired feature column was a challeneg. 
In future projects, I will recosnider the dataset selection approach, so that I can analysze the data in a better way. 
