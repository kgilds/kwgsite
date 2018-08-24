---
title: milestones
author: Kevin
date: '2018-06-10'
slug: milestones
categories:
  - worknotes
  - R
tags:
  - Forcats
  - ggplot2
---

This morning I successfully employed the Forcats package and re_code function to change factor levels for easier plotting and implemented the scales function to display the percent sign.


I like seven point likert scales but I don't like the output of seven point scales on graphs or tables--especially with a scale like Strongly Disagree through Strongly Agree. 




```r
p_relationship <- parent %>%
	group_by(Time) %>% #Pre and Post variable
	mutate(positive_relationships = fct_recode(positive_relationships, #recode the levels to make it easier to plot and table display)
		"Strong Disagreement" = "Strongly Disagree", 
		"Strong Disagreement" = "Disagree",
		"Slight Disagreement" = "Slightly Disagree",
		"Neutral" = "Neither Agree/Disagree",
		"Slight Agreement" = "Slightly Agree",
		"Strong Agreement" = "Agree",
		"Strong Agreement" = "Strongly Agree"))
```


This is going to be a pain for the whole report but not too bad for each sub-section. This may be a good opportunity to to learn purr.


I finally implemented the scales function to add percent sign. I feel more comfortable working on the hood with ggplot2 and finally added  a single line to ggplot2 script and worked like a charm.


```r
improved_relationship_plot <- ggplot(pi_relationships, aes(x = helped_relationships, y = ..prop.., group = 1 )) +
	geom_bar() +
	scale_y_continuous(labels = scales:: percent) 
	
improved_relationship_plot
```


> good week of work: 555 minutes  
