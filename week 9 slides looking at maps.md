Working with maps in R
========================================================
author: Ray Hoobler
date: March 7th, 2018
autosize: true


Why work with maps?
========================================================

Over the last two years, a number of students have included "spacial analysis" as part of the professional project proposals. Examples include:

- prevalence of lead in blood samples, compared by zip codes 
- examination of lead in municipal water samples 
- mapping the spatial patterns of the salt through time and the geospatial resources of the greater Bonneville Salt Flats research initiative
- evaluating the effectiveness of a watershed restoration plan
- trail activity and its effects on Flammulated Owl breeding populations in Snow Basin Utah

What are my options?
========================================================

Fortunately, there are several options available to display 

- **ggplot2 Esentials** (Chapter 7: ggplot2 and maps)
- [Making Maps with R](http://eriqande.github.io/rep-res-web/lectures/making-maps-with-R.html)
- [**ggmap : Spatial Visualization with ggplot2**] (http://stat405.had.co.nz/ggmap.pdf)

Example of a common map (USGS)
========================================================

[Public Supply Water Use] (https://water.usgs.gov/watuse/wups.html)  
![2010 Water Use](publicsupply-map-2010.png) 

Map details can be found at https://water.usgs.gov/watuse/wups.html  

Example of a common map (PSM)
========================================================
![PSM programs accross the U.S.](plot of psm programs across US - hrz.png)  
(Created by yours truly)

Overview of packages used for maps
===
We will need the flolloiwng librarys to start

```r
library(tidyverse) # this installs ggplot2 and other tidyverse pacakges

library(maps) # draw geograhpical maps

# install.packages("mapdata")
library(mapdata) # additional high resolution outlines (you may need to install the pacakge first)
```

What is in the "maps" pacakge
===
Currently available maps
- world: This is a map of the entire world  
- usa: This is a map of the US coast  
- state: This is a map of the USA at the state level  
- county: This is a map of the USA at the county level  
- italy: This is a map of Italy  
- france: This is a map of France  
- nz: This is a map of New Zealand  

(Excerpt From: “ggplot2 Essentials.” iBooks.)

When possible, work with tidy data
===
Orginal dataset:    

```r
head(us.cities)
```

```
        name country.etc    pop   lat    long capital
1 Abilene TX          TX 113888 32.45  -99.74       0
2   Akron OH          OH 206634 41.08  -81.52       0
3 Alameda CA          CA  70069 37.77 -122.26       0
4  Albany GA          GA  75510 31.58  -84.18       0
5  Albany NY          NY  93576 42.67  -73.80       2
6  Albany OR          OR  45535 44.62 -123.09       0
```

Convert to tidy dat (let's just assume that it will help later)
===
Tidy dataset:  

```r
us_cities <- as.tibble(us.cities)
us_cities
```

```
# A tibble: 1,005 x 6
   name           country.etc    pop   lat   long capital
   <chr>          <chr>        <int> <dbl>  <dbl>   <int>
 1 Abilene TX     TX          113888  32.4  -99.7       0
 2 Akron OH       OH          206634  41.1  -81.5       0
 3 Alameda CA     CA           70069  37.8 -122.        0
 4 Albany GA      GA           75510  31.6  -84.2       0
 5 Albany NY      NY           93576  42.7  -73.8       2
 6 Albany OR      OR           45535  44.6 -123.        0
 7 Albuquerque NM NM          494962  35.1 -107.        0
 8 Alexandria LA  LA           44933  31.3  -92.5       0
 9 Alexandria VA  VA          127159  38.8  -77.1       0
10 Alhambra CA    CA           88857  34.1 -118.        0
# ... with 995 more rows
```



