---
title: geom_point
author: kevin
date: '2018-06-24'
slug: geom-point
categories:
  - r
tags:
  - forcats
  - ggplot
---


I have recently discovered the magic of geom_point coupled with fct_reorder. I am not sure how I got along with out it.

Here is an example, I used yesterday. 



```r
metallica %>%
  select(2,6,23) %>%
  ggplot(aes(album_popularity, fct_reorder(album_name, album_popularity))) +
  geom_point() +
  geom_vline(xintercept = 50.94, col='red')
```


