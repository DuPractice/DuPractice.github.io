---
title: When a R user began coding with Python III
date: 2023-07-25T16:00:21-04:00
author: Xinting Du
slug: bookdown-tips
draft: false
toc: true
tags: Python
---



I am pushing forward one of my projects, in which I wish to analyze on the grid level instead of on the administrative level. This kind of aggregation is popular in several studies, name a few, [Besley and Reynal-Querol \(2014\)](https://www.cambridge.org/core/journals/american-political-science-review/article/abs/legacy-of-historical-conflict-evidence-from-africa/6AD09AD8FDC0A82242F1873B6AB3478F), [Michalopoulos and Papaioannou \(2016\)](https://www.aeaweb.org/articles?id=10.1257/aer.20131311), and [Berman, et al \(2017\)](https://www.aeaweb.org/articles?id=10.1257/aer.20150774). While I was doing that, I confronted several problems and finally figured them out.

[Reference](https://stackoverflow.com/questions/52937483/r-fitting-a-grid-over-a-city-map-and-inputting-data-into-grid-squares) in stackoverflow:

Code in this page used the georeferenced data of San Jose and a randomly-created crime data as an example.
The workflow is:
1. Make a grid of squares
2. Spatially join the vector data with the grids
3. Build the dataframe

The output like this:


|grid_id |num_assaults| num_thefts|
|-----------|-----------------|-----------|
|     1    |      100   |      89|
 | 2      |     55   |     456|
|3        |   12      | 1321|
|4      |     48       | 498|
|5     |      66        |  6|



With sf, you can make a grid of squares with the st_make_grid() function. Here I'll make a 2km grid over San Jose's bounding box, then intersect it with the boundary of San Jose. Note that I'm projecting to UTM zone 10N so I can specify the grid size in meters.
```r
library(tigris)
library(tidyverse)
library(sf)
options(tigris_class = "sf", tigris_use_cache = TRUE)
set.seed(1234)

## set San Jose and grids 
sj <- places("CA", cb = TRUE) %>%
  filter(NAME == "San Jose") %>%
  st_transform(26910)

g <- sj %>%
  st_make_grid(cellsize = 2000) %>%
  st_intersection(sj) %>%
  st_cast("MULTIPOLYGON") %>%
  st_sf() %>%
  mutate(id = row_number())
  
 ## generate some random crime data 
  thefts <- st_sample(sj, size = 500) %>%
  st_sf()

assaults <- st_sample(sj, size = 200) %>%
  st_sf()
  
## check the plot
plot(g$geometry)
plot(thefts, add = TRUE, col = "red")

## spatially joined the grid and the dataframe
theft_grid <- g %>%
  st_join(thefts) %>%
  group_by(id) %>%
  summarize(num_thefts = n())

plot(theft_grid["num_thefts"])

## create the result
assault_grid <- g %>%
  st_join(assaults) %>%
  group_by(id) %>%
  summarize(num_assaults = n()) 

st_geometry(assault_grid) <- NULL

crime_data <- left_join(theft_grid, assault_grid, by = "id")

crime_data

```





