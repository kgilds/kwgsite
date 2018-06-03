----
title: "worknotes"

----

# Notes from workin

### 06/03/2018
Yesterday 06/02/2018 downloaded updated data and ran all. Think I got teacher and parent survey where I want. Strategy will be put the table as they are now but collapse some of the levels so that graph can be a bit cleaner or focused; currently I would have to run the width wider and the output to word is sub-optimal. There is a function in Forcats that will do this. 


06/03/2018: Worked in the bookdown framework but really I was setting up functions for the analysis. It was just side benefit that it was also rendering the bookdown format.

Received this error < Error in rmarkdown::render_site("/home/jdb-work/index.Rmd", encoding = "",  : 
  unused argument (knit_root_dir = "~")
Execution halted

I corrected the problem by setting the Set the Knit Directory to Document Directory. Here is github issue that helped me resolve the issue.  https://github.com/rstudio/rstudio/issues/2158. Not sure if this is the same problem but used the solution to solve the problem. 

Next iteration may be to use the functions developed today and update package so that you may use for other life skills?  Write and utilize the package in iterations. 

A couple of thoughs; post work notes on webpage; do I put it as a post or seperate page. tagging the page would be fun. I think I will post it. 





### 05/28/2018
Yesterday {05/28/2018} figured out ggplot problem. Need to figure out scales add percent signs. 

identified places where functions could be placed. I suspect with a package we could get the whole system report system in a package. 

started documenting package but had trouble connecting to git repo. 
making connecting to a git repo without files. need to add git add. commit and master will emerge


### 05/24/2018
Worked on cleaning up parent post survey. Need to change name. The report is structured to pull down by section. Looked at using janitor package; I loved it but there is something to be said for the table output; recall the graphs never work in Word. Also the possibilities with Shiny are fantastic. Could you arrange the ordrer it displays. 

### 05/23/2018

* Merged in q3 into Master this morning.


working on q3 sections today; noticed that attendance and behavior follow the same structure; I just used save as and adjusted the name of the input and output data. I don't think the time section of the save rds function is just a zombie--there but not being used. 

### 04/28/2018
started on q3, functions, functions. I don't think I can replace q1 and q3 scripts until or unless you run through shiny. But you can leave it a bit more abstract (save as quarter as opposed to q1; however not sure good or bad) when you save it as an RDS that is when you can specify time frame of the data source; Thinking about how many functions I have for each section purr may be a method.

### 04/22/201
worked on post surveys; and started shiny sidebar. I think I like the drop down in the body. 


### 01/07/2018
 
Don't forgot to use branches for development; so you can see your bad code. 

### 01/06/2018
spin worked


#01/05/2018
worked on cleaning up academic scripts and reports; nearly ready they are nearly taking shape.

* review how to dentisty histograms or see grades through the years-- #01/07/2017--this is not going to work


#01/04/2017
downloaded data from qualtrics ran status report; updated application; sent e-mail with status report.

#01/01/2017-01/03/2017
worked on foundation of academic data. Settled on sourcing rscripts into reports; attempted to use Rmd file and that did not work.



#12/31/2017
finished am and ae history. completed draft of langarts included reverse engineering of if_else with converting numbers to letter grades. started on reading report but did not save the file and windows crashed while savings. :)

* put helper r scripts into sub folders that make sense will need to make adjustments to script to reflect this change;

* update name of objects in langarts script; I don't like that it refers to q1_?--q1 what. Also name of the objects that read; lang grade is not specific enough. 




#12/30/2017
created datset with pre survey data, saved to rds. updated hr_history section; created seperate r script hr_history; created seperate data elements and put into table. 

##todo

* ae_history
* am_history

#12/29/2017
started working on history; rabbit hole; it can be easy or complicated. downloaded data from db to csv file and placed in history folder. 

#12/27/2017
added q2, q3, and q4 data entry into qualtrics; need to review again. 
worked on ensuring I knew how to combine all the csv files; this worked well no trouble. Need to map out what all needs to be entered; have attendance reports; need to recall; all what I enter.
started working on updating package and how to document; struck me that matches are going to be a problem with the current configuration. Decisions need to be made on how to handle. 


