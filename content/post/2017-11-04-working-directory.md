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

One of the biggest challenges starting with R was understanding the concept of the working directory. This seems crazy in retrospect. However, a bad habit that festered was changing the working directory in the chunks of my Rmd files. I could not figure it how to make R read the data and I simply  ignored the warnings. 

This fall I read some posts in R-Studio Community on workflow in R and I wanted to incorproate these techniques. However, I needed to figure this working directory out.  I reviewed Github, researched the topioc on Stack Overflow, and thought about asking on R-Studio Community. However, I was not sure I couldd even formulate the problem. 

My data sits in multiple folders in the Project Folder

I set my Global Options/R Markdown setting to Evaluate Chunks in Project.  

Finally, I figured it out and it was simple as being more explicit in the file address. I was

I

```r
student_10222017
```


