--- 
title: "rCharts Viz with R"
author: "Solomon Christy AB"
highlighter: highlight.js
output:
  html_document: default
  pdf_document:
    keep_tex: yes
job: Business Analytics Student, Praxis Business School, Bengaluru
knit: slidify::knit2slides
mode: selfcontained
hitheme: tomorrow
subtitle: Explore the power of rCharts
framework: io2012
widgets:
- mathjax
- bootstrap
- quiz
--- 

## Introduction


Bored of using the conventional "ggplot2" package for visualizing your data? Looking for an
interactive dynamic visualization which will enhance the elegance of your work? 
Then, "rCharts" is the best solution by far. Bet you would not have seen such a visualization in R.


> "rCharts" is an R package to create, customize and publish interactive javascript visualizations from R.


> With rCharts, you can make use of boxplot, scatterplot, barplot (discrete/multi), area chart, pie chart/donut chart, line chart, line dotted. 




To begin with, I shall provide an example of code here to exhibit how simple and convenient it is, to work with "rCharts".

(I've chosen to work with MultiBar Chart as the provided example demands it)


--- 

## Prerequisites

### 1. Install "rCharts" library


```r
install.packages("devtools")
install.packages("Rcpp")
library(devtools)
library(Rcpp)
# Ramnath Vaidhynathan is the R Contributor, currently working in MCGill University, San Francisco 
# as Associate Professor developed this RCharts and Slidify Libraries
install_github('ramnathv/rCharts') 
```

---

## Prerequisites

### 2. Install "slidify" library


```r
# Slidify is also developed by Ramnath V who developed the "rCharts".
# To include rCharts graphs in markdown, you require Slidify. 

# Slidify is basically an amalgamation of existing features present in
# R Markdown and elements you need to incorporate rCharts in your presentation.

# With Slidify, you can create stunning presentation with markdown basics.

# Visit www.slidify.org to know the procedures to install Slidify in your R Studio

library(devtools) # install this lib if you have not done yet
install_github('slidify','ramnathv')
install_github('slidifyLibraries','ramnathv')
```

---

## Code


```r
#Filling BLANKS with "NA"
mydata = read.csv("D:/bigmart.csv", na.strings = "")
#Removing rows with "NA" in any field
final<-mydata[complete.cases(mydata),]
```




```r
#Counting Total items for each Item Type
fat <- as.data.frame(table(final$Item_Type, final$Item_Fat_Content))
names(fat) <- c("Item_Type","Fat_Content","Number")
```

---

## Code (cont.)


```r
library(rCharts)
# Below lib is required only when you render the rCharts graph in Slidify
library(knitr)
p2a <- nPlot(Number ~ Item_Type, 
             data = fat, group = 'Fat_Content',
             type = 'multiBarChart')

p2a$set(dom = 'chart2', width = 1300)
```


```r
# Call Object 'p2a' to render the barchart
p2a
```

---

## Rendered rCharts BarPlot

### Item_Type Vs Number_Of_Items
<iframe src=' assets/fig/unnamed-chunk-8-1.html ' scrolling='no' frameBorder='0' seamless class='rChart nvd3 ' id=iframe- charte8877b54cf6 ></iframe> <style>iframe.rChart{ width: 100%; height: 400px;}</style>

