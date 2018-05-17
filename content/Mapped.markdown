---
title: Maps

---


Hello


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


# Intro

My issue list includes a task to map the Fl Absences data set.




```
## Response [http://www.fldoe.org/core/fileparse.php/7584/urlt/1516ABS21DAYSchool.xls]
##   Date: 2018-05-14 01:51
##   Status: 200
##   Content-Type: application/msexcel
##   Size: 751 kB
## <ON DISK>  /tmp/RtmpHOT2Td/file3dd05a3b2e1.xls
```

## Read the data


## Clean and Convert the data

```
## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion
```

## Make my own percents


## Summary Stats for plotting

```
## # A tibble: 74 x 2
##    district_name  mean
##            <chr> <dbl>
##  1       ALACHUA 14.29
##  2         BAKER 19.64
##  3           BAY 15.28
##  4      BRADFORD 17.70
##  5       BREVARD  6.50
##  6       BROWARD  9.82
##  7       CALHOUN 17.78
##  8     CHARLOTTE  8.41
##  9        CITRUS 10.38
## 10          CLAY  9.69
## # ... with 64 more rows
```

## Maps

### Get Florida Map from library ggmap

```r
states <- map_data("state")
```

```
## 
## Attaching package: 'maps'
```

```
## The following object is masked from 'package:purrr':
## 
##     map
```

```r
fl_df <- subset(states, region == "florida")
```


This chunks sets up how to overlay county boundaries over the Florida map. 


```r
counties <- map_data("county")
fl_county <- subset(counties, region == "florida")
```

This will us a map of Florida


```r
fl_base <- ggplot(data = fl_df, mapping = aes(x = long, y = lat, group = group)) + 
  coord_fixed(1.3) + 
  geom_polygon(color = "black", fill = "gray")
fl_base + theme_nothing()
```

```
## Warning: `panel.margin` is deprecated. Please use `panel.spacing` property
## instead
```

![plot of chunk fl_base](figure/fl_base-1.png)


```r
fl_base + theme_nothing() + 
  geom_polygon(data = fl_county, fill = NA, color = "white") +
  geom_polygon(color = "black", fill = NA)  # get the state border back on top
```

```
## Warning: `panel.margin` is deprecated. Please use `panel.spacing` property
## instead
```

![plot of chunk fl_base-fl-county](figure/fl_base-fl-county-1.png)


## Back to the educational set

School districts in Florida pretty much align with Florida Counties. However, there is nuance between the map data and the school district data. 

This chunk renames the district_name to match the name in the map data and matches the case. 


```r
absent_21_c <- absent_21 %>%
  rename("subregion" = "district_name") #match name with map data in preperation of joining. 

absent_21_c$subregion <- tolower(absent_21_c$subregion) #make lowercase

absent_21_c
```

```
## # A tibble: 74 x 2
##    subregion  mean
##        <chr> <dbl>
##  1   alachua 14.29
##  2     baker 19.64
##  3       bay 15.28
##  4  bradford 17.70
##  5   brevard  6.50
##  6   broward  9.82
##  7   calhoun 17.78
##  8 charlotte  8.41
##  9    citrus 10.38
## 10      clay  9.69
## # ... with 64 more rows
```

## Use the ani-join to determine issues with merging


```r
non_match <- anti_join(fl_county, absent_21_c, by = "subregion")

non_match
```