#12/24/2017 & 12/25/2017
worked on structure for formuative evaluaiton report; I don't think bookdown is going to work if it can't source. split parent and teacher survey off of main report; checked and was able to child it and run it. The reason for this decision was because i was getting a weird message in the output and could not shake it with message=FALSE, comments=FALSE, warning=FALSE. Noted a nuance of round function and this is documented else where. 


#12/23/2017

updated data and ran reports. did not e-mail 


#12/22/2017

worked on trying to control the name of the file that is downloaded; the download handler takes you to weird places and the reactivity is not working anyway; you have control; you need to determine and you may want to split between download handler and trying to save the data to directory without the handler. ?  Another question since this is interal can you just put the data to console and save it that way? 

started work on getReal2 package. able to put outcome data using use_data function. Reading book on documentation. 

#12/20/2017

finished basic teacher report. Str saved me again on this data.  
cloned shiny_tracker from linux box and appear to have implemented a attendance data entry form. Next step will be to complete reports out of it.

#12/17/2017
struggled with the parent report; it was a read RDS problem and to use likert had to switch to reading to csv file. 

#12/16/2017
downloaded data and updated reports


#12/10/2017
finished q1-lang arts, q1_reading, q1_attendance, q1_behavior; this issue is that you will have to do this for each quarter if you do not figure out a different method to process. cleaned up rds files in processing. 

#12/09/2017
Updated data and status report; need to submit and redloy application

* started a council notebook with tabs; just need to clean up
  * this could be a good chance to use parameters
  
* 12/10/2017 need to start framework for q1. 


#12/02/2017
Added q1 for status report. seems like you got this up and running; including the shiny app; only thing you will need to do or think about is changing the name; also when you may need to make a change when you start counting post surveys. Total time today 4 hours 19 min


#12/01/2017
 Survey locations finised; this off directed to shiny app finished up shiny app and redeployed with site information. 

* Southeast has some schools LLMS, LL, L are the just one?

* also a data entry with Southeast but with a west central florida school. 



#11/30/2017
dded site_count.r to 02A Process-Student-Pre-Survey not able to use read_chunk but was able to source in the script?  I don't think it will be too hard to fix up with script; may want to include council to review sites. 


#11/29/2017
sent status report infomration; that took about 39 minutes. created new branch;  Played with school names and finding method to clean up the data entry. Current method gsub is not optimal because it will require spotting errors and makeing manual adjustments. Looked at regular expressions as a better method but not sure how to implement. I think there a good examples in the tidy text book of regular expressions used in the wild so to speak. Also, I am not sure if this needs to be perject; I am not sure it would be perfect even with regular expressions. 


# 11/25/2017
dl data from qualtrics and ran reports; about 11 minutes to dl data and get them ready to be read from scripts. Status report does not render as pdf; you need to recall to update the data anyway; would it be out of line to send as notebook. what is the practice or weaving through notebook and knitted material. The html document sucks in its current form; maybe pretty it up. almost like the duplicate report. Might be the best way to render and communicate the informatin anyway. 

It struck me this morning that import script should not be confined to just the survey data and this change should be reflected in the mind map; it will make the mind map better!



# 11/24/2017

Yesterday worked on trying to automate turning surveys answers into strings. my observation is that it may be useful to dl as a numbers rather than choice text; and then display with likert you are just reverse engineering; and this seems to be the practice. 

# 11/23/2017

Worked on reviewing duplicate entries and made determination to look for ways to automate this.

* fixed southeast student entry.
* downloaded rpivottable and was able to add tabs to report, base, school, grade. 

** create instrutions what to look for in report. 

find 



#11/20/2017 & 11/21/2017

