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

    ## Output file written: /var/folders/vv/4z329kws7cz22bxhrvzc0mjh0000gp/T//RtmpFrT6mo/file17ab44db279e.html

<br><br>

Use these additional arguments to have the table display correctly when
knitting your R-Markdown

``` r
print(dfSummary(demog, graph.magnif = 0.40), method = 'render')
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
    
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAfCAYAAAC7xK7qAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAE/SURBVFgJ7di9ToUwFABgCoeIEowMxtzFyQcwcWLQMPkKOvMMvgcOzsB9B0YWHoDFV3CC6HYVy6/nGpvc5ZI43nNK0rRpu3w9TXuoYXD7six7SpJkzcUNlmXdCSGuuIBNxM7bwgbMBaqcpmpwqTWYeqTZRRi6rjvCsqIeWeWDpmkePM87Vh3Ua5Gm6TPew4+2bX/9YU0p5VsURbcU8YDQyzAML3zf//X1fW/keb6hiN2a2B1aGkx1KyuXjrBaCao1uwjDOI7vZVnWjuOoe1hg5iWpRljEcXwGANe7QLyLN/gS8r3bR6QtAROOF9d177G0RFB7GXVdn2Jw4SQIgnOVae2dTWCgqqoPdoeWBhPYuYsEHeHF5SEwCPjzL+Z5NoZhIMBZJkzTJACTjNeiKG7wIeBzefrhj7Zt6x2+4p+CHzoxUVys5Rf7AAAAAElFTkSuQmCC">
    
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
    
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAUCAYAAADRA14pAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAEVSURBVFgJ7Zg9DoJAEIV3lyURCcQzeAO1NJTcwkJs9QgehnALOztaaKg5AH8WSIDgOtFAYbHSOkLBDm+WhG8eyUyWep53JIQcGGMVrK+rbdsFBCfHca5vBc+dA6htWdZa07SBKkkS4vu+DcJ1EJEEHDgeiqIQXdcHpDzPCaVUDAKigCFiGYUyAY8q0w9vmhz+YfNGfTqHnjuPoqgyTbPr32iahvYxtpWnabory3L7CQa9+PKpYXimruuehRCOqqolBiAZQ13XOgfQDUxaS/ilZXtR5MIwTDm4K2C8JACOAkoGAdMjmdqSrEIYcpPDGFyUMfydw7zrOhYEwc0wjEZWGQy5OI5nPMuyfVEUKwxA3xjgoOP+BGpbTZnVvlQ9AAAAAElFTkSuQmCC">
    
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
    
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAUCAYAAADRA14pAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAADESURBVFgJ7dZNCsIwEAXg/ExRkGQruOwNpOuCa0+hZ3DrIbxBc6TmBrmAbVwo1JDqpNBLTDKbQHZf3kAeM8bcuq57sEwGcE7zPB8y8TKRoD+crMC5YJNzSbiACb9ASZhwuAsNpmnahxBq6tDVB+M4noUQm/WC+smxad3xG75WVfWmjsVt3gFCm7Zta601dS+z1j4htSxcaYZw8mDOeSke5FMuxYN6xNklDDFG0ff9Syn1pZ6uc24LwzBcvPdH6tjkk1J+/pv4OUN+8kvtAAAAAElFTkSuQmCC">
    
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
    
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAUCAYAAADRA14pAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAEVSURBVFgJ7Zg9DoJAEIV3lyURCcQzeAO1NJTcwkJs9QgehnALOztaaKg5AH8WSIDgOtFAYbHSOkLBDm+WhG8eyUyWep53JIQcGGMVrK+rbdsFBCfHca5vBc+dA6htWdZa07SBKkkS4vu+DcJ1EJEEHDgeiqIQXdcHpDzPCaVUDAKigCFiGYUyAY8q0w9vmhz+YfNGfTqHnjuPoqgyTbPr32iahvYxtpWnabory3L7CQa9+PKpYXimruuehRCOqqolBiAZQ13XOgfQDUxaS/ilZXtR5MIwTDm4K2C8JACOAkoGAdMjmdqSrEIYcpPDGFyUMfydw7zrOhYEwc0wjEZWGQy5OI5nPMuyfVEUKwxA3xjgoOP+BGpbTZnVvlQ9AAAAAElFTkSuQmCC">
    
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
    
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAfCAYAAAC7xK7qAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAGWSURBVFgJ7ZlBS4RAFMcdnYVNl2oPEXToGxREpz0sSIeOnTvX3YOH8GN06C546FMsgidP7qEvEBGhUimCWa469oK+wTzZYXcEj/Pz/d9fZv68UZQte4jneVbf97eaplVY2tu2XSVJcuU4ToHFxOJQVVUv5vP5qa7rWEwlDMPXPM+PACieYCiKgbsKpmDgMbTuIYNUZJ7wOClYeIs4C5QOczZQ+OW067p+uVzmk8lkhVVtmqa7lNIfLB4mh8ZxfFOW5QkmFJqYWZb1jMnEYhHXde8JIdej0QgtaWEVh82pqmqPgtBj0zQPp9MpNl84XhRFn3KXFs4W5IKkw8gNFQ4nHRbOEuSC/pLWRxAE6Xg83vhzGIYS+zTLsjuIgY/IjUTHNU1TQkB64wHDYKKlEDgeDMO4hPebBzb0WojAO0VRnNm2zSUazKX6bDY7ED1p+b7/Apmfe/Amd+mhf81186XD63Zg6O9vncMUzjYCVy0KXI8M3VwuPmOMcAH+F1M40J8Wi8U5DAK+MIBDMeq6Bs3sfSj+xnJ/AS+WfH7SCsOJAAAAAElFTkSuQmCC">
    
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
    
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA0CAYAAADWr1sfAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAKRSURBVGgF7ZrPi9pAFMcTHak/WqmVpeCtt+J1oUKLbg977H/Qk+utIPSSW/+EgmChZ+2f4MWDZ/Us2HpYe+mhpbarVGJi4o/0m0JgYWEhaN7LNpPLhGTmfd6PMPPyZhRFXv+3B9R2u605jnORSCRWVKau1+u0YRjn9Xr9OxXT4whcz8vl8tNMJuM9C7wdj8dXo9GoCBC9wYiuE4vFlGQyGbihHgA8x7unbmPUQG6eNJg7AkHzZYSD9jC3fLHf743BYPALy5JJpcxsNsvG4/HfVLzrHLXRaDzEMnF6/WHQ91j7re12+83j2LZ9pWkaSeIj8vn8eyjwKp1OG54ClO1ms0nouv4VzJcUXIHoPqpUKo9zuRwF7wYDaabS7XZ/3HgR0AM5Swfk2NCIlREOTSgCUiRyERauI/GHqOx2u4B8ertYl63iur3X8d4KJACfe73eM1Q89OOJ9SVJhbMvfY04oLPabDZP4OAXB8i4M0PxNekim81+KhQKZ2h5vmlCd02nU9WtaZnFYjHFlWkR2qu4OXvkZmlpMOUnxsGSEebwOiXTzbTipmkq+BGn5LKwFovFPbem9XE4HOpIPiwWLQihsNURyD5sGGsixRxVq9UPhHwWVAzVw7elUqmGUo/GogEx1J2ld+7OIQzeErNZcHJZYnE7IVRGmNDZLKjoRRjr7/3JZGLjkMkJi8uJoWK5XL5erVZnqCt9IWaz4NRWq/UO5AskICS7d8e0EhWMn7Va7dyPTIFq5SmOLT1BTcvPuFD07XQ6D/wq4ubS/44twXC/Y8PQ3/fxp+jN0mEIE6UOMsKU3uZgRS7C7mban36/P0ulUiyHWg6JsmVZvncdxXw+f4PtlsIhYK6xyBDnXOw7w/0LpaHE+G40dFEAAAAASUVORK5CYII=">
    
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
    
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAUCAYAAADRA14pAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAEgSURBVFgJ7Zg9boQwEIVtY6QQBF0ukBtkt1whpYmUQ2yxmzZwgxwGcYM9BD00tKGgNSIFf4sImZwAg+TVWIsbmufx9+YhPIJGUfRJCPlgjLXwnF193z81TfMeBMH3rBihgIPRN8/zdpZlSeEVRUHiOH4FsZ6GAfzXMAxi27aU4X+tzovpDL+GfTO8pms67dkS1imtNax8GIbHLMta13VHmQJd1zFKqdSdLVPv1houhDjWdX1YcrDv+5clekxaGobh1zRNZ9M0a0xgKlhgSrQ5GN3DpPUMr7SKM1DVTNNUcEh3gvGSgHFUcCpg4NtDtmtJRWcx1dwSxpSGCpa7S5iP48iSJPlxHOeqoqOYauZ5/sDLsjxVVfWCCUwVC/y8aP4AfyJMPJ3Tfv0AAAAASUVORK5CYII=">
    
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
print(dfSummary(demog2, graph.magnif = 0.40), method = 'render')
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
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAUCAYAAADRA14pAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAETSURBVFgJ7ZgxDoIwFIbbUhKRQPQK3kAdDaO3cBAnE6/gYQjH4BSgCTMXgOCAgATwgQMONcw8ywCvLz9Jv/c37Uup67oXQsiJMZbDt3tYVVU327bPnyGuNwfQvWVZG03TerK2bYnneQtcmAMNh7BRFIXout5nwV1CKW0GCa6I4cIZp5HA4zWatkI6PG3/xmfPYVeeh2GYm6ZZd/LuWCqKYjn+6zQVPI7jQ5Zlu+/pQxHu32NMMXUc5wqu2qqqZpjARCxlWeocQLfQaa1gSYs0qHJBEMQc3G2hvSQAjgpOBAMdJJHHkqgymHLSYUxuilj+zmFe1zXzff9hGMZLVBFMuSiKZjxJkmOapmtMYL9Y4KLj+QYM+VAnfTeVnQAAAABJRU5ErkJggg==">
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
        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAKCAYAAADo3z3CAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAACDSURBVEgN7dQxDoAgDAXQUohh4DqO7J7DyVM5cBfOwCWIYTKIBK2jHKGhS9N0ev1JhXNuA4BVSnlSZ12lFK0QcbHWzlpr1tgPF0I4FPVG6YIxhj2Ywn2QvbIDDnB3EHbjSJhdpB3o+9KYc4YYY7fiN6aUJlVr3b33N73six/xL2qtiRdzSCEQpxFxlwAAAABJRU5ErkJggg==">
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
            <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAKCAYAAADo3z3CAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAACDSURBVEgN7dQxDoAgDAXQUohh4DqO7J7DyVM5cBfOwCWIYTKIBK2jHKGhS9N0ev1JhXNuA4BVSnlSZ12lFK0QcbHWzlpr1tgPF0I4FPVG6YIxhj2Ywn2QvbIDDnB3EHbjSJhdpB3o+9KYc4YYY7fiN6aUJlVr3b33N73six/xL2qtiRdzSCEQpxFxlwAAAABJRU5ErkJggg==">
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
                <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAKCAYAAADo3z3CAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAACDSURBVEgN7dQxDoAgDAXQUohh4DqO7J7DyVM5cBfOwCWIYTKIBK2jHKGhS9N0ev1JhXNuA4BVSnlSZ12lFK0QcbHWzlpr1tgPF0I4FPVG6YIxhj2Ywn2QvbIDDnB3EHbjSJhdpB3o+9KYc4YYY7fiN6aUJlVr3b33N73six/xL2qtiRdzSCEQpxFxlwAAAABJRU5ErkJggg==">
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
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAfCAYAAAC7xK7qAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAFQSURBVFgJ7Zg/aoVAEMZ31xF8IoiV3YMcIHknECSnSCkJWCZd+hwgdwh2OYYXsPQCFvLgRTFIAv6JGVt5xYOVZHddwWLVGef3fbIzSMjGDpokyeM0TQ+GYXypzt513Q4YY7dBENzYtq06L8nzvAKk/EF3yRaAKaUTU97WBaAGXgii3FI7rJylCyAYx3HKsqx2HKdb3FNuWRTFDsqyvG/b9lo5ujNAwzB8g+/7L9if7kzTFH7S6vt+no7eoyh6OsNz0SVA0H0Yhr7neRcF/OdDdV2TNE33PDXoXZpHPRlitcMyuMRTo3aYRz0ZYudJ64Rb/dGyLOH7MNZq4PBw4hEWqqp6xsHjFX/zfPIk+qvYpmk+eN4Fruu+oWqHOI6veBLJEjtPWgwApHB3DVH1Lr2GiiLn0A6L7M4atW3PYey/FM/NgAP24HyGXuNz0TkEVOAX6l1hUcHmcr0AAAAASUVORK5CYII=">
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
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAfCAYAAAC7xK7qAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAFqSURBVFgJ7Zm9ToRAEMdhWUwOKKQwFxsba2isKGgsfBAtTUzgDXwCGp+Al6DhGSgkwc4GDY25a/AI3057Gzir5ZJhSTZkZjcz+5t/siy7krSyRw7D8GUcxydFUQ7Y2Zum2VBCyL3ruramadh5pSzLdhQoB1BXWgOwLMsjQS8rAyiAmYKgM4XC6CRlgGjf92OSJHvDMBqmD52Z5/mGFkXxWJalhY5uAqjruoput9vXqqqe67q2Pc/7mBiHykVUVb2xLOsA71tUZDMwYpWeKQwat1AYjZQzIELhmcKgcRPYaf2kaarBv+IXGqoTIHIQBJcAa0PbnRjHrQsKvvd9/5tbAiYwNU3zTdf1B2gV07eICVvbC0h0vUgySELh0RzHuQLwpXIe5Ymi6PPIwdkQqzTnAp89vFD47BJwnsDqFKbw/ZXhqkWC0wDOtZ0OPwzDokWnbdu+x3F8BwcAv9NT4uuF+x70d1p8K/hP9D+WSl6s6CHYsAAAAABJRU5ErkJggg==">
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
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAUCAYAAADRA14pAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAEXSURBVFgJ7ZbNCoJAEMfXdYVM9CQ9QG9QHUPo0lt0qE5BB68+j6/iC3jScx5FRTGRlG0br1IQiLRs7mXYr5n5zX9hVnJd94oQOmOMa7BCj7ZtZwRA95ZlrVVVFRq2gwvDMCNgn7IsI03ThAeWJIlh4Sl7gBNwryDCTSeFhZO0B0SgN82DIKgNw6C9PeGmURTNSJqmh6qqtsLRvQe6E9M0L4yxk6Io1fszfKw2TUPjON45jlMMyYgA6AZ+Wkt40kP8jH7X87xbWZYLCDQMGNRl8L1EAD560jwEmNoSDyqMmcOk8JjV5cH33ylMKKXY9/1C1/WGBwU+5ZAkSdc3H5/2v10nWZYd8zxffXvhV+egdSa2bUdD478AvaxOgxQgqcgAAAAASUVORK5CYII=">
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
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAApCAYAAABp50paAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAH8SURBVGgF7Vq9asJQFL433qBGwSoVHboWCh30CWpeoEPpAzjUjhY69A069QWKU8W9Y6HgJqWgKJRCZ+lQhUIGIzbW/PU4K2KK9yfkZrw593zf+b5wc3NuEIrYhVut1rXneReqqs541O66rur7/ku1Wr1igU9isdhJpVI5TqVSLPBWMEBs1G633ZUblAYIqOtD0SiZTFKC2Jx2Pp+jJYfNUbu7q+wuVTgyyYLD4dP/WUqH/69dOGYSx3F+u92ukU6nLR6U4bWEF4sFZoVNZrPZpWmah6wA1+GA6J/rxmmM4WazeU8IOYvH4z80AETKOZlMMlArKei6XshmsyJxo8JlMBgYcpWmIq1ASaXDAplBhYp0mIqsAiUl0HEYwgf4N6+OB0stLMvKkNFodAvbyicAHtbr9SFLAjywSLFYfMjn8/p4PHaAwD4PEiwxFXiUvXK5nEkkEiZLYF5YcpXmpTwrXOkwK6V54UTSYQU6Dsi2bY2X6ixxCfSUHjudzh6cPnywBOaFhRuNxpGiKOdAgNn5zq6KxRi/1Wq15yD5iKZpd6VS6RRaPUHmCRHb6/W+gMhBEDIEVHJyuRwKY0+r3+/bQYpdxkZylQ4qUqjjpcOhtm8L8pFzePnLAzEMA8ExxBb6iBUCLZvADQsynU5v4H32CpuPMG483sWyQEA2f5JRj65jFLjIAAAAAElFTkSuQmCC">
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
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAfCAYAAAC7xK7qAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAFGSURBVFgJ7Zk7boQwEEBtY4olEAmkFQXS3iBpQkOBkNJxgFwgW9DtHXKHnIA7JBXdKl1EkYILUNDk06Ag8Vln0qJFS+uxLVF4PJb85kmWNRCi2KB5nh+EEHvDMH6xs/d9v+GMsfs4jm8ty8LOS6qq+uZAeQK7RAVgSqlg6LXOADXwrCDoptowOqUzID5NkyjL8se27X62hm5a1/WGN03z2LbtDTq6M0DjOHbc9/0neIE8ZFkWnMlBF+Kmae7gtXVCR7YApG/phcKgCWvDaFQugGjDC4VBE2bw0vrsuu4KDdEFECNJkiNAv6Zp6jmO8wVdAXFhj9TLzHXd5yAIXjzPewPovdQ0Kw7POOdWFEXbMAyvIX+7Yo/UKfqWllrfisNrwyuKJHWKeoahOU3hVwv5/1QYfBiGj6Io7qAJ0EML5F0FaKUY/wDq/FSOEnswhAAAAABJRU5ErkJggg==">
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
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA0CAYAAADWr1sfAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAJeSURBVGgF7VpPa+JAHE2aSSXaFf9QCl6WvXoqFHtZtBePS79AwUMvZdfL4mG/QE9lC4LQHi2sn2LxqvgJiseiiweLmCqm2Y0m7hsPvXjIFEI6nUxgUMaXmffmxczLTxVFHoKvQLPZvES7Elzmizyi6/rRer3WX3oEf7MjuL4teVLw1pII1iEdFszQLTmRc5g4jhPDtrS7tRSCdqj1ej2lquoBmk0ImVar1YWgWjeySDabvYbQL7FY7O9sNntC76HIgndwZEql0kG5XP6I1CX8pR25m5YULPL3l2qTDkfCYQQPhbYoOE5Wq9V9u90+xpZkIXU9iO6w2mg09pGyPrMKXS6Xv2u1ms2K5w1Hksnkr1wud4JX14/ceDzWJ5NJA7gfflheP0eqJHY+nzfS6bQvx0wmo/R6Pc8XyDFAbkscmxMINelwIMvI8SCRc5jADM22bQX7q68vFOO67rt+Ziae591iq1kgfPzzVYyHDYi+Y8BxCyHI0A6tZ4Ghw8IyHo9/bbVaLFDuMLg6PaJp2vdCoXCKAMIdwaAJDQYDk6p0E4mEwpK0giYQ9nij0ciL3F1aCg77Mgt7Pulw2Cse9ny0xLPX7/edVCrlWwAIm1zQ8w2HQ4PM5/Mzy7JOgh6c0/EWtMRzAXLnCCAWC0lEyw8IKT8rlcoNC543zOZvS8Vi8ROEM3EzTVPpdDrHAL9PwcjSa/yCqKBMyyQYuZviNkVsphM4A8ltiTNDAqcjHQ58STkbMHIO06Q163a7j4ZhPLOYgaqBhmayYHnEkOl0+g1BIvcacjjnz2vwEvuGK/AfLYCseCfOutYAAAAASUVORK5CYII=">
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
        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAAKCAYAAADo3z3CAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAACDSURBVEgN7dQxDoAgDAXQUohh4DqO7J7DyVM5cBfOwCWIYTKIBK2jHKGhS9N0ev1JhXNuA4BVSnlSZ12lFK0QcbHWzlpr1tgPF0I4FPVG6YIxhj2Ywn2QvbIDDnB3EHbjSJhdpB3o+9KYc4YYY7fiN6aUJlVr3b33N73six/xL2qtiRdzSCEQpxFxlwAAAABJRU5ErkJggg==">
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