```
##          long      lat group order  region  subregion
## 1   -80.89018 25.79456   302 12629 florida miami-dade
## 2   -80.89018 25.97218   302 12630 florida miami-dade
## 3   -80.69538 25.96645   302 12631 florida miami-dade
## 4   -80.68965 25.94926   302 12632 florida miami-dade
## 5   -80.30003 25.94926   302 12633 florida miami-dade
## 6   -80.30003 25.96072   302 12634 florida miami-dade
## 7   -80.13387 25.96072   302 12635 florida miami-dade
## 8   -80.13961 25.90342   302 12636 florida miami-dade
## 9   -80.12814 25.85186   302 12637 florida miami-dade
## 10  -80.12814 25.81748   302 12638 florida miami-dade
## 11  -80.12814 25.79456   302 12639 florida miami-dade
## 12  -80.13387 25.78310   302 12640 florida miami-dade
## 13  -80.14534 25.77737   302 12641 florida miami-dade
## 14  -80.16252 25.78310   302 12642 florida miami-dade
## 15  -80.16825 25.80029   302 12643 florida miami-dade
## 16  -80.16825 25.82321   302 12644 florida miami-dade
## 17  -80.16252 25.85759   302 12645 florida miami-dade
## 18  -80.17398 25.85759   302 12646 florida miami-dade
## 19  -80.18545 25.85186   302 12647 florida miami-dade
## 20  -80.19691 25.83467   302 12648 florida miami-dade
## 21  -80.20263 25.78883   302 12649 florida miami-dade
## 22  -80.20836 25.75445   302 12650 florida miami-dade
## 23  -80.21982 25.73726   302 12651 florida miami-dade
## 24  -80.25420 25.72008   302 12652 florida miami-dade
## 25  -80.26566 25.69716   302 12653 florida miami-dade
## 26  -80.27712 25.63986   302 12654 florida miami-dade
## 27  -80.30003 25.62840   302 12655 florida miami-dade
## 28  -80.31149 25.61694   302 12656 florida miami-dade
## 29  -80.32296 25.59975   302 12657 florida miami-dade
## 30  -80.32296 25.56538   302 12658 florida miami-dade
## 31  -80.32296 25.54819   302 12659 florida miami-dade
## 32  -80.33441 25.52527   302 12660 florida miami-dade
## 33  -80.35160 25.49662   302 12661 florida miami-dade
## 34  -80.35733 25.46225   302 12662 florida miami-dade
## 35  -80.34587 25.42214   302 12663 florida miami-dade
## 36  -80.32868 25.39349   302 12664 florida miami-dade
## 37  -80.32868 25.37057   302 12665 florida miami-dade
## 38  -80.33441 25.35338   302 12666 florida miami-dade
## 39  -80.38598 25.33046   302 12667 florida miami-dade
## 40  -80.39171 25.30182   302 12668 florida miami-dade
## 41  -80.40317 25.29036   302 12669 florida miami-dade
## 42  -80.42609 25.27317   302 12670 florida miami-dade
## 43  -80.43755 25.23879   302 12671 florida miami-dade
## 44  -80.44328 25.22160   302 12672 florida miami-dade
## 45  -80.47192 25.23306   302 12673 florida miami-dade
## 46  -80.48911 25.22733   302 12674 florida miami-dade
## 47  -80.50057 25.20441   302 12675 florida miami-dade
## 48  -80.51776 25.20441   302 12676 florida miami-dade
## 49  -80.55787 25.23306   302 12677 florida miami-dade
## 50  -80.58651 25.23879   302 12678 florida miami-dade
## 51  -80.59798 25.23306   302 12679 florida miami-dade
## 52  -80.59225 25.20441   302 12680 florida miami-dade
## 53  -80.60944 25.19296   302 12681 florida miami-dade
## 54  -80.63235 25.19296   302 12682 florida miami-dade
## 55  -80.67818 25.18150   302 12683 florida miami-dade
## 56  -80.71256 25.15858   302 12684 florida miami-dade
## 57  -80.79278 25.15858   302 12685 florida miami-dade
## 58  -80.82716 25.17576   302 12686 florida miami-dade
## 59  -80.85007 25.18150   302 12687 florida miami-dade
## 60  -80.89591 25.18150   302 12688 florida miami-dade
## 61  -80.89018 25.79456   302 12689 florida miami-dade
## 62  -81.56627 27.03215   303 12691 florida    de soto
## 63  -82.05329 27.03215   303 12692 florida    de soto
## 64  -82.05329 27.10090   303 12693 florida    de soto
## 65  -82.21371 27.10090   303 12694 florida    de soto
## 66  -82.21371 27.19831   303 12695 florida    de soto
## 67  -82.15642 27.20403   303 12696 florida    de soto
## 68  -82.15642 27.24414   303 12697 florida    de soto
## 69  -82.05901 27.24987   303 12698 florida    de soto
## 70  -82.05901 27.33582   303 12699 florida    de soto
## 71  -81.56054 27.33582   303 12700 florida    de soto
## 72  -81.56627 27.03215   303 12701 florida    de soto
## 73  -81.57200 29.82245   345 14185 florida   st johns
## 74  -81.59492 29.90267   345 14186 florida   st johns
## 75  -81.58920 29.93704   345 14187 florida   st johns
## 76  -81.60065 29.96569   345 14188 florida   st johns
## 77  -81.66940 30.02299   345 14189 florida   st johns
## 78  -81.66940 30.04591   345 14190 florida   st johns
## 79  -81.66367 30.07456   345 14191 florida   st johns
## 80  -81.66367 30.09174   345 14192 florida   st johns
## 81  -81.66367 30.11466   345 14193 florida   st johns
## 82  -81.63503 30.11466   345 14194 florida   st johns
## 83  -81.62357 30.11466   345 14195 florida   st johns
## 84  -81.59492 30.11466   345 14196 florida   st johns
## 85  -81.55482 30.09748   345 14197 florida   st johns
## 86  -81.53762 30.09174   345 14198 florida   st johns
## 87  -81.53189 30.08601   345 14199 florida   st johns
## 88  -81.43449 30.08601   345 14200 florida   st johns
## 89  -81.42876 30.24644   345 14201 florida   st johns
## 90  -81.36574 30.24644   345 14202 florida   st johns
## 91  -81.35427 30.18915   345 14203 florida   st johns
## 92  -81.33136 30.09748   345 14204 florida   st johns
## 93  -81.29125 29.96569   345 14205 florida   st johns
## 94  -81.27979 29.91986   345 14206 florida   st johns
## 95  -81.29125 29.87975   345 14207 florida   st johns
## 96  -81.26833 29.86256   345 14208 florida   st johns
## 97  -81.25114 29.83391   345 14209 florida   st johns
## 98  -81.25114 29.78808   345 14210 florida   st johns
## 99  -81.24541 29.72505   345 14211 florida   st johns
## 100 -81.23396 29.70213   345 14212 florida   st johns
## 101 -81.21104 29.69067   345 14213 florida   st johns
## 102 -81.19958 29.67348   345 14214 florida   st johns
## 103 -81.19958 29.64484   345 14215 florida   st johns
## 104 -81.25114 29.65056   345 14216 florida   st johns
## 105 -81.29125 29.64484   345 14217 florida   st johns
## 106 -81.30844 29.65056   345 14218 florida   st johns
## 107 -81.31990 29.64484   345 14219 florida   st johns
## 108 -81.31417 29.62765   345 14220 florida   st johns
## 109 -81.52616 29.62192   345 14221 florida   st johns
## 110 -81.52616 29.75370   345 14222 florida   st johns
## 111 -81.53189 29.76516   345 14223 florida   st johns
## 112 -81.57200 29.82245   345 14224 florida   st johns
## 113 -80.33441 27.54781   346 14226 florida   st lucie
## 114 -80.32868 27.50770   346 14227 florida   st lucie
## 115 -80.32868 27.46760   346 14228 florida   st lucie
## 116 -80.31149 27.43322   346 14229 florida   st lucie
## 117 -80.27139 27.35301   346 14230 florida   st lucie
## 118 -80.24274 27.29571   346 14231 florida   st lucie
## 119 -80.21409 27.25560   346 14232 florida   st lucie
## 120 -80.28857 27.25560   346 14233 florida   st lucie
## 121 -80.28857 27.20403   346 14234 florida   st lucie
## 122 -80.67245 27.20403   346 14235 florida   st lucie
## 123 -80.67245 27.55354   346 14236 florida   st lucie
## 124 -80.33441 27.54781   346 14237 florida   st lucie
```

