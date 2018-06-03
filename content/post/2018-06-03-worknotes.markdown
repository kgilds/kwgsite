---
title: Worknotes
author: Kevin
date: '2018-06-03'
categories:
  - r
  - worknotes
tags:
  - bookdown
  - Forcats
  - functions
slug: worknotes
---

One new approach is to post worknotes. My hope is that the work notes help generate better content for future articles and projects.  

Yesterday 06/02/2018 downloaded updated data and ran all. Think I got teacher and parent survey where I want. Strategy will be put the table as they are now but collapse some of the levels so that graph can be a bit cleaner or focused; currently I would have to run the width wider and the output to word is sub-optimal. There is a function "fct_recode" in Forcats that will do this. 

> worktime: 100 minutes

06/03/2018: Worked in the bookdown framework but really I was setting up functions for the analysis. It was just side benefit that it was also rendering the bookdown format.

Received this error 

> Error in rmarkdown::render_site("/home/jdb-work/index.Rmd", encoding = "",  : 
  unused argument (knit_root_dir = "~")
Execution halted

I corrected the problem by setting the Set the Knit Directory to Document Directory. Here is github issue that helped me resolve the issue.  https://github.com/rstudio/rstudio/issues/2158. Not sure if this is the same problem but used the solution to solve the problem. 
Next iteration may be to use the functions developed today and update package so that you may use for other life skills?  Write and utilize the package in iterations. 

A couple of thoughts; post work notes on webpage; do I put it as a post or separate page. tagging the page would be fun. I think I will post it. 

> worktime:  180 minutes 
