---
title: Freeing Educational Data With A Shiny App
author: Kevin
date: '2018-04-04'
slug: freeing-educational-data-with-a-shiny-app
categories: [R, Shiny]
tags:
  - Shiny
description: ''
featured: ''
featuredalt: ''
featuredpath: ''
linktitle: ''
toc: yes
---

I built a [Shiny Application](https://tidydatabykwg57.shinyapps.io/flabsences/) to free data from a spreadsheet on the [Florida Department of Education website](http://www.fldoe.org/accountability/data-sys/edu-info-accountability-services/pk-12-public-school-data-pubs-reports/students.stml). I learned a lot--specifically making the input variable reactive, sprinkling in html to make it look how I want, and using the DT package for useful rendering of the data.  

## Reactive 

I knew that I wanted to split the data into school types--elementary, middle, and high and had a sense that my input value would need to be reactive. For instance, I was concerned I would have to make a new input call every time a user switched school types.  

Here is an article on [Reactivity](https://shiny.rstudio.com/articles/reactivity-overview.html)

Making the input variable reactive was easy.

```r
 ## Make School District Reactive
  dataInput <- reactive ({
    dplyr::filter(absences_2, district_name == input$school_district)


### us the reactive expression

output$all <- renderTable({
       
       
      all<- dataInput()
      
      
      )
      
      
   })

    
})
```


## About Page

It was difficult to proofread the content of the About page along with the html tags. 
The next time I produce an About page, I am going to reference in a md file. 

This is a useful [Shiny Example](https://shiny.rstudio.com/gallery/including-html-text-and-markdown-files.html) of referencing in a markdown file. 


```r
includeMarkdown("include.md")
```


## Output with  DataTable

I received feedback after initial release from the [R4DS Community](https://www.jessemaegan.com/post/r4ds-the-next-iteration/) to consider rendering the output with DataTable (DT)

A chief advantage to rendering the output with a DataTable is that is provides the user with more control over the data. Another advantage is being able to display the % symbol in the output is easy with the DT package.

```r
formatPercentage('percent', 2)
```

I wanted to keep the percent column in descending order and my previous dplyr statement no longer applied. 

This is where I learned to use the options that are available with DT. This is a line of code that utilizes options to order the percent column in descending order. 



```r
elem <- DT::datatable(elem, rownames = FALSE, options= list(order =list(4, "desc"))) %>%
```


Notice that the 4 is the index or column number that is being ordered. The rownames argument gave me a bit of trouble as the rowname impacts the index in the options section. 

On the surface it appeared--the column I wanted order would be 5 and initially I thought the index would be 6. I finally deduced the solution and reduced the index to 4 and obtained the expected output.

Here is the documentation for [DT Options](https://rstudio.github.io/DT/options.html) and dealing with rownames can be found here [DT Rownames](https://rstudio.github.io/DT/)


## Next Steps

My next step is to place the district averages to a map of Florida. My hunch is that school districts in rural areas have the highest percent of students with 21 days or more of absences. 