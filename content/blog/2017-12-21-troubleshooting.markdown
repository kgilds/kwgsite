---
title: Framework for Troubleshooting
author: Kevin
date: '2018-01-13'
slug: troubleshooting
categories:
  - R
tags:
  - Str
  - likert
  - Rds
---

I transitioned from using databases to the RDS format to store evolving data. I  ran into some trouble with the RDS format. I was stumped when previous working code would not work on a new data set. 


My troubleshooting framework is as follows: 

1) Look for silly typos. 

2) Check your data types.

3) Isolate the issue.

The [str function](https://www.rdocumentation.org/packages/utils/versions/3.4.3/topics/str) is the MVP of this troubleshooting adventure with a a little help from isolating the issue. The str function helped me identify that my data object was carrying baggage from the previous data frame. My dplyr select statement selected 6 variables of interest from the original data frame with 23 variables. 

*The str output*

#  $ sheHasSelfConfidence      : chr  "Neither Agree/Disagree" "Agree" "Strongly Agree" "Strongly Agree" ...
##  $ goodAttitudeAboutSchool   : chr  "Slightly Disagree" "Agree" "Strongly Agree" "Strongly Agree" ...
##  $ readsBooksForFun          : chr  "Disagree" "Neither Agree/Disagree" "Agree" "Strongly Agree" ...
##  $ positiveRelationships     : chr  "Slightly Agree" "Slightly Agree" "Strongly Agree" "Strongly Agree" ...
##  $ homeworkWithoutSupervision: chr  "Disagree" "Neither Agree/Disagree" "Strongly Agree" "Strongly Agree" ...
##  - attr(*, "spec")=List of 2
##   ..$ cols   :List of 23
##   .. ..$ ResponseID                                                                                                  : list()
##   .. .. ..- attr(*, "class")= chr  "collector_character" "collector"
##   .. ..$ ResponseSet                                                                                                 : list()


**$ cols : List of 23** is the key to knowing something was wrong.


Here is the str output when it is correct:


'data.frame': 195 obs. of 6 variables:
$ graduate : Factor w/ 5 levels "Agree","Neither Agree/Disagree",..: 4 5 5 5 5 2 5 5 5 5 ...
$ sheHasSelfConfidence : Factor w/ 6 levels "Agree","Disagree",..: 3 1 6 6 6 5 6 1 6 6 ...
$ goodAttitudeAboutSchool : Factor w/ 6 levels "Agree","Disagree",..: 5 1 6 6 6 2 6 6 6 6 ...
$ readsBooksForFun : Factor w/ 7 levels "Agree","Disagree",..: 2 3 1 6 6 2 1 6 4 3 ...
$ positiveRelationships : Factor w/ 7 levels "Agree","Disagree",..: 4 4 6 6 6 4 6 4 4 1 ...
$ homeworkWithoutSupervision: Factor w/ 7 levels "Agree","Disagree",..: 2 3 6 6 6 2 6 6 6 6 ...




After researching on Google, I came across this [issue](
httpd://github.com/tidyverse/dplyr/issues/3028). However, I don't think I was encountering this bug. I isolated the issue by running the same dplyr package on the old data set and the select statement worked just fine. The only difference, I noted is that the previous data was not in a Rds format. 

Here is the screenshot my Trello comments as I reasoned through this

![trello](/img/trello2.png)




Ultimately, I had to change the format I was holding the data in to a csv file type.







