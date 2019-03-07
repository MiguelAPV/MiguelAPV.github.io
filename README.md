---
title: "Untitled"
author: "Miguel Porro"
date: "February 17, 2019"
output: html_document
---



```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
options(knitr.table.format = "html") 
```

Simple plotly example - BITCOIN  dataset
----
This is an R Markdown document. 
Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. 



Settings
----
We are going to plot the Bitcoin time Series from 02-26-2019
```{r, eval=FALSE}
library(plotly)
```
```{r, echo=FALSE}
library(plotly)
```
```{r, echo=FALSE}
library(anytime)
```


Settings (cont.)
----
```{r, echo=TRUE}
BTC <- read.csv("C:/Users/migue/Desktop/DATA Cleaned TESIS/BTC_data1hora26-02.csv", header = TRUE, colClasses = "character")
BTC$Close <- as.numeric(gsub(',', '', BTC$Close))
BTC$Open.time <- as.numeric(BTC$Open.time)
BTC$Open.time <- BTC$Open.time/1000
BTC$Open.time <- anytime(BTC$Open.time)
summary(BTC)
```

```{r , eval=FALSE}
plot_ly(BTC, x = ~Open.time , y = ~Close, type = "scatter", mode = "lines")
```


Plotting
----
```{r , echo=FALSE}
plot_ly(BTC, x = ~Open.time , y = ~Close, type = "scatter", mode = "lines")
```

Interpretation
----
Simply put: 

- This is the Bitcoin time series from the last 14 days before 02-26-2019, It can be used to make really good predictions using time series regression models.
