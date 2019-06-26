Lesson\_4
================
Fernando Rodriguez
1/31/2019

# Lesson 4

to do<br> 1. install.packages(“dplyr”)<br> 2. load physics demographic
data<br>

# Table of Contents<br>

1.  Revisiting Subsetting Data<br>
2.  summarize() and table()<br>
3.  Using dplyr() library<br>
      - filter()<br>
      - arrange()<br>
      - select()<br>
4.  Recoding data<br>
5.  dplyr() continued<br>

<!-- end list -->

  - mutate()<br>

# 0a. Load Libraries

``` r
library(readr)
library(ggplot2)
library(summarytools)
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

# 0b. Load our physics demographic data

# importing demographic data using read\_csv()

``` r
demog <- read_csv("/Volumes/GoogleDrive/My Drive/Intro to R Workshop - Winter 2019/Data Files/Physics Course Demo Data.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   roster_randomid = col_double(),
    ##   officialroster = col_character(),
    ##   ingradebookdata = col_character(),
    ##   insurveyparticipatedata = col_character(),
    ##   status = col_character(),
    ##   gender = col_character(),
    ##   eth2009rollupforreporting = col_character(),
    ##   agegroup = col_character(),
    ##   lowincomeflag = col_character(),
    ##   fulltimestatus = col_character(),
    ##   firstgenerationflag = col_character(),
    ##   homeprimarylang = col_character(),
    ##   admissionsstatusdetail = col_character(),
    ##   hsgpa = col_double(),
    ##   transfergpa = col_double(),
    ##   firstregacadyr = col_character(),
    ##   firstregacadterm = col_character(),
    ##   major1 = col_character()
    ## )

# 1\. Subsetting Data

``` r
# get a feel for the data
view(dfSummary(demog))
```

    ## Method 'viewer' only valid within RStudio. Switching method to 'browser'.

    ## Output file written: /var/folders/vv/4z329kws7cz22bxhrvzc0mjh0000gp/T//Rtmpz6Yk6K/file17fc1631c4fe.html

``` r
demog_ss_female <- subset(demog, gender == "Female")
```

# 2\. summary() and table()

``` r
summary(demog$hsgpa) # numeric data
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
    ##   3.160   3.910   4.040   4.001   4.145   4.400      41

``` r
table(demog$gender) # character strings
```

    ## 
    ##     Female       Male Not stated 
    ##         91         67          1

# 3\. Use dplyr() to transform our data

filter() - pick observations(e.g. students) by a specific value

``` r
demog_ss_gender <- filter(demog, gender == "Female" | gender == "Male")
```

filter by two different criteria

``` r
test1 <- filter(demog, gender == "Male" & ingradebookdata == "Yes")
```

``` r
summary(demog$hsgpa)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
    ##   3.160   3.910   4.040   4.001   4.145   4.400      41

``` r
test2 <- filter(demog, gender == "Male" & hsgpa >= 4.0)
```

Exercise

1.  create a filter function
2.  that filters by students who are low-income AND first-generation
    students
3.  Assign this filter to a new
dataframe

<!-- end list -->

``` r
test3 <- filter(demog, lowincomeflag == "Y" & firstgenerationflag == "Y")
```

# agrrange()

reorder rows

``` r
test4_arrange <- arrange(demog, major1)
```

using is.na

``` r
x <- NA
is.na(x)
```

    ## [1] TRUE

``` r
!is.na(x)
```

    ## [1] FALSE

``` r
demog_ss <- filter(demog, !is.na(major1))
```

# Recoding data

let’s use demog\_ss from now on

``` r
demog_ss$gender_num <- NA
summary(demog_ss$gender_num)
```

    ##    Mode    NA's 
    ## logical     159

``` r
demog_ss$gender_num[demog_ss$gender == "Male"] <- 0
demog_ss$gender_num[demog_ss$gender == "Female"] <- 1
demog_ss$gender_num[demog_ss$gender == "Not stated"] <- NA

table(demog_ss$gender_num)
```

    ## 
    ##  0  1 
    ## 67 91

``` r
table(demog_ss$gender, demog_ss$gender_num)
```

    ##             
    ##               0  1
    ##   Female      0 91
    ##   Male       67  0
    ##   Not stated  0  0

# hold down alt when selecting multiple rows to mass-edit code

``` r
# 
# demog_ss$gender_num[demog_ss$gender == "Male"] <- 0
# demog_ss$gender_num[demog_ss$gender == "Female"] <- 1
# demog_ss$gender_num[demog_ss$gender == "Not stated"] <- NA
# 
# demog_ss$gender_num2[demog_ss$gender2 == "Male"] <- 0
# demog_ss$gender_num2[demog_ss$gender2 == "Female"] <- 1
# demog_ss$gender_num2[demog_ss$gender2 == "Not stated"] <- NA
# 
# demog_ss$gender_num3[demog_ss$gender3 == "Male"] <- 0
# demog_ss$gender_num3[demog_ss$gender3 == "Female"] <- 1
# demog_ss$gender_num3[demog_ss$gender3 == "Not stated"] <- NA
# 
# demog_ss$gender_num4[demog_ss$gender4 == "Male"] <- 0
# demog_ss$gender_num4[demog_ss$gender4 == "Female"] <- 1
# demog_ss$gender_num4[demog_ss$gender4 == "Not stated"] <- NA
```
