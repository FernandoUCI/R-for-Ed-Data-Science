Lesson 2
================
Fernando Rodriguez
1/17/2019

<br><br>

# 0\. Load libraries

``` r
# install.packages("summarytools")
library(ggplot2) # for plotting
library(summarytools) # for getting data summaries
```

<br><br>

# 1\. More workflow basics

code chunks alt + command + i (mac)<br> control + alt + i (windows)<br>

### Navigate multiple R-Markdown files

``` r
# using same variable name
a <- 6 + 10
```

<br><br>

### Commenting code / commenting out code<br>

Commenting out multiple lines of code<br> First highlight the code, the
run this<br>

control + shift + c (windows and mac)<br> command + shift + c (mac)<br>

``` r
# add comments. It doesn't effect the caculations

# a <- 6 + 10
# b <- 10 + 10
```

<br><br>

# 2\. Importing Data using read.csv

We are going to use the read.csv() function<br> There are some pros and
cons to using this, but the purpose is to get familiar with finding full
path directories and the consequences of including and excluding
specific
arguments.

``` r
demog <- read.csv("/Volumes/GoogleDrive/My Drive/R Workspace/R-for-Ed-Data-Science/Data/Physics Course Demo Data.csv", header = TRUE)
```

<br><br>

## Getting the structure of the data using str() function

``` r
str(demog)
```

    ## 'data.frame':    192 obs. of  19 variables:
    ##  $ roster_randomid          : int  672849 872962 482931 455346 491579 608378 714417 508735 407162 529371 ...
    ##  $ officialroster           : Factor w/ 3 levels "","NO","Yes": 3 3 3 3 3 3 3 3 3 3 ...
    ##  $ ingradebookdata          : Factor w/ 2 levels "","Yes": 2 2 2 2 2 2 2 2 2 2 ...
    ##  $ insurveyparticipatedata  : Factor w/ 2 levels "","Yes": 2 2 2 2 2 2 2 2 2 2 ...
    ##  $ status                   : Factor w/ 2 levels "","Enrolled": 2 2 2 2 2 2 2 2 2 2 ...
    ##  $ gender                   : Factor w/ 4 levels "","Female","Male",..: 3 3 3 3 2 2 3 2 3 3 ...
    ##  $ eth2009rollupforreporting: Factor w/ 6 levels "","Asian / Pacific Islander",..: 4 2 6 2 2 3 2 2 5 2 ...
    ##  $ agegroup                 : Factor w/ 9 levels "","18","19","20",..: 4 4 8 3 4 3 4 3 4 3 ...
    ##  $ lowincomeflag            : Factor w/ 4 levels "","N","NAT","Y": 2 2 2 2 4 2 2 2 2 4 ...
    ##  $ fulltimestatus           : Factor w/ 3 levels "","Full-time",..: 3 3 3 2 2 2 2 3 2 3 ...
    ##  $ firstgenerationflag      : Factor w/ 5 levels "","MDT","N","NAT",..: 3 3 5 5 5 5 3 5 5 5 ...
    ##  $ homeprimarylang          : Factor w/ 5 levels "","English only",..: 3 2 5 2 5 2 3 2 5 3 ...
    ##  $ admissionsstatusdetail   : Factor w/ 4 levels "","Freshman",..: 2 2 4 2 2 2 2 2 2 2 ...
    ##  $ hsgpa                    : num  4.18 4 NA 4.04 4.14 ...
    ##  $ transfergpa              : num  NA NA 3.22 NA NA NA NA NA NA NA ...
    ##  $ gpacumulative            : logi  NA NA NA NA NA NA ...
    ##  $ firstregacadyr           : Factor w/ 6 levels "","2009-10","2012-13",..: 5 4 6 6 5 5 5 5 5 5 ...
    ##  $ firstregacadterm         : Factor w/ 2 levels "","Fall": 2 2 2 2 2 2 2 2 2 2 ...
    ##  $ major1                   : Factor w/ 27 levels "","Anthropology",..: 5 5 19 13 5 21 5 5 5 5 ...

<br><br>

## 3\. Vector Types and Classes

