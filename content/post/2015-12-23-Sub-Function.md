---
layout: post
title: Sub-function
excerpt: data management fun using the sub-function
tags: [R, Sub-Function, Data Management]
modified: 2016-02-28
comments: true
---



### Function of the week

Data management or data cleaning one of the most under appreciated task when it comes to completing a data analysis.

General users break data patterns all the time and enter data that is not quite correct. One function that can help you fix data without changing the original data source is the "sub function"

Here is an example of how I used the sub function. I needed to remove + from grade data entry. Here is the code I used to adjust the grade.  

``` r
mq1Reading$readingGrade <-sub("B+", "B", fixed=TRUE, mq1Reading$readingGrade)
```

I have used this function before but did not have to utilize the fixed=TRUE argument because I was adjusting a white space issue.

The fixed true argument spells out that we are not looking for regular expressions but regular text.

Here is the web page that helped me http://rfunction.com/archives/2354
