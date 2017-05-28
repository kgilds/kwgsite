---
layout: post
title: R Milestones
excerpt: Met some Milestones in R
tags: [Functions, Looping]
modified: 2016-03-25
comments: true
---

Proud to have finally met some basic programming milestones in R. A couple of months ago, I was finally able to write a function.

For the longest time, I wanted to be able to loop over a column and place the grade point in a new column. I finally accomplished this task. Here is the basic code.

```r
lang_pts <- numeric(0)

for(i in mq1_lang$langGrade){

     lang_pts<- c(lang_pts,switch(i, "A" =4, "B"=3, "C"=2, "D"=1, "F"=0, "I"=0))

     lang_pts


}

mq1_lang <- cbind(mq1_lang, lang_pts)
```
