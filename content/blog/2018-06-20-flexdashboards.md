---
title: Flexdashboards
author: 'Kevin '
date: '2018-06-20'
slug: flexdashboards
categories:
  - r
  - worknotes
  - getREAL!
tags: []
description: 'Rediscovering Flexdashboard'
featured: ''
featuredalt: ''
featuredpath: ''
linktitle: 'Fun with Flexdashboards'
---

Working with Flexdashboards is great-I had forgotten how much fun they are to work with. The other day I was reviewing some my prior applications, and  wanted to reuse Flexboard I built last year. 

I brought the file into the new directory and after an overhaul of previous code, I kept running into a strange error.  The error message conveyed that the data file was not in the directory. I could see the file in the directory and could successfully run the code chunk. 


I finally just stared creating a new flexboard when the solution dawned on me. This dashboard in the yaml had runtime shiny in it. I deleted the runtime shiny prompt and made the adjustment in the Knit option for the working directory. Sure enough R was not looking in the right directory for the file. I made the adjustment and it worked like a charm.

> work time 100 minutes