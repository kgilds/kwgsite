---
title: list.files
author: Kevin
date: '2018-01-27'
slug: list-files
categories:
  - R
tags: [list.files]
---

I learned how to use the list.file function from [Dean Attali's Post: Mimicking a Google Form with a Shiny App](https://deanattali.com/2015/06/14/mimicking-google-form-shiny/)

However the power of the list.file function finally set this in this week. The function is not merely a method to list the files--it can be a method to put all those files to an object that can be manipulated--mind blown. 😄 

Here is my script to combine multiple pdf files using the [tabulizer package](https://github.com/ropensci/tabulizer). I was generally surprised how easy it was the use list.file function to store all the pdf files to an object and then use the merge_pdf file.  



```r
library(tabulizer)

files <- list.files("~/student")



merge_pdfs(files, "Merged.pdf")
```

