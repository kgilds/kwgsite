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

This seems basic in retrospect but one of the biggest challenges starting with R was understanding the concept of the working directory. A bad habit that festered was changing the working directory in the chunks of my Rmd files. I could not figure it how to make R read the data and I simply ignored the warnings. 

This fall I read some posts in [R-Studio Community](https://community.rstudio.com/t/best-practices-for-organizing-rmarkdown-projects/914) on workflow in R and I wanted to incorporate these techniques. However, I needed to figure this working directory out.  I reviewed Github, researched the topic on Stack Overflow, and thought about asking on R-Studio Community. However, I was not sure I could even formulate the problem. 

My data sits in multiple folders in the Project Folder and I could not get to read the data or source scripts. 

This is what I was trying with no success. 


```r

setwd(~getRealMY2017208/raw_data)

readRD("student_10222017.rds")
```

Finally, I figured it out and it was simple as being more explicit in the file address. 




I set my Global Options/R Markdown setting to Evaluate Chunks in Project.  

```r
readRDS("raw_data/student_10222017.rds")

```

Ultimately, to make the analysis more reproducible; there should be  code to set that the working directory is the project. 


