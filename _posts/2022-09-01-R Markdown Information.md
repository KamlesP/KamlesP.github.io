---
title:          "Information about the tidyverse"
author:         "Kamlesh Pandey"
output:         
  html_document:
    code_folding: show
    toc: true
    toc_float: true
    toc_depth: 3
    theme: readable
    df_print: paged
    highlight: default
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
# R package for data science
The tidyverse is an opinionated collection of R packages designed for data science. All packages share an underlying design philosophy, grammar, and data structures.

Install the complete tidyverse with:
```{r, eval=FALSE, warning=FALSE, message=FALSE, echo=TRUE}
install.packages("tidyverse")
```
# Some Core Packages {.tabset .tabset-fade .tabset-pills}
The four _core_ packages that we’ll use the most are given below along with their purpose and a quick example of some functionality.

##     dplyr
``` {r , echo = FALSE, fig.align = 'center', out.width='25%'}
knitr::include_graphics("dplyr.png")
```
[dplyr is a grammar of data manipulation](https://dplyr.tidyverse.org), providing a consistent set of verbs that help you solve the most common data manipulation challenges:

* mutate() adds new variables that are functions of existing variables.
* select() picks variables based in their names.
* filter() picks cases based on their values.
* summarise() reduces multiple values down to a single summary.
* arrange() changes the ordering of the rows.

These all combine naturally with group_by() which allows you to perform any operation "by group". You can learn more about them in vignette("dplyr"). As well as these single-table verbs, dplyr also provides a variety of two-table verbs, which you can learn about in vignette("two-table").

If you are new to dplyr, the best place to start is the data transformation chapter in R for the data science.

```{r, eval=TRUE, warning=FALSE, message=FALSE}
library(dplyr)

starwars %>%
    filter(species == "Droid")
```

##     ggplot2
``` {r , echo = FALSE, fig.align = 'center', out.width='25%'}
knitr::include_graphics("ggplot2.png")
```
[ggplot2 is a system for declaratively creating graphics, based on the Grammar of Graphics. ](https://ggplot2.tidyverse.org) You provide the data, tell ggplot2 how to map variables to aesthetics, what graphical primitives to use, and it takes care of the details.


```{r eval=TRUE, message=FALSE, warning=FALSE}
library(ggplot2)

ggplot(mpg, aes(displ, hwy, color = class)) + 
  geom_point()
```

##     readr
``` {r img-with-knitr, echo = FALSE, fig.align = 'center', out.width='25%'}
knitr::include_graphics("readr.png")
```
[The goal of readr](https://readr.tidyverse.org) is to provide a fast and friendly way to read rectangular data (like csv, tsv, and fwf). It is designed to flexibly parse many types of data found in the wild, while still cleanly failing when data unexpectedly changes. If you are new to readr, the best place to start is the data import chapter in R for data science.

##     tidyr
``` {r , echo = FALSE, fig.align = 'center', out.width='25%'}
knitr::include_graphics("tidyr.png")
```
[The goal of tidyr](https://tidyr.tidyverse.org) is to help you create tidy data. Tidy data is where:

1. Every column is variable.
2. Every row is an observation.
3. Every cell is a single value.

Tidy data describes a standard way of storing data that is used wherever possible throughout the tidyverse. If you ensure that your data is tidy, you’ll spend less time fighting with the tools and more time working on your analysis. Learn more about tidy data in vignette("tidy-data").
```{r, eval=TRUE, warning=FALSE, message=FALSE}
library(tidyr)

relig_income
```

```{r, eval=TRUE}
relig_income %>%
    pivot_longer(-religion, names_to="income", values_to='frequency')
```
