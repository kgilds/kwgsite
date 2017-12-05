---
title: A bit of a hack
author: Kevin
date: '2017-12-02'
slug: a-bit-of-a-hack
categories:
  - R
  - gsub
tags: []
description: ''
featured: ''
featuredalt: ''
featuredpath: ''
linktitle: ''
---

This week I also finished up a feature of an application that I have been thinking about implementing. I wanted to summarize data entry by site location. The problem is that variable I am trying to summarize is free data entry--hence many ways to write the name of the school and misspelling. I used a bit of hack with the gsub function.  


My approach was this. 

```r
site$school <- toupper(site$school)


site$school <- gsub("DOWDELL MIDDLE", "DOWDELL", fixed=TRUE, site$school)
site$school <- gsub("DOWDELL MAGNET", "DOWDELL", fixed=TRUE, site$school)
site$school <- gsub("DOWDELL SCHOOL", "DOWDELL", fixed=TRUE, site$school)
site$school <- gsub("DOWDELLMIDDLE", "DOWDELL", fixed=TRUE, site$school)
site$school <- gsub("DOWDELL  MIDDLE", "DOWDELL", fixed=TRUE, site$school)
site$school <- gsub("BLAKE ACADMY", "BLAKE ACADEMY", fixed=TRUE, site$school)
site$school <- gsub("BLAKEACADMY", "BLAKE ACADEMY", fixed=TRUE, site$school)
site$school <- gsub("BLAKE ACAMAY", "BLAKE ACADEMY", fixed=TRUE, site$school)
site$school <- gsub("DREAM ACADENY", "DREAM ACADEMY", fixed=TRUE, site$school)
site$school <- gsub("FREEDOM MS", "FREEDOM MIDDLE SCHOOL", fixed=TRUE, site$school)
site$school <- gsub("RIBUALT MDDLE", "RIBAULT MIDDLE", fixed=TRUE, site$school)
```

However, my sense is that there is a better way implement this with regular expressions. I need to find examples in the wild and my firs stop is [here](http://tidytextmining.com/)




