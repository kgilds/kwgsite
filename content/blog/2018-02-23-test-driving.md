# Test Driving readxl
Kevin  
2018-02-23  

# Introduction

I am interested in school attendance data and found an interesting data set on the Florida Department of Education Website. This seemed like a good time to learn the ` r readxl package ` in order to wrangle spreadsheets in the wild. This post closely follows closely with theexamples on the [Github Repo](https://github.com/tidyverse/readxl). 

The file consists of data from a survey of schools in Florida that provides a count of students who were absent more than 21 days in the school year 2015-2016. 


```r
library(tidyverse)
```

```
## Loading tidyverse: ggplot2
## Loading tidyverse: tibble
## Loading tidyverse: tidyr
## Loading tidyverse: readr
## Loading tidyverse: purrr
## Loading tidyverse: dplyr
```

```
## Conflicts with tidy packages ----------------------------------------------
```

```
## filter(): dplyr, stats
## lag():    dplyr, stats
```

```r
library(readxl)
library(httr)
library(knitr)
```

### Getting the data

The url of the data set is below

```r
url <- 'http://www.fldoe.org/core/fileparse.php/7584/urlt/1516ABS21DAYSchool.xls'
```

Use the Get function from httr to grab the file

```r
GET(url, write_disk(absences <- tempfile(fileext = ".xls")))
```

```
## Response [http://www.fldoe.org/core/fileparse.php/7584/urlt/1516ABS21DAYSchool.xls]
##   Date: 2018-02-25 18:18
##   Status: 200
##   Content-Type: application/msexcel
##   Size: 751 kB
## <ON DISK>  /tmp/RtmpWPsNyb/file3d9535e795b5.xls
```



### Read the data

```r
absences_1 <- read_excel(absences)
```

### Check the data out with the str function

```r
str(absences_1)
```

```
## Classes 'tbl_df', 'tbl' and 'data.frame':	4039 obs. of  7 variables:
##  $ Students Absent 21 or More Days by School
## 2015-16, Final Survey 5: chr  "*To provide meaningful results and to protect the privacy of individual students, data are displayed only when "| __truncated__ "District #" "1" "1" ...
##  $ X__1                                                              : chr  NA "District Name" "ALACHUA" "ALACHUA" ...
##  $ X__2                                                              : chr  NA "School #" "22" "31" ...
##  $ X__3                                                              : chr  NA "School Name" "EARLY LEARNING ACADEMY AT DUVAL" "J. J. FINLEY ELEMENTARY SCHOOL" ...
##  $ X__4                                                              : chr  NA "Enrollments" "456" "721" ...
##  $ X__5                                                              : chr  NA "Absent 21 Days or Over" "127" "38" ...
##  $ X__6                                                              : chr  NA "% Absent 21 or More Days" "0.278509" "0.0527046" ...
```


### Display the data

```r
absences_1
```

```
## # A tibble: 4,039 x 7
##           `Students Absent 21 or More Days by School\n2015-16, Final Survey 5`
##                                                                          <chr>
##  1 *To provide meaningful results and to protect the privacy of individual stu
##  2                                                                  District #
##  3                                                                           1
##  4                                                                           1
##  5                                                                           1
##  6                                                                           1
##  7                                                                           1
##  8                                                                           1
##  9                                                                           1
## 10                                                                           1
## # ... with 4,029 more rows, and 6 more variables: X__1 <chr>, X__2 <chr>,
## #   X__3 <chr>, X__4 <chr>, X__5 <chr>, X__6 <chr>
```

The output is not in a tidy format. The first row has a title and the second row provides a description of the data. Lets extract just the meta data using ` r (n_max = 2)`.  


```r
meta <- read_excel(absences, n_max = 2)

meta
```

```
## # A tibble: 2 x 7
##          `Students Absent 21 or More Days by School\n2015-16, Final Survey 5`
##                                                                         <chr>
## 1 *To provide meaningful results and to protect the privacy of individual stu
## 2                                                                  District #
## # ... with 6 more variables: X__1 <chr>, X__2 <chr>, X__3 <chr>,
## #   X__4 <chr>, X__5 <chr>, X__6 <chr>
```

This is not exactly what I want. Using ` r (n_max = 2)` we captured the title and message about the data but we also captured the other columns and row information.  I am going to use the range argument to isolate the title and description of the data. 


```r
meta_1 <- read_excel(absences, range="A1:A2")

meta_1
```

```
## # A tibble: 1 x 1
##          `Students Absent 21 or More Days by School\n2015-16, Final Survey 5`
##                                                                         <chr>
## 1 *To provide meaningful results and to protect the privacy of individual stu
```

An important warning about the data is cut off in the blog down output. I am going to isolate on the cell to clearly display the message about the data. 


```r
meta_2 <- read_excel(absences, range="A2")

meta_2
```

```
## # A tibble: 0 x 1
## # ... with 1 variables: *To provide meaningful results and to protect the
## #   privacy of individual students, data are displayed only when the total
## #   number of students in a group is at least 10 and when the performance
## #   of individuals would not be disclosed. Data for groups less than 10
## #   are displayed with an asterisk (*). <lgl>
```

This did the trick. The message indicates that an asterisk is used when there is less than 10 students at a school. There is a ` r (na)` argument in the read_excel function but I could not get it work with a plain asterisk or an asterisk in quotes. Maybe a regular expression would work. 


```r
absences_2 <- read_excel(absences, skip =2, na = "*")

absences_2 <- read_excel(absences, skip =2, na = *)
```


### Let me introduce you to skip:

Now, that we have the title and message about the data, let us put the data in tidy format. From our exercise above we know that the first two rows are not helpful. Fortunately we can use the ` r (skip = 2)` argument to bypass the first 2 rows. 


```r
absences_2 <- read_excel(absences, skip = 2)
```

### Use str again to check what we are dealing with

```r
str(absences_2)
```

```
## Classes 'tbl_df', 'tbl' and 'data.frame':	4037 obs. of  7 variables:
##  $ District #              : num  1 1 1 1 1 1 1 1 1 1 ...
##  $ District Name           : chr  "ALACHUA" "ALACHUA" "ALACHUA" "ALACHUA" ...
##  $ School #                : num  22 31 41 52 71 81 82 91 101 111 ...
##  $ School Name             : chr  "EARLY LEARNING ACADEMY AT DUVAL" "J. J. FINLEY ELEMENTARY SCHOOL" "STEPHEN FOSTER ELEMENTARY SCHOOL" "A.QUINN JONES CENTER" ...
##  $ Enrollments             : chr  "456" "721" "593" "173" ...
##  $ Absent 21 Days or Over  : chr  "127" "38" "34" "90" ...
##  $ % Absent 21 or More Days: chr  "0.278509" "0.0527046" "0.0573356" "0.520231" ...
```

Lovely, we are going to have to convert some of these variables to numeric. 


```r
absences_2$Enrollments <- as.numeric(absences_2$Enrollments)
```

```
## Warning: NAs introduced by coercion
```

```r
absences_2$`Absent 21 Days or Over` <- as.numeric(absences_2$`Absent 21 Days or Over`)
```

```
## Warning: NAs introduced by coercion
```

```r
absences_2$`% Absent 21 or More Days` <- as.numeric(absences_2$`% Absent 21 or More Days`)
```

```
## Warning: NAs introduced by coercion
```


```r
str(absences_2)
```

```
## Classes 'tbl_df', 'tbl' and 'data.frame':	4037 obs. of  7 variables:
##  $ District #              : num  1 1 1 1 1 1 1 1 1 1 ...
##  $ District Name           : chr  "ALACHUA" "ALACHUA" "ALACHUA" "ALACHUA" ...
##  $ School #                : num  22 31 41 52 71 81 82 91 101 111 ...
##  $ School Name             : chr  "EARLY LEARNING ACADEMY AT DUVAL" "J. J. FINLEY ELEMENTARY SCHOOL" "STEPHEN FOSTER ELEMENTARY SCHOOL" "A.QUINN JONES CENTER" ...
##  $ Enrollments             : num  456 721 593 173 629 198 25 791 345 647 ...
##  $ Absent 21 Days or Over  : num  127 38 34 90 106 63 0 71 29 67 ...
##  $ % Absent 21 or More Days: num  0.2785 0.0527 0.0573 0.5202 0.1685 ...
```

In part II, we will dive into the data. Stay tuned. 

