---
title: Metallica Concerts with the Tidyverse
author: Kevin
date: '2017-11-19'
slug: metallica-concerts-with-the-tidyverse
categories:
  - tidyverse
tags: []

---

# Introduction
Most of my work in R is hidden from public view--this seems like a blessing but is a curse in many respects; I get no feedback on my work in R. 

I felt challenged and inspired by David Robinson's [post](http://varianceexplained.org/r/start-blog/) *Advice to aspiring data scientist: start a blog*

I completed the following analysis while in the midst of Hurricane Irma in September 2017, and I noticed the analysis utilizes many tidyverse functions. I also like how I referenced the Stack Overflow links when I had to work through a concept.  



## Metallica Concerts

I have attended eight (8) Metallica concerts from 1989 through 2017. Metallica makes available their sets list from their shows at [Met on Tour](https://www.metallica.com/tour/past). The only show where I had to use a different data source is the 1989 show in Cedar Rapids, Iowa. I used this 
[SetList](https://www.setlist.fm/setlist/metallica/1989/hilton-coliseum-ames-ia-33d6d411.html) from Ames, Iowa as a proxy and this list matches my memory. Here is the set list from each show using a datatable. 







```r
tours <- read.delim("metallica_cours.txt") %>%
	rename("Tour_Name" = "Tour_.Name")

#kable(tours)
```


```r
setlist <- read.delim("setlist.txt")

#kable(setlist)
```



```r
setlist_tour <- inner_join(setlist, tours, by="id") #join setlist with tours

#kable(setlist_tour)
```





```r
setlist_tour <- setlist_tour %>%
	select(3, 2, 6:9) 

datatable(setlist_tour)
```

<!--html_preserve--><div id="htmlwidget-5a4fc6ec4c2243c16265" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-5a4fc6ec4c2243c16265">{"x":{"filter":"none","data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40","41","42","43","44","45","46","47","48","49","50","51","52","53","54","55","56","57","58","59","60","61","62","63","64","65","66","67","68","69","70","71","72","73","74","75","76","77","78","79","80","81","82","83","84","85","86","87","88","89","90","91","92","93","94","95","96","97","98","99","100","101","102","103","104","105","106","107","108","109","110","111","112","113","114","115","116","117","118","119","120","121","122","123","124","125","126","127","128","129","130","131","132","133","134","135","136","137","138","139","140","141","142","143","144","145"],["November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","November 10, 1991","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","June 28, 1996","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","January 28, 1997","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","December 29, 1999","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","November 5, 2004","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","October 3, 2009","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","July 5, 2017","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989","June 20, 1989"],["Enter Sandman","Creeping Death","Harvester of Sorrow","Welcome Home (Sanitarium)","Sad But True","Bass Solo","Through The Never","The Unforgiven","Justice Medley","Drum Solo","Guitar Solo","The Four Horseman","For Whom the Bell Tolls","Fade to Black","Whiplash","Master of Puppets","Seek and Destroy","One","Last Caress","Am I Evil?","Battery","So What","Creeping Death","Sad But True","Ain't My Bitch","Whiplash","Fade to Black","King Nothing","One","Until It Sleeps","For Whom the Bell Tolls","Wherever I May Roam","Nothing Else Matters","Enter Sandman","Last Caress","Master of Puppets","Overkill","So What","Creeping Death","Sad But True","Ain't My Bitch","Whiplash","King Nothing","One","Wasting My Hate","Bass/Guitar Solo","Nothing Else Matters","Until It Sleeps","For Whom the Bell Tolls","Wherever I May Roam","Fade to Black","Kill/Ride Medley","Last Caress","Master of Puppets","Enter Sandman","Am I Evil?","Motorbreath","Die, Die, My Darling!","Fuel","For Whom the Bell Tolls","The Four Horseman","Whiskey in the Jar","2X4","No Leaf Clover","Sad But True","Creeping Death","Bleeding Me","Masterarium","Blackend","Nothing Else Matters","King Nothing","One","Turn the Page","Enter Sandman","Phantom Lord","Blackend","Fuel","Sad But True","No Leaf Clover","Holier Than Thou","The Unforgiven","The God that Failed","St. Anger","Fade to Black","Creeping Death","Fighting Fire with Fire","Wherever I May Roam","Nothing Else Matters","Master of Puppets","One","Enter Sandman","Disposable Heroes","Seek and Destroy","That was Just Your life","The End of The Line","Harvester of Sorrow","Through The Never","One","Broken, Beat, and Scared","Cyanide","Sad But True","Welcome Home (Sanitarium)","All Nightmare Long","The Day that Never Comes","Master of Puppets","Battery","Nothing Else Matters","Enter Sandman","The Wait","Trapped Under Ice","Seek and Destroy","Hardwired","Atlas, Rise","For Whom the Bell Tolls","Fuel","The Unforgiven","Now that we are dead","Moth Into Flame","Wherever I May Roam","Halo on Fire","Hit the Lights","Sad But True","One","Master of Puppets","Fade to Black","Seek and Destroy","Fighting Fire with Fire","Nothing Else Matters","Enter Sandman","Blackend","For Whom the Bell Tolls","Welcome Home (Sanitarium)","Harvester of Sorrow","The Thing that should not be","Bass Solo","Creeping Death","Fade to Black","Seek and Destroy","Justice for All","Master of Puppets","One","Guitar Solo","Battery","Last Caress","Whiplash"],["Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Des Moines","Des Moines","Des Moines","Des Moines","Des Moines","Des Moines","Des Moines","Des Moines","Des Moines","Des Moines","Des Moines","Des Moines","Des Moines","Des Moines","Des Moines","Des Moines","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","Ames","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","St. Petersuburg","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Tampa","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Orlando","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids","Cedar Rapids"],["Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Wherever We May Roam","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Lollapalooza","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","Pour Touring Me","M2K","M2K","M2K","M2K","M2K","M2K","M2K","M2K","M2K","M2K","M2K","M2K","M2K","M2K","M2K","M2K","M2K","M2K","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","Madly In Anger With The World","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Magnetic","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","World Wired","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice","Damaged Justice"],["https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/9743","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10075","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10157","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10360","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://www.metallica.com/tour/10565","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://metallica.com/tour/10727","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://www.metallica.com/tour/30535","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640","https://metallica.com/tour/9640"],["Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Iowa State Fairgrounds","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Hilton C","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","Tropicana Field","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","St. Pete Times Forum","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Camping World Stadium","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center","Five Seasons Center"]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>Date<\/th>\n      <th>song_title<\/th>\n      <th>City<\/th>\n      <th>Tour_Name<\/th>\n      <th>Notes<\/th>\n      <th>Venue<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"order":[],"autoWidth":false,"orderClasses":false,"columnDefs":[{"orderable":false,"targets":0}]}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->

## Song Count by City

I have seen Metallica perform the most songs in Cedar Rapids, Iowa and a close second is Tampa, FL. 



```r
setlist_tour_tbl <- tours %>%
	group_by(Tour_Name) %>% #group by tourname
	select(5:6) # select variables City and Tour_Name


kable(setlist_tour_tbl) #display pretty table
```



|City            |Tour_Name                     |
|:---------------|:-----------------------------|
|Cedar Rapids    |Damaged Justice               |
|Cedar Rapids    |Wherever We May Roam          |
|Des Moines      |Lollapalooza                  |
|Ames            |Pour Touring Me               |
|St. Petersuburg |M2K                           |
|Tampa           |Madly In Anger With The World |
|Tampa           |World Magnetic                |
|Orlando         |World Wired                   |



```r
setlist_tour_city <- setlist_tour %>%
     count(City) #get count of City of Tour


kable(setlist_tour_city) #display pretty table
```



|City            |  n|
|:---------------|--:|
|Ames            | 20|
|Cedar Rapids    | 37|
|Des Moines      | 16|
|Orlando         | 18|
|St. Petersuburg | 18|
|Tampa           | 36|



From this set list of eight tours some song titles are repeated and on average song_titles repeat 2.3 times.


```r
song_count_avg <- setlist_tour %>%
	count(song_title) %>% #get a count of songs from setlist
	summarise(song = mean(n)) #get average


kable(song_count_avg) #display pretty table
```



|     song|
|--------:|
| 2.301587|

Below is a graph of the song_titles I have heard more than once. At first, glance, I was surprised that I had not seen *Master of Puppets* eight times. I checked the data and it occurred to me during the [*M2K*](https://www.metallica.com/tour/10360) Tour in St. Petersburg that Metallica performed *Masterarium*--a mix of Master of Puppets and Welcome Home Sanitarium--A fantastic performance. 



<img src="/post/2017-11-19-metallica-concerts-with-the-tidyverse_files/figure-html/song_count_graph-1.png" width="672" />



This [article](https://stackoverflow.com/questions/26114525/r-how-to-count-how-many-values-per-level-in-a-given-factor)
helped me figure out to perform a count using factors. 


## Number of Song performed

On average, Metallica performed 18 songs when I went to see them. 


```r
tour_count_avg <- setlist_tour %>%
	group_by(Tour_Name) %>% #group the songs by tour
	summarise(song_title = length(song_title)) %>%  #get a count of the song_title; song_title is a facotr
	summarise(song_title= mean(song_title)) #obtain mean of the counts

kable(tour_count_avg) #display pretty table
```



| song_title|
|----------:|
|     18.125|

Here is a breakdown of the number of songs played during each tour stop. 


```r
song_count_tour <- setlist_tour %>%
	group_by(Tour_Name) %>%
	summarise(song_title = length(song_title))
	
kable(song_count_tour)
```



|Tour_Name                     | song_title|
|:-----------------------------|----------:|
|Damaged Justice               |         16|
|Lollapalooza                  |         16|
|M2K                           |         18|
|Madly In Anger With The World |         18|
|Pour Touring Me               |         20|
|Wherever We May Roam          |         21|
|World Magnetic                |         18|
|World Wired                   |         18|


### Wordcloud Mess

This [stackoverflow question](https://stackoverflow.com/questions/27981651/text-wordcloud-plotting-error) and answer helped me with this WordCloud. At least it helped me plot all the songs. 




```r
song_count_wc <- setlist_tour %>%
	count(song_title) %>%
	with(wordcloud(song_title, n, scale = c(3, 0.1)))
```

<img src="/post/2017-11-19-metallica-concerts-with-the-tidyverse_files/figure-html/song_count-1.png" width="672" />

### Conclusion

One area for future development is to learn how how to scrape the setlist data from the web. I manually entered into a spreadsheet and turned them into a text file. 
