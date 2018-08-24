---
title: Learning Functions
author: kevin
date: '2018-05-08'
slug: learning-functions
categories:
  - R
  - functions
  - dplyr
tags: []
description: ''
featured: ''
featuredalt: ''
featuredpath: ''
linktitle: ''
---

My latest foray into writing functions led me to a new learning opportunity. 

My first  try at this function did not work as expected. The first part of the function worked but the second argument did not take with the mutate statement. The output provided me with a table but did not take my second argument for source. 


```{r}
base_count <- function(df, source){
	mutate(df,"Source"  = "source") %>%
	count(Source)

	
}
```

To Stack Overflow I go, and this [post](https://stackoverflow.com/questions/28973056/in-r-pass-column-name-as-argument-and-use-it-in-function-with-dplyrmutate-a
) helped me out. 



```{r}
base_count <- function(df, source){
	mutate_(df,"Source"  = "source") %>%
	count(Source)

	
}

student_post_count <- base_count(postUnique, "Student Post")
```

This works! But it seems odd to have to quote the arugment in order for the function to work.  

I looked up `r mutate_` in the help page and the page informs that this verb is now superfluous  because dplyr utilizes tidy evaluation semantics. 

>"NSE verbs still capture their arguments but you can now unquote parts of these arguments."


This is hazy to me, and I am not clear why this function works. The help page directs to dplyr's [vignette on programming for more information](https://cran.r-project.org/web/packages/dplyr/vignettes/programming.html)

Wow!  A whole new world of understanding of how R and dplyr works. 





```{r}
base_count_f <- function(df, source){
	source <- enquo(source)
	mutate(df, "Source" = "source") %>%
		count(Source)
}

base_count_f(postUnique, Student_Post)
```