Not all the names match; so a touchup of subregion names is called for. 


```r
absent_21_c$subregion <- gsub("dade", "miami-dade", fixed = TRUE, absent_21_c$subregion)

absent_21_c$subregion <- gsub("desoto", "de soto", fixed = TRUE, absent_21_c$subregion)

absent_21_c$subregion <- gsub("st. johns", "st johns", fixed = TRUE, absent_21_c$subregion)

absent_21_c$subregion <- gsub("st. lucie", "st lucie", fixed = TRUE, absent_21_c$subregion)
```



### Join Forces

Put the 


```r
map_d <- inner_join(fl_county, absent_21_c, by = "subregion") #join map data and educational data
```


# Map Set Up

This is where I started to blindly  follow.  In essence, what this chunk is doing is setting up the parameters of the theme. 


```r
ditch_the_axes <- theme(
  axis.text = element_blank(),
  axis.line = element_blank(),
  axis.ticks = element_blank(),
  panel.border = element_blank(),
  panel.grid = element_blank(),
  axis.title = element_blank()
  )
```




```r
fl_abs <- fl_base + 
      geom_polygon(data = map_d, aes(fill = mean), color = "white") +
      geom_polygon(color = "black", fill = NA) +
      theme_bw() +
      ditch_the_axes

fl_abs
```

![plot of chunk unnamed-chunk-5](figure/unnamed-chunk-5-1.png)



```r
fl_abs_2 <- fl_abs + 
    scale_fill_gradientn(colours = rev(rainbow(7)),
                         breaks = c(2, 4, 10, 100, 1000, 10000),
                         trans = "log10")
fl_abs_2
```

![plot of chunk unnamed-chunk-6](figure/unnamed-chunk-6-1.png)

