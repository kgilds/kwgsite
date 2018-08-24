---
title: working directory
author: Kevin
date: '2017-11-04'
slug: working-directory
categories:
  - R
  - computer literacy
  - R-studio community
tags:
  - R
description: ''
featured: ''
featuredalt: '' 
featuredpath: ''
linktitle: ''
---

This seems basic in retrospect but one of the biggest challenges starting with R was understanding the concept of the working directory. For the most part, I figured the working directory out. However a bad habit that festered was changing the working directory in the chunks of my Rmd files. 

Below is how I would configure my R chunks to read data or source scripts/functions. 
My data sits in multiple folders in the Project Folder, and I could not get the chunk to read the data or source scripts without setting the working directly.



```R
setwd(~getRealMY2017208/raw_data)

readRD("student_10222017.rds")

```



This fall I read some posts in [R-Studio Community](https://community.rstudio.com/t/best-practices-for-organizing-rmarkdown-projects/914) on workflow in R and I wanted to incorporate these techniques. However, I needed to figure this working directory issue out.  

I reviewed Github, researched the topic on Stack Overflow, and thought about asking on R-Studio Community. However, I was not sure I could even formulate the problem. 



### Solution

It was not really the working directory after all. I needed to more explict in my file address. 

* I set my Global Options/R Markdown setting to Evaluate Chunks in Project.  

```r
readRDS("raw_data/student_10222017.rds")

```

Ultimately, to make the analysis more reproducible; there should be code to set that the working directory is the project directy.


```{r "setup", include=FALSE}
require("knitr")
opts_knit$set(root.dir = "~/gits/project/")
```