had an idea to complete notebooks on the outcome and reference the code to a full report; was able to do this kind of. I finally figured this [article](http://zevross.com/blog/2014/07/09/making-use-of-external-r-code-in-knitr-and-r-markdown/). It is working beautifully; now to determine what to include in the outcome script file. Have basic count/percent and by council. Do you do average? and how are you going to reference history

#11/19/2017

was able to get the gmailr script to integrate with status report; for now I have my e-mail to test. could not get it to attach file. check around on intrawebs and other people have problems. Spent most of the morning working on documentation and freem mind workflow.

* made another mindmap to identify milestones, and data sources; this helped.

* make a mindmap of the getReal History book is a heck of a thought. 

* made determintation to write one pre survey analysis file; this may be for student, teacher and parent seperately however.. This may change as you start to work on it. I don't know if you are going to compare prior years or not. 

* tease the idea of writing an updated internal package for Get Real; I can't recall my own functions and what is needed. 




#11/18/2017
pulled data down from qualtrics; data pulled, reports ran, and apps updated. 

The only issiue is that I noted that gswcf dropped 3 and thought maybe it was due to duplicates. Compared student survey files and it turned out 3 were missing from the last data pull on 11/11/2017. Found them; identified response_id and could not find them in qualtrics. Saved the data seperate in files and sent message to Rebecca. Played around with gmailr and I can get the main script to run but can't seem to get the attachment working. 

* don't forget to update the sentence in the status report when the data was pulled? Is there anyway to automate this? 

? could you source gmail scrip to run from the status report rmds. Need attachment to work and may want to just put in draft format. 


#11/14/2017


sent status report; idea for summarizing by site. May need to use a lookup table. Could you automatically compare the answers. 

tested this idea for status report; however, I used the entire survey_status as the whole rather than segmenting by each data source. It did not return any difference. I have hard time seeing that segmenting by source would make a difference. 

```R
student_pre_count <- student_pre_unique %>%
	mutate("Source"  = "Student Pre") %>%
	group_by(Source or council) %>%
	count(Source)
	
```


#11/12/2017


### Status Report Application
Put multiple tabs on data entry statup application; it works but not jazzed about; thinking of seeing how a tab box would work with the orginal application. Otherwise I think it would require to do a seprate page for all the output and then a council seperate page tab. taboxes in dashboard do not display color. 

Have a tab/page for straight data entry status; this you may want to split into info boxes. 
then a council page. Set new branch and merged into master and published. 

? I may want to put the input chooser on the inside of body of the page but I am not sure where?

* May want to split the data sources into value or info boxes but I think you need to a branch and test. 


? by location 

### status report process

? write a script to move the csv files to dropbox
command line script to do this. 

? render the pdf file and script to e-mail it or least put in draft email. 






* Need to send rds file to the status application folder--completed

* correct file extensions on rds file--completed






#11/11/2017

recalled to switch back to master branch before updating data. 

In qualtrics before to download from legacy downloader to match with your code. There seems to be a very slight change in the process.

In the run_all script chunks I put as an option cache=TRUE. Need to learn about this; it did speed up the running process. It did not change my pdf output; however, I had it open. Just monitor this.

Not jazzed about vaild surveys entered by council tbl. Maybe try a group_by call. there are a lot of dependcies--each subject will need to be changed if it works; so how can you test. Maybe test on branch

but this is a starting point. 


```R
student_pre_count <- student_pre_unique %>%
	mutate("Source"  = "Student Pre") %>%
	group_by(Source or council) %>%
	count(Source)
	
```
What I would like to see happen.

Work flow proesss that will send data to the status update application.

Also a flow to send data to dropbox folder. This may be a change when you test the scripts. This may be subtle challenge to send in  the directory; I did save a bookmark on firebox broweser on using purr to loop and create the files. I wonder if you could add the file path. Recall the script works 


student_pre_count

Gateway has a lot of student survey errors on this batch. 

#11/10/2017

Going to make another branch; change the app with better data to converge and display data. 

set up a notebook and merge the data sets and see what you can produce
merged rds files that are by council together to determine if that will fix the isse. The issue is that the boxes are moving if the data is not consistent. For instance, Gateway does not have any errors and that is making the box move around; in a simliar fashion West Central Council does not have parent errors and that is throwing the data off. 

* You are going to have to move the errors to a second page. 

# 11/07/2017
Sent status report. Looked at app and when you change the council; things start moving. Not ready to be shared yet. 

* Need to work on reviewing the duplicates; most likely it will be easier to resolve now rather than waiting all the errors to come in. 


#11/06/2017
Worked on cleaning up status report; and looking at formatting system time. 



# 11/05/2017

worked on adding graphs to the status report document. completed viable product for status update application; made some switches which took some time to debug. Determined to leave graphs out; not that interesting. Put errors and status together to avoid too much switch between tasks and keeping the date together; trade off was that errors by council can't be dynamic. Just get a list all together.

* It may be a good idea to put the errors as one rds and then do the split later or in the server scripts. current method is too efficient. 

* Can you think of a way to get the output and save as the current date to monitor progress as we go along. Time series data. 

* take the graphs off the status report. 


# 11/04/2017

downloaded data from qualtrics. ironed out some and kinks in the scripts.

Made the determination to only use 1 import script rather than segment out student, parent, and teacher. The essence of the script was to read the csv file and save back as an rds.

Made the determination to use dashboard shiny app rather than a flexboard. I like the control aspects and putting a lot of different information on the same screen.

* Need to delete other import files; actually updated map already
* Clean up the status report. Status report is the mail delirvable.  in case application is not ready.
* Diagram it out. 
* Can you write an automatic e-mail script of the status report and link 



# 11/03/2017

cloned the wiki to local machine. may want to put the code book and methodology  sections as a holding place. 

worked this week on getting ready for a status report. Took a different approach this time instead of an all encompassing script to extract the data; there are many scripts to feed the status report. Will need to evaluate how well this works. Currently it is working and a pdf renders. In theory, only the import files should have to be updated to read the most current downloaded csv files. Maybe you can develop an app this weekend.


# 10/29/2017

Naming conventions should follow this 

01-Task-Subject-Sub-Subject

Import      01
Process     02
Sub-process 02A or 2B etc
Match       03
Analysis    04


add naming convention as task in trello



worked through frame work on getting survey count and survey error counts. Used helper scripts to obtain counts and they will run in the 4 processing script.

* 02A-Process-Subject-Pre-Survey
* 02B-Process-Subject-Pre-Dupes
* 02A-Process-Subject-Post-Survey
* 02B-Process-Subject-Post-Dupes

Also started R helper script to process all the count RDS file and bind them together. How are you going to chart this?

* will need to do this for the council rds file as well.




# 10/28/2017

finished updating parent scripts--pre, pre_dupes, post post_dupes. Started working on framework for status report; started notebooks for obtaining counts--dont forget you have to do a duplicates; does this mean another script. Currently put in seperate notebooks but would this be better as a script and when you process the script it is generated?

this was a nice hack to get the raw count rather than using nrows because this way you have the source
```
#!r

teacher_pre_count <- teacher_status %>%
	mutate("Source"  = "Teacher Pre") %>%
	count(Source)
```



#10/21/2017

update on working directory issue: I went to global seting to change to establish the project as the working directory; will this hold true every time you start R studio


worked on all the teacher scripts. Came up with I think a better naming schemes for files; Task #--01, 02 and substep 02A Process Pre  Surve, 02B Process Pre Duplicates--Next is Name of Data Source--Next is more descriptive of the file. 02B-Process_Teacher_Pre_Survey. 

idea; you could incorporate this wiki as the codebook? 

# 10/20/2017

worked on redoing student scripts and outlining process. figured out how not to set working directory with "file_folder/name_of_file". However, I am mannually setting the option to run the project directory--need to hardcode this in with scripts. Also started the process of breaking file structure down in free mind. 


## 10/14/2017

* fixed typo in Q1 grade portal-directions sections

* ran some test scripts with q1 grade portal. It is processing as expected

* worked out script processing frame work. 

The import file should be kept separate from processing tasks. For example the import script should not also change variable names and other processing tasks. This way there is a clean data set from the csv.

The processing scripts generally can/should contain scripts that change variable names, ensure the survey is completed, change girl code to upper; make council names consistent--general clean up.

Determined to have a processing script that deals with duplicate as separate file. Processing "Module" Duplicates. This has some elements of "duplication"--no pun intended but it is a distinct task from what we are trying to produce--A data frame or set without errors. 

 

 

10/07/2017
Scripts to process q1 language arts--needs more splitting into sub sections. Need more test data to see how the scripts respond/work. 

10/06/2017
switched Q1 grade data entry from radial buttons to drop down button. This allows users to deselect a course. Noted that arrow buttons will change the grade value; tab is the better way to navigate. Noted this in the directions.