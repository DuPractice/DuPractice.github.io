---
title: Multiple ways to import text data in R
date: 2023-08-01T16:00:21-04:00
author: Xinting Du
slug: bookdown-tips
draft: false
toc: true
tags: R
---


# Past
Reading text files is always the first step when analyzing the text data. However, it could be challenging. Before I get to know the **package 'readtext'**, I used to write a loop to import data like the following code.


```r
# Step one in this approach is grabbing the list of files. 
file.list<-list.files()
file.list

# Step two in this approach is setting up the loop
for(i in 1:length(file.list)){
  
  temp<-import(file.list[i])
  
  if(i==1){amdts<-temp}
  	else{amdts<-bind_rows(amdts,temp)}
  
  print(paste("Loading file",i,"of",length(file.list),sep=" "))
}

```
One advantage is that the for loop could also be applied on importing data more than text data. However, when importing text data via this way, it is inefficient.



# Package readtext

This package could be really powerful if you have many individual files and did not combine them yet, or your data is in many formats and have many variables you want to keep them as covariates.

Here is the [manual reference](https://cran.r-project.org/web/packages/readtext/readtext.pdf).


```r
# ------ Data import ------ #
getwd()
data_dir <- 'you project directory/' 

files <- readtext(paste0(data_dir, "DocName/*"), # here, we import the raw files, drawing document metadata from the file names
# metadata, i.e. covariates
                             docvarsfrom = "filenames", 
                             dvsep="_", 
                             docvarnames = c("Name", "Session", "Year", "Actor", "Speech"))
                             
                             
# read .csv files
files <- readtext( paste0(data_dir, "DocName/*"), text_field = 'texts')                

# only read .txt files in a package
readtext(paste0(data_dir, "DocName/*.txt"))                          

```
The code will return a *data.frame* consisting of a columns doc_id and text that contain a document identifier and the texts respectively, with any additional columns consisting of document-level variables either found in the file containing the texts, or created through the readtext call.
Two advantages of using readtext. 

Once we have a data.frame, it is easy to transfer it into a *tibble*, which could be used in *tidyverse*, *tidytext*, and etc. 
Also, it could be transfered into corpus, which is used in *quanteda*.

```r
# into tibble

text_tibble <- text_files %>% 
	as_tibble()

# into corpus

text_corpus <- text_files %>%
	corprus()
```

