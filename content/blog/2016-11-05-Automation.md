---
layout: "post"
title: "hacked automation"
author: "Kevin Gilds, MPA"

output: github_document
---




rmarkdown::render("file.name")

The line of code above has dramatically improved my workflow. The render function helped me reach the goal of creating an automated system of creating a status report and share data in a more efficient manner.

Ultimately, I still want to use the makefile feature but this process has helped identify the structure.

Here is a snippet of how the automation works

**Created an Rmd file that does the following**

-   reads the csv survey data files
-   creates an RDS file in the directory
-   renders the data management scripts

**The data management scripts run and do the following**

-   the data management scripts send data to a sqlite database
-   sends data to dropbox folder.
-   creates a status report on valid data entry and duplicate entries.
