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
sum(is.na(mtcars))
```
Just condiser an idealy scenario when our dataset has more than 50% missing values. Fot such kind of sparse datset one possible solution can be to exclude the dataset from the main dataset. But if we simply remove the dataset then there high possibility that we introduce a bias in our dataset. So handling missing data is not a straightr forward case to understand more you can explore more about a separate bracnh of statistics Imputation.

## Summary Statistics of Data
At this point you will have idea about the missing values in the dataset still you don't have much idea about each feature columns available in the dataset. Potentially you need to have inforamtions like type of variable (continuous, discrete or categorical), mean, median, IQR, min and max value for the respective columns. These inforamtions will help in identifying type of visualization you can use to represent the data.

Correlation coefficient can be your best tool, it will give you information the relationship between two variables. Just consider we want to visualize the correlation between two continuous feature column, the best way is to plot them and calcualte perason correaltion coefficient. 

```{r}
# scatter plot between mpg and hp
gg <- ggplot(df, aes(x=mpg, y=hp)) + 
  geom_point(aes(col=cyl, size=gear)) + 
  geom_smooth(method="loess", se=F) + 
  xlim(c(05, 50)) + 
  ylim(c(20, 500)) + 
  labs(subtitle="MPG Vs HP", 
       y="Horsepower", 
       x="Miles per gallon", 
       title="Scatterplot", 
       caption = "Source: mtcars")

plot(gg)
```

<img
  src="/docs/assets/p2.png"
  style="display: inline-block; margin: 0 auto; max-width: auto">

Box plot can be your other tool to carry out EDA with the data. Fiding out outlier in your dataset is a crucial step as that will decide the type of central tendency you want to decide for the dataset. There can be multiple reason for an outliers in the dataset, one potential reason can be incorrect data accumulation. handling outlier is a tricky process but to visualize the data with outlier we can use box plot.
```{r}

library(ggExtra)
data(mpg, package="ggplot2")

theme_set(theme_bw())  # pre-set the bw theme.
mpg_select <- mpg[mpg$hwy >= 35 & mpg$cty > 27, ]
g <- ggplot(mpg, aes(cty, hwy)) + 
  geom_count() + 
  geom_smooth(method="lm", se=F)
ggMarginal(g, type = "histogram", fill="transparent")
ggMarginal(g, type = "boxplot", fill="transparent")

```
<img
  src="/docs/assets/p3.png"
  style="display: inline-block; margin: 0 auto; max-width: auto">