R has 6 atomic vector types<br> Atomic means that it only holds data of
a single type<br> - character: “a” “string values”<br> - numeric: 2,
1.4, 503<br> - iteger: 2L (the L tells R to store this as an
integer)<br> - logical: TRUE or FALSE<br> - complex: 1+4i (complex
numbers with real and imaginary parts)<br> <br><br>

### Factors

Factors are stored as a vector of integer values WITH a cooresponding
set of character values.<br>

In many ways factors are a special case of integers.<br>

``` r
str(demog$agegroup)
```

    ##  Factor w/ 9 levels "","18","19","20",..: 4 4 8 3 4 3 4 3 4 3 ...

<br><br>

# 4\. Data Reduction, how do you do this?

Using the summarytools library to get overall descriptive info and
NAs.<br><br>

However, as you’ll see next week, the summary tools is not generating
the correct Ns. This has to do with how we imported our data. We need to
include an argument that instructs R what to do with our NAs in the .csv
file.

``` r
view(dfSummary(demog, style = 'rmarkdown'))
```

    ## 'rmarkdown' style not supported - using 'multiline' instead.

    ## Method 'viewer' only valid within RStudio. Switching method to 'browser'.

    ## Output file written: /var/folders/vv/4z329kws7cz22bxhrvzc0mjh0000gp/T//Rtmpy24VA1/file1761275819c2.html

<br><br>

Use these additional arguments to have the table display correctly when
knitting your R-Markdown

``` r
print(dfSummary(demog, graph.magnif = 0.65), method = 'render')
```

<!--html_preserve-->

<div class="container st-container">

<h3>

Data Frame Summary

</h3>

<h4>

demog

</h4>

<strong>N</strong>:
192

<table class="table table-striped table-bordered st-table st-table-striped st-table-bordered st-multiline ">

<thead>

<tr>

<th align="center">

<strong>No</strong>

</th>

<th align="center">

<strong>Variable</strong>

</th>

<th align="center">

<strong>Stats / Values</strong>

</th>

<th align="center">

<strong>Freqs (% of Valid)</strong>

</th>

<th align="center">

<strong>Graph</strong>

</th>

<th align="center">

<strong>Valid</strong>

</th>

<th align="center">

<strong>Missing</strong>

</th>

</tr>

</thead>

<tbody>

<tr>

<td align="center">

1

</td>

<td align="left">

roster\_randomid \[integer\]

</td>

<td align="left">

mean (sd) : 514434.11 (243939.78) min \< med \< max : 104500 \< 543478
\< 994588 IQR (CV) : 409408.75 (0.47)

</td>

<td align="left">

192 distinct
values

</td>

<td align="center" border="0">

<img src="data:image/png;base64,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">

</td>

<td align="center">

192 (100%)

</td>

<td align="center">

0 (0%)

</td>

</tr>

<tr>

<td align="center">

2

</td>

<td align="left">

officialroster \[factor\]

</td>

<td align="left">

1.  
2.  NO

