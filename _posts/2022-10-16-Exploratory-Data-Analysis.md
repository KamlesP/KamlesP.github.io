We oftern come across a situation where we want to analyse an experiment, we are looking for an answr of how several input parameters are affecting the final output of the process? First step in this process to have a dataset, if not then we need to genearte datasets either by carring out surveys or if we doing out an experiment then we can generate simulated data from the computational softwares like COMSOL, ANSYS and Simulink. Once we have a dataset then we can process for EDA( exploratory data analysis) to answer common questions related to the experiment,

# Exploratory Data Analysis
In simple term, EDA referes to performing visualization and identifying informations and pattern about the dataset. This information can be anything such as a pattern or tread in the dataset, missing values, correlation coefficeints between the parameters and potential outliers. These features are important for our hypothesis testing and coming out with an probablistic model which can help a firm in increasing sales and profit from their products.

# Before EDA(Exploratory Data Analysis)

Before starting a EDA, one should ask to the purpose of the expeiment or the data i.e understaning at high level. Based on the type of insights you want from the dataset the type of EDA might differ. Once you have the high level understanding the your focus must shift to understand more about the dataset i.e number of columns and rows in the dataset, size of dataset. Is the size too big, do we need additional computational power to process the dataset, you should have idea of such question before jumping into EDA.
 Below I have attached mtcars dataset from the R in built datasets. We can see that the dataset has 32 rows and 11 columns.
 
<img
  src="/docs/assets/r1.png"
  style="display: inline-block; margin: 0 auto; max-width: auto">
 
 With dataset you should have a good understanding of what each paramter represent in the dataset, and with that details you should keep a notepad where you shuould keep summary regarding the dataset.
 
 # Possible Steps in EDA(Exploratory Data Analysis) 
 
 ## Missing Data
You should start the exploratory data analysis with exploring if tht dataset has any missing value or not. If dataset has large number of input features, it is useful to count the number of missing values and visualy plot them. In mtcar dataset no missing value reported.

```{r}

sum(is.na(mtcar))

```