3.  Yes
    
    </td>
    
    <td align="left">
    
    2 (1.0%) 14 (7.3%) 176
    (91.7%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    3
    
    </td>
    
    <td align="left">
    
    ingradebookdata \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
4.  Yes
    
    </td>
    
    <td align="left">
    
    16 (8.3%) 176
    (91.7%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    4
    
    </td>
    
    <td align="left">
    
    insurveyparticipatedata \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
5.  Yes
    
    </td>
    
    <td align="left">
    
    2 (1.0%) 190
    (99.0%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGEAAAAhCAYAAADJXsXPAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAFNSURBVGgF7ZixioNAEIZ3VwlKCPZ3YKtYpbNMXsgHuCe4zkIf55p9g+ssbE7srk5sguiNB+mmzTDIv03IEPh/v48lyQSGTtM0l7Isf7338/YeR5aAa9v2GgSBT9P0QzYaaU8Cbl3XY1EUN2vt4TnEqywBJxuHNI4AJHBUhGeQIAyci4MEjorwDBKEgXNxkMBREZ5BgjBwLg4SOCrCM0gQBs7FQQJHRXgGCcLAuThHO6Op67oT7ZAe3Acwez0BV1WVJwGXcRw/Xx+HBBBQSsDWdf2eJMlXFEU3pR13XWtZlkNI55zn+VuWZcmun1bpw83zbMKtG305mziOldbcd61pmgx+oipwDAmQoICAggq4CZCggICCCrgJkKCAgIIKuAmQoICAggq4CQok/K8taIlkt7/POPIEiL0JaW/03ff9zzAMd/kKSCQCFhQUEPgDeV89rsjbzhoAAAAASUVORK5CYII=">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    5
    
    </td>
    
    <td align="left">
    
    status \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
6.  Enrolled
    
    </td>
    
    <td align="left">
    
    16 (8.3%) 176
    (91.7%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    6
    
    </td>
    
    <td align="left">
    
    gender \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
7.  Female

8.  Male

9.  Not stated
    
    </td>
    
    <td align="left">
    
    33 (17.2%) 91 (47.4%) 67 (34.9%) 1
    (0.5%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    7
    
    </td>
    
    <td align="left">
    
    eth2009rollupforreporting \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
10. Asian / Pacific Islander

11. Hispanic

12. International student

13. Unknown / declined to sta

14. White, non-Hispanic
    
    </td>
    
    <td align="left">
    
    33 (17.2%) 102 (53.1%) 18 (9.4%) 15 (7.8%) 13 (6.8%) 11
    (5.7%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    8
    
    </td>
    
    <td align="left">
    
    agegroup \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
15. 18

16. 19

17. 20

18. 21

19. 22

20. 23

21. 24

22. 25-29
    
    </td>
    
    <td align="left">
    
    33 (17.2%) 6 (3.1%) 59 (30.7%) 67 (34.9%) 17 (8.8%) 6 (3.1%) 1
    (0.5%) 1 (0.5%) 2
    (1.0%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    9
    
    </td>
    
    <td align="left">
    
    lowincomeflag \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
23. N

24. NAT

25. Y
    
    </td>
    
    <td align="left">
    
    33 (17.2%) 102 (53.1%) 2 (1.0%) 55
    (28.6%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    10
    
    </td>
    
    <td align="left">
    
    fulltimestatus \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
26. Full-time

27. Part-time
    
    </td>
    
    <td align="left">
    
    33 (17.2%) 93 (48.4%) 66
    (34.4%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    11
    
    </td>
    
    <td align="left">
    
    firstgenerationflag \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
28. MDT

29. N

30. NAT

31. Y
    
    </td>
    
    <td align="left">
    
    33 (17.2%) 7 (3.6%) 77 (40.1%) 2 (1.0%) 73
    (38.0%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    12
    
    </td>
    
    <td align="left">
    
    homeprimarylang \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
32. English only

33. English/non-English

34. Missing data

35. Non-English
    
    </td>
    
    <td align="left">
    
    33 (17.2%) 37 (19.3%) 67 (34.9%) 2 (1.0%) 53
    (27.6%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    13
    
    </td>
    
    <td align="left">
    
    admissionsstatusdetail \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
36. Freshman

37. Not applicable

38. Transfer
    
    </td>
    
    <td align="left">
    
    33 (17.2%) 151 (78.6%) 2 (1.0%) 6
    (3.1%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    14
    
    </td>
    
    <td align="left">
    
    hsgpa \[numeric\]
    
    </td>
    
    <td align="left">
    
    mean (sd) : 4 (0.22) min \< med \< max : 3.16 \< 4.04 \< 4.4 IQR
    (CV) : 0.23 (0.06)
    
    </td>
    
    <td align="left">
    
    59 distinct
    values
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    151 (78.65%)
    
    </td>
    
    <td align="center">
    
    41 (21.35%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    15
    
    </td>
    
    <td align="left">
    
    transfergpa \[numeric\]
    
    </td>
    
    <td align="left">
    
    mean (sd) : 3.33 (0.28) min \< med \< max : 3.01 \< 3.25 \< 3.71 IQR
    (CV) : 0.38 (0.08)
    
    </td>
    
    <td align="left">
    
    3.01 : 1 (16.7%) 3.14\! : 1 (16.7%) 3.22 : 1 (16.7%) 3.28 : 1
    (16.7%) 3.63\! : 1 (16.7%) 3.71 : 1 (16.7%) \!
    rounded
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">

</td>

<td align="center">

6 (3.12%)

</td>

<td align="center">

186 (96.88%)

</td>

</tr>

<tr>

<td align="center">

16

</td>

<td align="left">

gpacumulative \[logical\]

</td>

<td align="left">

</td>

<td align="left">

All NA’s

</td>

<td align="center" border="0">

</td>

<td align="center">

0 (0%)

</td>

<td align="center">

192 (100%)

</td>

</tr>

<tr>

<td align="center">

17

</td>

<td align="left">

firstregacadyr \[factor\]

</td>

<td align="left">

1.  
2.  2009-10

3.  2012-13

4.  2013-14

5.  2014-15

6.  2015-16
    
    </td>
    
    <td align="left">
    
    33 (17.2%) 1 (0.5%) 5 (2.6%) 21 (10.9%) 109 (56.8%) 23
    (12.0%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    18
    
    </td>
    
    <td align="left">
    
    firstregacadterm \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
7.  Fall
    
    </td>
    
    <td align="left">
    
    33 (17.2%) 159
    (82.8%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    <tr>
    
    <td align="center">
    
    19
    
    </td>
    
    <td align="left">
    
    major1 \[factor\]
    
    </td>
    
    <td align="left">
    
    1.  
8.  Anthropology

9.  Art

10. Art History

11. Biological Sciences

12. Biology/Education

13. Business Administration

14. Business Economics

15. Computer Game Science

16. Computer Science \[ 17 others \]
    
    </td>
    
    <td align="left">
    
    33 (17.2%) 1 (0.5%) 2 (1.0%) 1 (0.5%) 89 (46.4%) 1 (0.5%) 1 (0.5%) 1
    (0.5%) 6 (3.1%) 5 (2.6%) 52
    (27.1%)
    
    </td>
    
    <td align="center" border="0">
    
    <img src="data:image/png;base64,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">
    
    </td>
    
    <td align="center">
    
    192 (100%)
    
    </td>
    
    <td align="center">
    
    0 (0%)
    
    </td>
    
    </tr>
    
    </tbody>
    
    </table>
    
    <p>
    
    Generated by
    <a href='https://github.com/dcomtois/summarytools'>summarytools</a>
    0.8.8 (<a href='https://www.r-project.org/'>R</a> version
    3.5.2)<br/>2019-06-25
    
    </p>
    
    </div>
    
    <!--/html_preserve-->
    
    <br><br>

### Importing csv files with correct NAs

``` r
demog2 <- read.csv("/Volumes/GoogleDrive/My Drive/R Workspace/R-for-Ed-Data-Science/Data/Physics Course Demo Data.csv", header = TRUE,
                   na.strings = c ("", NA))
```

<br><br>

### Re-running dfSummary

``` r
print(dfSummary(demog2, graph.magnif = 0.65), method = 'render')
```

<!--html_preserve-->

<div class="container st-container">

<h3>

Data Frame Summary

</h3>

<h4>

demog2

</h4>

<strong>N</strong>:
192

<table class="table table-striped table-bordered st-table st-table-striped st-table-bordered st-multiline ">

<thead>

<tr>

<th align="center">

<strong>No</strong>

</th>

<th align="center">

<strong>Variable</strong>

</th>

<th align="center">

<strong>Stats / Values</strong>

</th>

<th align="center">

<strong>Freqs (% of Valid)</strong>

</th>

<th align="center">

<strong>Graph</strong>

</th>

<th align="center">

<strong>Valid</strong>

</th>

<th align="center">

<strong>Missing</strong>

</th>

</tr>

</thead>

<tbody>

<tr>

<td align="center">

1

</td>

<td align="left">

roster\_randomid \[integer\]

</td>

<td align="left">

mean (sd) : 514434.11 (243939.78) min \< med \< max : 104500 \< 543478
\< 994588 IQR (CV) : 409408.75 (0.47)

</td>

<td align="left">

192 distinct
values

</td>

<td align="center" border="0">

<img src="data:image/png;base64,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">

</td>

<td align="center">

192 (100%)

</td>

<td align="center">

0 (0%)

</td>

</tr>

<tr>

<td align="center">

2

</td>

<td align="left">

officialroster \[factor\]

</td>

<td align="left">

1.  NO
2.  Yes
    </td>
    <td align="left">
    14 (7.4%) 176
    (92.6%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">
    </td>
    <td align="center">
    190 (98.96%)
    </td>
    <td align="center">
    2 (1.04%)
    </td>
    </tr>
    <tr>
    <td align="center">
    3
    </td>
    <td align="left">
    ingradebookdata \[factor\]
    </td>
    <td align="left">
    1.  Yes
        </td>
        <td align="left">
        176
        (100.0%)
        </td>
        <td align="center" border="0">
        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGEAAAAQCAYAAAAGeBHHAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAACWSURBVFgJ7ZjBCcAgEAQ9CSHiwxICeUrAXtKZtpROLCA/X8IR0kRccG3AuRkOQck5n977O4TwGJ7fDfTe10VE9hijpJSO3wl4oWmtGUsP4w0wwvgG3ASABozACAgGABj4JjACgAEABG4CIwAYAEDgJjACgAEABG4CQITvA09rrZtzTgF4pkNQVSPf1KWUy1rrpzMAMvALfjkVAm1e7IYAAAAASUVORK5CYII=">
        </td>
        <td align="center">
        176 (91.67%)
        </td>
        <td align="center">
        16 (8.33%)
        </td>
        </tr>
        <tr>
        <td align="center">
        4
        </td>
        <td align="left">
        insurveyparticipatedata \[factor\]
        </td>
        <td align="left">
        1.  Yes
            </td>
            <td align="left">
            190
            (100.0%)
            </td>
            <td align="center" border="0">
            <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGEAAAAQCAYAAAAGeBHHAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAACWSURBVFgJ7ZjBCcAgEAQ9CSHiwxICeUrAXtKZtpROLCA/X8IR0kRccG3AuRkOQck5n977O4TwGJ7fDfTe10VE9hijpJSO3wl4oWmtGUsP4w0wwvgG3ASABozACAgGABj4JjACgAEABG4CIwAYAEDgJjACgAEABG4CQITvA09rrZtzTgF4pkNQVSPf1KWUy1rrpzMAMvALfjkVAm1e7IYAAAAASUVORK5CYII=">
            </td>
            <td align="center">
            190 (98.96%)
            </td>
            <td align="center">
            2 (1.04%)
            </td>
            </tr>
            <tr>
            <td align="center">
            5
            </td>
            <td align="left">
            status \[factor\]
            </td>
            <td align="left">
            1.  Enrolled
                </td>
                <td align="left">
                176
                (100.0%)
                </td>
                <td align="center" border="0">
                <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGEAAAAQCAYAAAAGeBHHAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAACWSURBVFgJ7ZjBCcAgEAQ9CSHiwxICeUrAXtKZtpROLCA/X8IR0kRccG3AuRkOQck5n977O4TwGJ7fDfTe10VE9hijpJSO3wl4oWmtGUsP4w0wwvgG3ASABozACAgGABj4JjACgAEABG4CIwAYAEDgJjACgAEABG4CQITvA09rrZtzTgF4pkNQVSPf1KWUy1rrpzMAMvALfjkVAm1e7IYAAAAASUVORK5CYII=">
                </td>
                <td align="center">
                176 (91.67%)
                </td>
                <td align="center">
                16 (8.33%)
                </td>
                </tr>
                <tr>
                <td align="center">
                6
                </td>
                <td align="left">
                gender \[factor\]
                </td>
                <td align="left">
                1.  Female
3.  Male
4.  Not stated
    </td>
    <td align="left">
    91 (57.2%) 67 (42.1%) 1
    (0.6%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">
    </td>
    <td align="center">
    159 (82.81%)
    </td>
    <td align="center">
    33 (17.19%)
    </td>
    </tr>
    <tr>
    <td align="center">
    7
    </td>
    <td align="left">
    eth2009rollupforreporting \[factor\]
    </td>
    <td align="left">
    1.  Asian / Pacific Islander
5.  Hispanic
6.  International student
7.  Unknown / declined to sta
8.  White, non-Hispanic
    </td>
    <td align="left">
    102 (64.1%) 18 (11.3%) 15 (9.4%) 13 (8.2%) 11
    (6.9%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">
    </td>
    <td align="center">
    159 (82.81%)
    </td>
    <td align="center">
    33 (17.19%)
    </td>
    </tr>
    <tr>
    <td align="center">
    8
    </td>
    <td align="left">
    agegroup \[factor\]
    </td>
    <td align="left">
    1.  18
9.  19
10. 20
11. 21
12. 22
13. 23
14. 24
15. 25-29
    </td>
    <td align="left">
    6 (3.8%) 59 (37.1%) 67 (42.1%) 17 (10.7%) 6 (3.8%) 1 (0.6%) 1 (0.6%)
    2
    (1.3%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">
    </td>
    <td align="center">
    159 (82.81%)
    </td>
    <td align="center">
    33 (17.19%)
    </td>
    </tr>
    <tr>
    <td align="center">
    9
    </td>
    <td align="left">
    lowincomeflag \[factor\]
    </td>
    <td align="left">
    1.  N
16. NAT
17. Y
    </td>
    <td align="left">
    102 (64.1%) 2 (1.3%) 55
    (34.6%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">
    </td>
    <td align="center">
    159 (82.81%)
    </td>
    <td align="center">
    33 (17.19%)
    </td>
    </tr>
    <tr>
    <td align="center">
    10
    </td>
    <td align="left">
    fulltimestatus \[factor\]
    </td>
    <td align="left">
    1.  Full-time
18. Part-time
    </td>
    <td align="left">
    93 (58.5%) 66
    (41.5%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGEAAAAhCAYAAADJXsXPAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAF2SURBVGgF7ZqxaoRAEIZ3cwtRrlBSJpVYaGeeIMmj2OVtLNRHSSHcKySkFyQ+QZpEUIia3SsHtnR2i3+rm7niG74f7mRWKfSp6/pZShmYzzj8BmTTNC9xHL8lSbLw40Gc5/mk9n0/p2n6VxTFHZTwG5imSdzwY0GkBhACNeKgRggOpFMkQqBGHNQIwYF0ikQI1IiDGiE4kE6RCIEacVAjBAfSKRIhUCMOaoTgQDpFKr09nYZhUNu2fdMvUR9vQHuX0mDatn3SBVbZxzsHwVcDsqqqhyiKLkEQ/Pg6JOdc+hdBrev6XpblKxdX6fOY5/l9lmURF9Rnjr5fEV3XKc4ZrzD95yzCMOTkestalkVoHxvngHhE5bRtYSEEixjONkLgtG1hIQSLGM42QuC0bWEhBIsYzjZC4LRtYSEEixjONkLgtG1hIQSLGM72dW1hdtrmnUgcIczuSC/wbjldmEudz77vv8Zx/OUEe8wydywfHs+H0Y4w8A9UzEvDChpiggAAAABJRU5ErkJggg==">
    </td>
    <td align="center">
    159 (82.81%)
    </td>
    <td align="center">
    33 (17.19%)
    </td>
    </tr>
    <tr>
    <td align="center">
    11
    </td>
    <td align="left">
    firstgenerationflag \[factor\]
    </td>
    <td align="left">
    1.  MDT
19. N
20. NAT
21. Y
    </td>
    <td align="left">
    7 (4.4%) 77 (48.4%) 2 (1.3%) 73
    (45.9%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">
    </td>
    <td align="center">
    159 (82.81%)
    </td>
    <td align="center">
    33 (17.19%)
    </td>
    </tr>
    <tr>
    <td align="center">
    12
    </td>
    <td align="left">
    homeprimarylang \[factor\]
    </td>
    <td align="left">
    1.  English only
22. English/non-English
23. Missing data
24. Non-English
    </td>
    <td align="left">
    37 (23.3%) 67 (42.1%) 2 (1.3%) 53
    (33.3%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">
    </td>
    <td align="center">
    159 (82.81%)
    </td>
    <td align="center">
    33 (17.19%)
    </td>
    </tr>
    <tr>
    <td align="center">
    13
    </td>
    <td align="left">
    admissionsstatusdetail \[factor\]
    </td>
    <td align="left">
    1.  Freshman
25. Not applicable
26. Transfer
    </td>
    <td align="left">
    151 (95.0%) 2 (1.3%) 6
    (3.8%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">
    </td>
    <td align="center">
    159 (82.81%)
    </td>
    <td align="center">
    33 (17.19%)
    </td>
    </tr>
    <tr>
    <td align="center">
    14
    </td>
    <td align="left">
    hsgpa \[numeric\]
    </td>
    <td align="left">
    mean (sd) : 4 (0.22) min \< med \< max : 3.16 \< 4.04 \< 4.4 IQR
    (CV) : 0.23 (0.06)
    </td>
    <td align="left">
    59 distinct
    values
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">
    </td>
    <td align="center">
    151 (78.65%)
    </td>
    <td align="center">
    41 (21.35%)
    </td>
    </tr>
    <tr>
    <td align="center">
    15
    </td>
    <td align="left">
    transfergpa \[numeric\]
    </td>
    <td align="left">
    mean (sd) : 3.33 (0.28) min \< med \< max : 3.01 \< 3.25 \< 3.71 IQR
    (CV) : 0.38 (0.08)
    </td>
    <td align="left">
    3.01 : 1 (16.7%) 3.14\! : 1 (16.7%) 3.22 : 1 (16.7%) 3.28 : 1
    (16.7%) 3.63\! : 1 (16.7%) 3.71 : 1 (16.7%) \!
    rounded
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">

</td>

<td align="center">

6 (3.12%)

</td>

<td align="center">

186 (96.88%)

</td>

</tr>

<tr>

<td align="center">

16

</td>

<td align="left">

gpacumulative \[logical\]

</td>

<td align="left">

</td>

<td align="left">

All NA’s

</td>

<td align="center" border="0">

</td>

<td align="center">

0 (0%)

</td>

<td align="center">

192 (100%)

</td>

</tr>

<tr>

<td align="center">

17

</td>

<td align="left">

firstregacadyr \[factor\]

</td>

<td align="left">

1.  2009-10
2.  2012-13
3.  2013-14
4.  2014-15
5.  2015-16
    </td>
    <td align="left">
    1 (0.6%) 5 (3.1%) 21 (13.2%) 109 (68.5%) 23
    (14.5%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">
    </td>
    <td align="center">
    159 (82.81%)
    </td>
    <td align="center">
    33 (17.19%)
    </td>
    </tr>
    <tr>
    <td align="center">
    18
    </td>
    <td align="left">
    firstregacadterm \[factor\]
    </td>
    <td align="left">
    1.  Fall
        </td>
        <td align="left">
        159
        (100.0%)
        </td>
        <td align="center" border="0">
        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGEAAAAQCAYAAAAGeBHHAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAACWSURBVFgJ7ZjBCcAgEAQ9CSHiwxICeUrAXtKZtpROLCA/X8IR0kRccG3AuRkOQck5n977O4TwGJ7fDfTe10VE9hijpJSO3wl4oWmtGUsP4w0wwvgG3ASABozACAgGABj4JjACgAEABG4CIwAYAEDgJjACgAEABG4CQITvA09rrZtzTgF4pkNQVSPf1KWUy1rrpzMAMvALfjkVAm1e7IYAAAAASUVORK5CYII=">
        </td>
        <td align="center">
        159 (82.81%)
        </td>
        <td align="center">
        33 (17.19%)
        </td>
        </tr>
        <tr>
        <td align="center">
        19
        </td>
        <td align="left">
        major1 \[factor\]
        </td>
        <td align="left">
        1.  Anthropology
6.  Art
7.  Art History
8.  Biological Sciences
9.  Biology/Education
10. Business Administration
11. Business Economics
12. Computer Game Science
13. Computer Science
14. Dance \[ 16 others \]
    </td>
    <td align="left">
    1 (0.6%) 2 (1.3%) 1 (0.6%) 89 (56.0%) 1 (0.6%) 1 (0.6%) 1 (0.6%) 6
    (3.8%) 5 (3.1%) 3 (1.9%) 49
    (30.8%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">
    </td>
    <td align="center">
    159 (82.81%)
    </td>
    <td align="center">
    33 (17.19%)
    </td>
    </tr>
    </tbody>
    </table>
    <p>
    Generated by
    <a href='https://github.com/dcomtois/summarytools'>summarytools</a>
    0.8.8 (<a href='https://www.r-project.org/'>R</a> version
    3.5.2)<br/>2019-06-25
    </p>
    </div>
    <!--/html_preserve-->
