R Workshop for Education Data Science Lesson 1
================
Fernando Rodriguez
1/10/2019

<br>

Table of Contents
-----------------

1.  Loading/Installing Libraries
2.  More workflow basics
    -   Navigating multiple R-Markdown files
    -   Commenting within chunks of code
3.  Values and Types
4.  Loading .csv data files
5.  Data transformation with dplyr
    -   Exploratory data analysis

``` r
knitr::opts_chunk$set(echo = TRUE, results = 'asis')
```

0. Loading Libraries
--------------------

First, let's load the libraries you will use for this lesson. This is the first thing you should do when writing an R-Markdown document. That way, you ensure that you load all of the necessary libraries prior to running code.

``` r
# install.libraries("dplyr") <- installing libraries require double qoutations 
library(ggplot2) # <- loading libraries doesn't require double qoutations
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

<br><br>

1. More workflow basics
-----------------------

Navigating Multiple Markdown Files
----------------------------------

You can have several R-Markdown files open. However, if you are using the same variable names across different R-Markdown files, These variables will get overritten.

We will learn more about how to manage differnt R-Markdown files and projects in later lessons

``` r
a <- 6
```

Commenting out text and code
----------------------------

Sometimes you want to leave a quick comment inside an r-chunk, or would simply like to comment out some code. You can do this by using `#`

``` r
# comment 
# 2 + 3
```

You can comment-out multiple lines of code by selecting the code and using<br> control + shift + c (windows and mac)<br> command + shift + c (mac)

``` r
ggplot(mtcars, aes(x = hp, y = mpg, color = mpg)) + 
 geom_point() + 
  theme(text = element_text(size = 20)) +
  labs(x = "Horsepower", y = "MPG") +
  scale_color_gradient(low = "red", high = "blue") +
  facet_grid(.~cyl)
```

![](Lesson_2_files/figure-markdown_github/unnamed-chunk-5-1.png)

Vales and Types
---------------

Operators
---------

Loading Data
------------

``` r
demodata <- read.csv("/Volumes/GoogleDrive/My Drive/R Workspace/R-for-Ed-Data-Science/Data/Physics Course Demo Data.csv", header = T)
```

Examine the data

``` r
demodata
```

    roster_randomid officialroster ingradebookdata insurveyparticipatedata

1 672849 Yes Yes Yes 2 872962 Yes Yes Yes 3 482931 Yes Yes Yes 4 455346 Yes Yes Yes 5 491579 Yes Yes Yes 6 608378 Yes Yes Yes 7 714417 Yes Yes Yes 8 508735 Yes Yes Yes 9 407162 Yes Yes Yes 10 529371 Yes Yes Yes 11 199241 Yes Yes Yes 12 682272
13 200213 Yes Yes Yes 14 104500 Yes Yes Yes 15 782325 Yes Yes Yes 16 663041 Yes Yes Yes 17 800759 Yes Yes Yes 18 701203 Yes Yes Yes 19 787480 Yes Yes Yes 20 649091 Yes Yes Yes 21 195967 NO Yes 22 807444 Yes Yes Yes 23 367621
24 235765 Yes Yes Yes 25 714591 Yes Yes Yes 26 689154 Yes Yes Yes 27 556811 Yes Yes Yes 28 141747 Yes Yes Yes 29 146863 Yes Yes Yes 30 653129 Yes Yes Yes 31 726750 Yes Yes Yes 32 180174 Yes Yes Yes 33 372017 Yes Yes Yes 34 231943 Yes Yes Yes 35 720875 Yes Yes Yes 36 728936 Yes Yes Yes 37 744067 Yes Yes Yes 38 507347 Yes Yes Yes 39 450617 Yes Yes Yes 40 703891 NO Yes 41 300495 Yes Yes Yes 42 197521 Yes Yes Yes 43 807647 Yes Yes Yes 44 214859 Yes Yes Yes 45 791363 Yes Yes Yes 46 261820 Yes Yes Yes 47 639104 NO Yes 48 105751 Yes Yes Yes 49 899347 Yes Yes Yes 50 701268 NO Yes 51 806308 Yes Yes Yes 52 698539 Yes Yes Yes 53 161048 Yes Yes Yes 54 660042 Yes Yes Yes 55 438171 Yes Yes Yes 56 531161 Yes Yes Yes 57 708793 Yes Yes Yes 58 806999 Yes Yes Yes 59 713290 Yes Yes Yes 60 295360 Yes Yes Yes 61 385563 Yes Yes Yes 62 575990 Yes Yes Yes 63 769969 Yes Yes Yes 64 663523 Yes Yes Yes 65 877457 Yes Yes Yes 66 367687 Yes Yes Yes 67 325700 Yes Yes Yes 68 948009 Yes Yes Yes 69 934386 Yes Yes Yes 70 498458 Yes Yes Yes 71 362123 Yes Yes Yes 72 168272 Yes Yes Yes 73 130996 Yes Yes Yes 74 832591 Yes Yes Yes 75 321628 Yes Yes Yes 76 885752 Yes Yes Yes 77 596216 Yes Yes Yes 78 147718 Yes Yes Yes 79 822133 Yes Yes Yes 80 614009 Yes Yes Yes 81 104716 Yes Yes Yes 82 178174 Yes Yes Yes 83 411700 Yes Yes Yes 84 677059 Yes Yes Yes 85 887445 NO Yes 86 571608 Yes Yes Yes 87 592464 Yes Yes Yes 88 346931 Yes Yes Yes 89 480786 Yes Yes Yes 90 620376 Yes Yes Yes 91 673701 Yes Yes Yes 92 307656 Yes Yes Yes 93 370442 NO Yes 94 557446 Yes Yes Yes 95 548808 Yes Yes Yes 96 692379 Yes Yes Yes 97 780207 Yes Yes Yes 98 861427 Yes Yes Yes 99 538148 Yes Yes Yes 100 182504 Yes Yes Yes 101 836257 Yes Yes Yes 102 334953 Yes Yes Yes 103 237519 Yes Yes Yes 104 453902 Yes Yes Yes 105 803390 NO Yes 106 400323 Yes Yes Yes 107 761623 Yes Yes Yes 108 243861 Yes Yes Yes 109 183679 NO Yes 110 589476 Yes Yes Yes 111 712741 Yes Yes Yes 112 667648 Yes Yes Yes 113 177681 Yes Yes Yes 114 304461 Yes Yes Yes 115 170223 Yes Yes Yes 116 364842 Yes Yes Yes 117 462383 Yes Yes Yes 118 409639 Yes Yes Yes 119 626999 NO Yes 120 568332 Yes Yes Yes 121 591403 Yes Yes Yes 122 663501 Yes Yes Yes 123 170432 Yes Yes Yes 124 814796 Yes Yes Yes 125 143914 Yes Yes Yes 126 774095 Yes Yes Yes 127 331387 Yes Yes Yes 128 204748 Yes Yes Yes 129 432697 Yes Yes Yes 130 235637 NO Yes 131 843351 Yes Yes Yes 132 205399 Yes Yes Yes 133 691384 Yes Yes Yes 134 299868 Yes Yes Yes 135 371246 Yes Yes Yes 136 865397 Yes Yes Yes 137 698338 Yes Yes Yes 138 345089 Yes Yes Yes 139 764174 Yes Yes Yes 140 518321 Yes Yes Yes 141 140533 Yes Yes Yes 142 571486 Yes Yes Yes 143 175489 Yes Yes Yes 144 276402 Yes Yes Yes 145 618201 Yes Yes Yes 146 744130 Yes Yes Yes 147 963766 Yes Yes Yes 148 782702 Yes Yes Yes 149 866922 Yes Yes Yes 150 183023 Yes Yes Yes 151 735668 Yes Yes Yes 152 438165 Yes Yes Yes 153 637773 NO Yes 154 358425 Yes Yes Yes 155 804794 Yes Yes Yes 156 666223 Yes Yes Yes 157 133180 Yes Yes Yes 158 145670 Yes Yes Yes 159 663491 Yes Yes Yes 160 334203 Yes Yes Yes 161 319665 NO Yes 162 340310 Yes Yes Yes 163 429492 Yes Yes Yes 164 827276 Yes Yes Yes 165 321917 Yes Yes Yes 166 106707 Yes Yes Yes 167 578062 Yes Yes Yes 168 777294 Yes Yes Yes 169 600673 Yes Yes Yes 170 288266 Yes Yes Yes 171 351132 Yes Yes Yes 172 994588 Yes Yes Yes 173 831333 Yes Yes Yes 174 281031 Yes Yes Yes 175 198967 Yes Yes Yes 176 141925 Yes Yes Yes 177 640414 Yes Yes Yes 178 825174 NO Yes 179 499769 Yes Yes Yes 180 627410 Yes Yes Yes 181 888382 Yes Yes Yes 182 667020 Yes Yes Yes 183 219450 Yes Yes Yes 184 696499 Yes Yes Yes 185 331128 NO Yes 186 475486 Yes Yes Yes 187 645994 Yes Yes Yes 188 149531 Yes Yes Yes 189 238015 Yes Yes Yes 190 215400 Yes Yes Yes 191 855257 Yes Yes Yes 192 351821 Yes Yes Yes status gender eth2009rollupforreporting agegroup lowincomeflag 1 Enrolled Male International student 20 N 2 Enrolled Male Asian / Pacific Islander 20 N 3 Enrolled Male White, non-Hispanic 24 N 4 Enrolled Male Asian / Pacific Islander 19 N 5 Enrolled Female Asian / Pacific Islander 20 Y 6 Enrolled Female Hispanic 19 N 7 Enrolled Male Asian / Pacific Islander 20 N 8 Enrolled Female Asian / Pacific Islander 19 N 9 Enrolled Male Unknown / declined to state 20 N 10 Enrolled Male Asian / Pacific Islander 19 Y 11 Enrolled Male Hispanic 19 N 12 Male Asian / Pacific Islander 22 N 13 Enrolled Female Asian / Pacific Islander 18 N 14 Enrolled Male Hispanic 19 Y 15 Enrolled Female Asian / Pacific Islander 19 Y 16 Enrolled Female Unknown / declined to state 19 N 17 Enrolled Male Asian / Pacific Islander 18 Y 18 Enrolled Male Hispanic 22 N 19 Enrolled Male International student 20 N 20 Enrolled Female Asian / Pacific Islander 20 N 21
22 Enrolled Male Asian / Pacific Islander 19 N 23
24 Enrolled
25 Enrolled Male Asian / Pacific Islander 20 Y 26 Enrolled
27 Enrolled Female Hispanic 19 Y 28 Enrolled Male International student 20 N 29 Enrolled Female Asian / Pacific Islander 21 Y 30 Enrolled Male Unknown / declined to state 19 Y 31 Enrolled Female Asian / Pacific Islander 19 N 32 Enrolled
33 Enrolled Female Asian / Pacific Islander 20 Y 34 Enrolled
35 Enrolled
36 Enrolled Female Asian / Pacific Islander 19 N 37 Enrolled Female Asian / Pacific Islander 20 N 38 Enrolled Female Asian / Pacific Islander 20 N 39 Enrolled Female Asian / Pacific Islander 20 N 40
41 Enrolled Female Asian / Pacific Islander 22 N 42 Enrolled Female Asian / Pacific Islander 20 N 43 Enrolled Male Asian / Pacific Islander 20 Y 44 Enrolled Male Asian / Pacific Islander 19 Y 45 Enrolled Male White, non-Hispanic 20 N 46 Enrolled Male Asian / Pacific Islander 19 N 47 Female International student 19 N 48 Enrolled Female Asian / Pacific Islander 19 Y 49 Enrolled Female Asian / Pacific Islander 21 Y 50 Female Asian / Pacific Islander 19 N 51 Enrolled Female Asian / Pacific Islander 19 N 52 Enrolled Female Hispanic 19 N 53 Enrolled Male Asian / Pacific Islander 20 N 54 Enrolled Male Asian / Pacific Islander 20 N 55 Enrolled Female Asian / Pacific Islander 20 Y 56 Enrolled Female Asian / Pacific Islander 19 N 57 Enrolled Female Asian / Pacific Islander 21 N 58 Enrolled
59 Enrolled Male Asian / Pacific Islander 21 N 60 Enrolled Female International student 20 N 61 Enrolled Male International student 19 Y 62 Enrolled Female Hispanic 19 Y 63 Enrolled Female White, non-Hispanic 20 N 64 Enrolled Male Asian / Pacific Islander 21 N 65 Enrolled Female Hispanic 20 N 66 Enrolled Female White, non-Hispanic 20 N 67 Enrolled Male Asian / Pacific Islander 18 N 68 Enrolled Female Hispanic 20 Y 69 Enrolled Male Hispanic 19 N 70 Enrolled Female Asian / Pacific Islander 19 N 71 Enrolled Male Asian / Pacific Islander 18 N 72 Enrolled Male Asian / Pacific Islander 20 N 73 Enrolled Male Unknown / declined to state 22 Y 74 Enrolled
75 Enrolled Male Asian / Pacific Islander 19 Y 76 Enrolled
77 Enrolled Female Asian / Pacific Islander 20 N 78 Enrolled Male Hispanic 19 Y 79 Enrolled Male Unknown / declined to state 25-29 NAT 80 Enrolled Male Asian / Pacific Islander 20 N 81 Enrolled Male Asian / Pacific Islander 19 N 82 Enrolled Male Asian / Pacific Islander 20 Y 83 Enrolled Male Asian / Pacific Islander 20 N 84 Enrolled Male Asian / Pacific Islander 19 N 85
86 Enrolled Female Asian / Pacific Islander 21 N 87 Enrolled Male Asian / Pacific Islander 20 N 88 Enrolled Male Asian / Pacific Islander 20 Y 89 Enrolled Female Asian / Pacific Islander 21 N 90 Enrolled Female White, non-Hispanic 21 N 91 Enrolled Female Asian / Pacific Islander 21 Y 92 Enrolled
93
94 Enrolled Female Asian / Pacific Islander 19 N 95 Enrolled Female Asian / Pacific Islander 21 Y 96 Enrolled Female Asian / Pacific Islander 19 Y 97 Enrolled Female Asian / Pacific Islander 19 N 98 Enrolled Female Hispanic 19 Y 99 Enrolled Male Asian / Pacific Islander 19 N 100 Enrolled
101 Enrolled Female Asian / Pacific Islander 20 N 102 Enrolled Female Asian / Pacific Islander 20 Y 103 Enrolled
104 Enrolled Male Asian / Pacific Islander 20 N 105
106 Enrolled Female Asian / Pacific Islander 19 N 107 Enrolled Female Hispanic 21 N 108 Enrolled Female Asian / Pacific Islander 19 Y 109
110 Enrolled Male Asian / Pacific Islander 20 N 111 Enrolled Male Unknown / declined to state 19 N 112 Enrolled Female International student 19 N 113 Enrolled Male Asian / Pacific Islander 20 N 114 Enrolled Female Asian / Pacific Islander 20 N 115 Enrolled Female Asian / Pacific Islander 19 N 116 Enrolled Female Hispanic 19 N 117 Enrolled Male International student 19 N 118 Enrolled Female Unknown / declined to state 19 Y 119
120 Enrolled Male Unknown / declined to state 19 N 121 Enrolled Female Hispanic 20 Y 122 Enrolled Female Hispanic 21 Y 123 Enrolled Female Asian / Pacific Islander 19 Y 124 Enrolled Female White, non-Hispanic 19 N 125 Enrolled Female White, non-Hispanic 19 N 126 Enrolled
127 Enrolled Female Asian / Pacific Islander 22 N 128 Enrolled Male Asian / Pacific Islander 19 Y 129 Enrolled Female Asian / Pacific Islander 19 N 130
131 Enrolled
132 Enrolled Female White, non-Hispanic 21 N 133 Enrolled Female International student 20 N 134 Enrolled Male Asian / Pacific Islander 20 N 135 Enrolled
136 Enrolled Female Asian / Pacific Islander 21 Y 137 Enrolled Female Asian / Pacific Islander 21 NAT 138 Enrolled Male Asian / Pacific Islander 20 N 139 Enrolled Female International student 20 Y 140 Enrolled Female Asian / Pacific Islander 19 N 141 Enrolled Male Asian / Pacific Islander 19 Y 142 Enrolled Female Asian / Pacific Islander 19 N 143 Enrolled
144 Enrolled Male Asian / Pacific Islander 20 N 145 Enrolled Male Unknown / declined to state 20 N 146 Enrolled Female Asian / Pacific Islander 19 N 147 Enrolled Female Unknown / declined to state 20 N 148 Enrolled Female White, non-Hispanic 19 N 149 Enrolled
150 Enrolled Male Asian / Pacific Islander 18 N 151 Enrolled Not stated White, non-Hispanic 20 Y 152 Enrolled Male Hispanic 20 N 153
154 Enrolled Female Asian / Pacific Islander 19 Y 155 Enrolled Female Asian / Pacific Islander 20 N 156 Enrolled Female White, non-Hispanic 19 Y 157 Enrolled Female Asian / Pacific Islander 20 N 158 Enrolled Female Asian / Pacific Islander 20 Y 159 Enrolled Female Asian / Pacific Islander 20 Y 160 Enrolled Female Asian / Pacific Islander 20 N 161
162 Enrolled Female Asian / Pacific Islander 20 Y 163 Enrolled Male Unknown / declined to state 19 Y 164 Enrolled Male Asian / Pacific Islander 19 N 165 Enrolled Male Asian / Pacific Islander 20 Y 166 Enrolled Female Asian / Pacific Islander 23 Y 167 Enrolled Female Asian / Pacific Islander 20 Y 168 Enrolled Female Unknown / declined to state 22 Y 169 Enrolled Female Asian / Pacific Islander 20 Y 170 Enrolled Female Asian / Pacific Islander 19 Y 171 Enrolled Male Asian / Pacific Islander 20 N 172 Enrolled Male Asian / Pacific Islander 20 Y 173 Enrolled Female Hispanic 20 Y 174 Enrolled Male Asian / Pacific Islander 18 Y 175 Enrolled
176 Enrolled Female Unknown / declined to state 20 N 177 Enrolled Female Asian / Pacific Islander 19 Y 178
179 Enrolled Male International student 20 N 180 Enrolled Female Asian / Pacific Islander 25-29 N 181 Enrolled Male Asian / Pacific Islander 21 N 182 Enrolled Female International student 20 N 183 Enrolled
184 Enrolled Female Asian / Pacific Islander 20 Y 185
186 Enrolled Female Asian / Pacific Islander 20 N 187 Enrolled Female International student 20 N 188 Enrolled Male International student 21 N 189 Enrolled
190 Enrolled Male International student 20 N 191 Enrolled Male Asian / Pacific Islander 20 N 192 Enrolled
fulltimestatus firstgenerationflag homeprimarylang 1 Part-time N English/non-English 2 Part-time N English only 3 Part-time Y Non-English 4 Full-time Y English only 5 Full-time Y Non-English 6 Full-time Y English only 7 Full-time N English/non-English 8 Part-time Y English only 9 Full-time Y Non-English 10 Part-time Y English/non-English 11 Full-time N Non-English 12 Full-time N English/non-English 13 Full-time Y English/non-English 14 Full-time N English/non-English 15 Full-time Y English/non-English 16 Part-time N English/non-English 17 Part-time Y English/non-English 18 Full-time Y English only 19 Full-time N Non-English 20 Part-time Y English/non-English 21
22 Part-time N English/non-English 23
24
25 Full-time N English/non-English 26
27 Part-time Y English/non-English 28 Part-time N Non-English 29 Full-time Y English/non-English 30 Part-time N English only 31 Part-time N English/non-English 32
33 Full-time MDT English/non-English 34
35
36 Full-time Y Non-English 37 Full-time N English/non-English 38 Part-time N English only 39 Part-time N Non-English 40
41 Full-time MDT English/non-English 42 Full-time N English/non-English 43 Part-time Y English only 44 Full-time Y English/non-English 45 Full-time N English/non-English 46 Full-time Y Non-English 47 Part-time N Non-English 48 Part-time Y English/non-English 49 Full-time Y Non-English 50 Part-time N English/non-English 51 Full-time N English only 52 Full-time Y English/non-English 53 Part-time Y English/non-English 54 Full-time MDT English/non-English 55 Full-time Y Non-English 56 Part-time Y English/non-English 57 Part-time N English/non-English 58
59 Full-time Y Non-English 60 Part-time Y Non-English 61 Full-time N Non-English 62 Part-time Y Non-English 63 Part-time N English only 64 Full-time N English/non-English 65 Full-time Y English only 66 Full-time N Non-English 67 Full-time Y English/non-English 68 Full-time N English/non-English 69 Part-time N English only 70 Full-time Y Non-English 71 Part-time N Non-English 72 Full-time N English/non-English 73 Part-time Y Non-English 74
75 Part-time Y Non-English 76
77 Full-time N Non-English 78 Part-time MDT Non-English 79 Part-time NAT Missing data 80 Full-time N English/non-English 81 Part-time N English only 82 Full-time Y English/non-English 83 Full-time Y English only 84 Part-time N English/non-English 85
86 Full-time Y English only 87 Full-time Y English/non-English 88 Full-time Y English/non-English 89 Full-time N English only 90 Full-time N English/non-English 91 Full-time Y English only 92
93
94 Full-time N English only 95 Full-time Y English/non-English 96 Full-time Y English/non-English 97 Full-time N English/non-English 98 Full-time Y Non-English 99 Part-time N English only 100
101 Part-time N English/non-English 102 Full-time Y Non-English 103
104 Part-time N English/non-English 105
106 Full-time N Non-English 107 Full-time Y English/non-English 108 Full-time Y English/non-English 109
110 Full-time Y English only 111 Full-time N English only 112 Full-time Y Non-English 113 Part-time Y English only 114 Full-time N Non-English 115 Part-time N English/non-English 116 Full-time Y English only 117 Part-time N Non-English 118 Part-time Y Non-English 119
120 Full-time N English/non-English 121 Part-time Y Non-English 122 Part-time Y Non-English 123 Part-time N Non-English 124 Full-time N English/non-English 125 Full-time N English only 126
127 Full-time MDT English/non-English 128 Part-time Y English/non-English 129 Part-time N English only 130
131
132 Full-time N English only 133 Part-time MDT Non-English 134 Full-time N English/non-English 135
136 Full-time Y English/non-English 137 Part-time NAT Missing data 138 Full-time N Non-English 139 Part-time N English/non-English 140 Full-time N English only 141 Part-time Y Non-English 142 Full-time N English only 143
144 Full-time N English only 145 Part-time N Non-English 146 Full-time N Non-English 147 Full-time N English/non-English 148 Part-time N English only 149
150 Full-time N English/non-English 151 Full-time N English only 152 Part-time N English only 153
154 Full-time N English/non-English 155 Part-time N Non-English 156 Part-time Y Non-English 157 Part-time Y English/non-English 158 Part-time Y English only 159 Full-time Y English/non-English 160 Part-time Y English only 161
162 Full-time Y Non-English 163 Full-time Y Non-English 164 Part-time N English only 165 Full-time Y English/non-English 166 Part-time Y English/non-English 167 Full-time Y English/non-English 168 Full-time Y Non-English 169 Full-time Y Non-English 170 Part-time Y English/non-English 171 Part-time Y Non-English 172 Full-time MDT English/non-English 173 Full-time N English/non-English 174 Part-time Y English only 175
176 Part-time N English/non-English 177 Full-time Y Non-English 178
179 Full-time N Non-English 180 Full-time Y Non-English 181 Part-time N Non-English 182 Part-time Y Non-English 183
184 Full-time Y Non-English 185
186 Full-time N English only 187 Full-time N Non-English 188 Part-time N Non-English 189
190 Full-time N English/non-English 191 Full-time N English/non-English 192
admissionsstatusdetail hsgpa transfergpa gpacumulative firstregacadyr 1 Freshman 4.18 NA NA 2014-15 2 Freshman 4.00 NA NA 2013-14 3 Transfer NA 3.22 NA 2015-16 4 Freshman 4.04 NA NA 2015-16 5 Freshman 4.14 NA NA 2014-15 6 Freshman 4.33 NA NA 2014-15 7 Freshman 4.20 NA NA 2014-15 8 Freshman 4.22 NA NA 2014-15 9 Freshman 4.27 NA NA 2014-15 10 Freshman 4.25 NA NA 2014-15 11 Freshman 4.05 NA NA 2014-15 12 Freshman 4.00 NA NA 2012-13 13 Freshman 3.30 NA NA 2015-16 14 Freshman 4.00 NA NA 2014-15 15 Freshman 4.04 NA NA 2014-15 16 Freshman 4.13 NA NA 2014-15 17 Freshman 3.83 NA NA 2015-16 18 Freshman 3.60 NA NA 2012-13 19 Freshman 3.99 NA NA 2015-16 20 Freshman 4.06 NA NA 2014-15 21 NA NA NA
22 Freshman 4.00 NA NA 2014-15 23 NA NA NA
24 NA NA NA
25 Freshman 3.91 NA NA 2014-15 26 NA NA NA
27 Freshman 4.09 NA NA 2014-15 28 Freshman 3.78 NA NA 2014-15 29 Freshman 3.88 NA NA 2013-14 30 Freshman 3.52 NA NA 2014-15 31 Freshman 4.00 NA NA 2014-15 32 NA NA NA
33 Freshman 3.87 NA NA 2014-15 34 NA NA NA
35 NA NA NA
36 Freshman 4.36 NA NA 2014-15 37 Freshman 4.00 NA NA 2014-15 38 Freshman 4.18 NA NA 2014-15 39 Freshman 4.18 NA NA 2014-15 40 NA NA NA
41 Freshman 4.18 NA NA 2012-13 42 Freshman 4.07 NA NA 2014-15 43 Freshman 4.18 NA NA 2014-15 44 Freshman 4.00 NA NA 2014-15 45 Freshman 4.04 NA NA 2014-15 46 Freshman 4.08 NA NA 2014-15 47 Freshman 3.78 NA NA 2015-16 48 Freshman 3.95 NA NA 2014-15 49 Freshman 4.00 NA NA 2013-14 50 Freshman 4.40 NA NA 2014-15 51 Freshman 4.11 NA NA 2015-16 52 Freshman 4.00 NA NA 2014-15 53 Freshman 4.09 NA NA 2014-15 54 Freshman 4.26 NA NA 2014-15 55 Freshman 4.08 NA NA 2015-16 56 Freshman 4.27 NA NA 2014-15 57 Freshman 4.00 NA NA 2013-14 58 NA NA NA
59 Freshman 4.00 NA NA 2013-14 60 Freshman 4.07 NA NA 2014-15 61 Freshman 4.00 NA NA 2015-16 62 Freshman 4.04 NA NA 2014-15 63 Freshman 3.16 NA NA 2013-14 64 Freshman 4.18 NA NA 2013-14 65 Freshman 4.29 NA NA 2014-15 66 Freshman 4.04 NA NA 2013-14 67 Freshman 4.30 NA NA 2015-16 68 Freshman 4.04 NA NA 2014-15 69 Freshman 3.29 NA NA 2014-15 70 Freshman 4.00 NA NA 2014-15 71 Freshman 3.85 NA NA 2015-16 72 Freshman 4.00 NA NA 2014-15 73 Transfer NA 3.14 NA 2015-16 74 NA NA NA
75 Freshman 4.22 NA NA 2014-15 76 NA NA NA
77 Freshman 4.09 NA NA 2014-15 78 Freshman 4.17 NA NA 2014-15 79 Not applicable NA NA NA 2009-10 80 Freshman 4.20 NA NA 2014-15 81 Freshman 4.07 NA NA 2014-15 82 Freshman 3.39 NA NA 2014-15 83 Freshman 3.81 NA NA 2014-15 84 Freshman 4.00 NA NA 2014-15 85 NA NA NA
86 Freshman 4.15 NA NA 2013-14 87 Freshman 4.36 NA NA 2014-15 88 Freshman 3.85 NA NA 2014-15 89 Freshman 3.86 NA NA 2013-14 90 Freshman 3.90 NA NA 2013-14 91 Freshman 4.09 NA NA 2013-14 92 NA NA NA
93 NA NA NA
94 Freshman 4.05 NA NA 2014-15 95 Freshman 4.00 NA NA 2013-14 96 Freshman 3.80 NA NA 2014-15 97 Freshman 4.00 NA NA 2014-15 98 Freshman 3.65 NA NA 2015-16 99 Freshman 4.22 NA NA 2015-16 100 NA NA NA
101 Freshman 4.25 NA NA 2014-15 102 Freshman 3.69 NA NA 2013-14 103 NA NA NA
104 Freshman 3.90 NA NA 2014-15 105 NA NA NA
106 Freshman 3.86 NA NA 2014-15 107 Freshman 3.95 NA NA 2013-14 108 Freshman 3.79 NA NA 2015-16 109 NA NA NA
110 Freshman 3.91 NA NA 2014-15 111 Freshman 4.30 NA NA 2015-16 112 Freshman 3.36 NA NA 2014-15 113 Freshman 4.35 NA NA 2014-15 114 Freshman 3.92 NA NA 2014-15 115 Freshman 4.00 NA NA 2014-15 116 Freshman 4.12 NA NA 2014-15 117 Freshman 4.00 NA NA 2014-15 118 Freshman 4.00 NA NA 2014-15 119 NA NA NA
120 Freshman 3.95 NA NA 2014-15 121 Freshman 4.22 NA NA 2014-15 122 Freshman 4.04 NA NA 2013-14 123 Freshman 4.00 NA NA 2014-15 124 Freshman 4.25 NA NA 2015-16 125 Freshman 4.15 NA NA 2015-16 126 NA NA NA
127 Transfer NA 3.71 NA 2015-16 128 Freshman 3.91 NA NA 2014-15 129 Freshman 3.95 NA NA 2014-15 130 NA NA NA
131 NA NA NA
132 Freshman 4.21 NA NA 2013-14 133 Freshman 3.85 NA NA 2015-16 134 Freshman 4.00 NA NA 2014-15 135 NA NA NA
136 Freshman 3.95 NA NA 2013-14 137 Not applicable NA NA NA 2012-13 138 Freshman 3.91 NA NA 2014-15 139 Freshman 4.13 NA NA 2014-15 140 Freshman 4.31 NA NA 2014-15 141 Freshman 4.04 NA NA 2014-15 142 Freshman 4.26 NA NA 2014-15 143 NA NA NA
144 Freshman 4.05 NA NA 2014-15 145 Freshman 4.13 NA NA 2014-15 146 Freshman 4.19 NA NA 2014-15 147 Freshman 4.08 NA NA 2014-15 148 Freshman 4.04 NA NA 2014-15 149 NA NA NA
150 Freshman 4.10 NA NA 2015-16 151 Freshman 3.70 NA NA 2014-15 152 Freshman 3.71 NA NA 2014-15 153 NA NA NA
154 Freshman 4.00 NA NA 2014-15 155 Freshman 4.00 NA NA 2014-15 156 Freshman 3.90 NA NA 2014-15 157 Freshman 4.08 NA NA 2014-15 158 Freshman 4.08 NA NA 2014-15 159 Freshman 4.00 NA NA 2013-14 160 Freshman 4.30 NA NA 2014-15 161 NA NA NA
162 Freshman 4.09 NA NA 2014-15 163 Freshman 3.77 NA NA 2014-15 164 Freshman 3.70 NA NA 2014-15 165 Freshman 4.17 NA NA 2014-15 166 Transfer NA 3.28 NA 2014-15 167 Freshman 3.76 NA NA 2013-14 168 Freshman 3.77 NA NA 2012-13 169 Freshman 3.90 NA NA 2014-15 170 Freshman 3.80 NA NA 2014-15 171 Freshman 4.09 NA NA 2014-15 172 Freshman 4.17 NA NA 2014-15 173 Freshman 3.95 NA NA 2014-15 174 Freshman 4.18 NA NA 2015-16 175 NA NA NA
176 Freshman 4.18 NA NA 2014-15 177 Freshman 4.07 NA NA 2014-15 178 NA NA NA
179 Freshman 3.55 NA NA 2014-15 180 Transfer NA 3.01 NA 2013-14 181 Freshman 4.06 NA NA 2014-15 182 Freshman 4.05 NA NA 2014-15 183 NA NA NA
184 Freshman 3.95 NA NA 2014-15 185 NA NA NA
186 Freshman 4.09 NA NA 2014-15 187 Freshman 3.96 NA NA 2014-15 188 Freshman 3.42 NA NA 2014-15 189 NA NA NA
190 Freshman 3.60 NA NA 2014-15 191 Transfer NA 3.63 NA 2015-16 192 NA NA NA
firstregacadterm major1 1 Fall Biological Sciences 2 Fall Biological Sciences 3 Fall Psychology 4 Fall Education Sciences 5 Fall Biological Sciences 6 Fall Public Health Sciences 7 Fall Biological Sciences 8 Fall Biological Sciences 9 Fall Biological Sciences 10 Fall Biological Sciences 11 Fall Computer Game Science 12 Fall Political Science 13 Fall Dance 14 Fall Biological Sciences 15 Fall Pharmaceutical Sciences 16 Fall Biological Sciences 17 Fall Biological Sciences 18 Fall Sociology 19 Fall Earth System Science 20 Fall Biological Sciences 21
22 Fall Biological Sciences 23
24
25 Fall Biological Sciences 26
27 Fall Biological Sciences 28 Fall Biological Sciences 29 Fall Social Policy and Public Servi 30 Fall Pharmaceutical Sciences 31 Fall Pharmaceutical Sciences 32
33 Fall Biological Sciences 34
35
36 Fall Pharmaceutical Sciences 37 Fall Biological Sciences 38 Fall Psychology and Social Behavior 39 Fall Biological Sciences 40
41 Fall History 42 Fall Biological Sciences 43 Fall Biological Sciences 44 Fall Biological Sciences 45 Fall Biological Sciences 46 Fall Biological Sciences 47 Fall Biological Sciences 48 Fall Biological Sciences 49 Fall Biological Sciences 50 Fall Biological Sciences 51 Fall Biological Sciences 52 Fall Pharmaceutical Sciences 53 Fall Computer Science 54 Fall Pharmaceutical Sciences 55 Fall Biology/Education 56 Fall Biological Sciences 57 Fall Biological Sciences 58
59 Fall Biological Sciences 60 Fall Biological Sciences 61 Fall Computer Game Science 62 Fall Biological Sciences 63 Fall Dance 64 Fall Pharmaceutical Sciences 65 Fall Biological Sciences 66 Fall Public Health Sciences 67 Fall Software Engineering 68 Fall Biological Sciences 69 Fall Biological Sciences 70 Fall Pharmaceutical Sciences 71 Fall Undeclared 72 Fall Biological Sciences 73 Fall Biological Sciences 74
75 Fall Pharmaceutical Sciences 76
77 Fall Pharmaceutical Sciences 78 Fall Undeclared 79 Fall Pharmacology and Toxicology 80 Fall Biological Sciences 81 Fall Pharmaceutical Sciences 82 Fall Biological Sciences 83 Fall Biological Sciences 84 Fall Biological Sciences 85
86 Fall Computer Game Science 87 Fall Biological Sciences 88 Fall Pharmaceutical Sciences 89 Fall Psychology and Social Behavior 90 Fall Social Ecology 91 Fall Public Health Sciences 92
93
94 Fall Pharmaceutical Sciences 95 Fall Biological Sciences 96 Fall Biological Sciences 97 Fall Biological Sciences 98 Fall Spanish 99 Fall Computer Game Science 100
101 Fall Biological Sciences 102 Fall Biological Sciences 103
104 Fall Biological Sciences 105
106 Fall Biological Sciences 107 Fall Political Science 108 Fall Pharmaceutical Sciences 109
110 Fall Biological Sciences 111 Fall Computer Game Science 112 Fall Environmental Science 113 Fall Biological Sciences 114 Fall Biological Sciences 115 Fall Biological Sciences 116 Fall Biological Sciences 117 Fall Computer Science 118 Fall Biological Sciences 119
120 Fall Biological Sciences 121 Fall Biological Sciences 122 Fall Psychology 123 Fall Biological Sciences 124 Fall Art History 125 Fall Anthropology 126
127 Fall Pharmaceutical Sciences 128 Fall Pharmaceutical Sciences 129 Fall Biological Sciences 130
131
132 Fall Computer Game Science 133 Fall Art 134 Fall Biological Sciences 135
136 Fall Public Health Sciences 137 Fall Biological Sciences 138 Fall Computer Science 139 Fall Biological Sciences 140 Fall Biological Sciences 141 Fall Biological Sciences 142 Fall Pharmaceutical Sciences 143
144 Fall Biological Sciences 145 Fall Biological Sciences 146 Fall Biological Sciences 147 Fall Biological Sciences 148 Fall Pharmaceutical Sciences 149
150 Fall Business Economics 151 Fall Psychology and Social Behavior 152 Fall Psychology 153
154 Fall Pharmaceutical Sciences 155 Fall Biological Sciences 156 Fall Biological Sciences 157 Fall Biological Sciences 158 Fall Pharmaceutical Sciences 159 Fall Biological Sciences 160 Fall Biological Sciences 161
162 Fall Pharmaceutical Sciences 163 Fall Biological Sciences 164 Fall Biological Sciences 165 Fall Biological Sciences 166 Fall Public Health Sciences 167 Fall Biological Sciences 168 Fall Biological Sciences 169 Fall Biological Sciences 170 Fall Biological Sciences 171 Fall Biological Sciences 172 Fall Biological Sciences 173 Fall Psychology and Social Behavior 174 Fall Computer Science 175
176 Fall Biological Sciences 177 Fall Biological Sciences 178
179 Fall Undeclared 180 Fall Dance 181 Fall Biological Sciences 182 Fall Art 183
184 Fall Biological Sciences 185
186 Fall Biological Sciences 187 Fall Biological Sciences 188 Fall Business Administration 189
190 Fall Computer Science 191 Fall Public Health Sciences 192

Getting structure of the data

``` r
str(demodata)
```

'data.frame': 192 obs. of 19 variables: $ roster\_randomid : int 672849 872962 482931 455346 491579 608378 714417 508735 407162 529371 ... $ officialroster : Factor w/ 3 levels "","NO","Yes": 3 3 3 3 3 3 3 3 3 3 ... $ ingradebookdata : Factor w/ 2 levels "","Yes": 2 2 2 2 2 2 2 2 2 2 ... $ insurveyparticipatedata : Factor w/ 2 levels "","Yes": 2 2 2 2 2 2 2 2 2 2 ... $ status : Factor w/ 2 levels "","Enrolled": 2 2 2 2 2 2 2 2 2 2 ... $ gender : Factor w/ 4 levels "","Female","Male",..: 3 3 3 3 2 2 3 2 3 3 ... $ eth2009rollupforreporting: Factor w/ 6 levels "","Asian / Pacific Islander",..: 4 2 6 2 2 3 2 2 5 2 ... $ agegroup : Factor w/ 9 levels "","18","19","20",..: 4 4 8 3 4 3 4 3 4 3 ... $ lowincomeflag : Factor w/ 4 levels "","N","NAT","Y": 2 2 2 2 4 2 2 2 2 4 ... $ fulltimestatus : Factor w/ 3 levels "","Full-time",..: 3 3 3 2 2 2 2 3 2 3 ... $ firstgenerationflag : Factor w/ 5 levels "","MDT","N","NAT",..: 3 3 5 5 5 5 3 5 5 5 ... $ homeprimarylang : Factor w/ 5 levels "","English only",..: 3 2 5 2 5 2 3 2 5 3 ... $ admissionsstatusdetail : Factor w/ 4 levels "","Freshman",..: 2 2 4 2 2 2 2 2 2 2 ... $ hsgpa : num 4.18 4 NA 4.04 4.14 ... $ transfergpa : num NA NA 3.22 NA NA NA NA NA NA NA ... $ gpacumulative : logi NA NA NA NA NA NA ... $ firstregacadyr : Factor w/ 6 levels "","2009-10","2012-13",..: 5 4 6 6 5 5 5 5 5 5 ... $ firstregacadterm : Factor w/ 2 levels "","Fall": 2 2 2 2 2 2 2 2 2 2 ... $ major1 : Factor w/ 27 levels "","Anthropology",..: 5 5 19 13 5 21 5 5 5 5 ...

Wait, yuck! Why does my ouput look so bad? How can I make it neater
===================================================================

looking

using dplyr as\_tibble is a special type of data frame that prints out quick summary tables

``` r
demodata <- as_tibble(demodata)
```

``` r
demodata
```

A tibble: 192 x 19
==================

roster\_randomid officialroster ingradebookdata insurveypartici… status <int> <fct> <fct> <fct> <fct> 1 672849 Yes Yes Yes Enrol… 2 872962 Yes Yes Yes Enrol… 3 482931 Yes Yes Yes Enrol… 4 455346 Yes Yes Yes Enrol… 5 491579 Yes Yes Yes Enrol… 6 608378 Yes Yes Yes Enrol… 7 714417 Yes Yes Yes Enrol… 8 508735 Yes Yes Yes Enrol… 9 407162 Yes Yes Yes Enrol… 10 529371 Yes Yes Yes Enrol… \# ... with 182 more rows, and 14 more variables: gender <fct>, \# eth2009rollupforreporting <fct>, agegroup <fct>, lowincomeflag <fct>, \# fulltimestatus <fct>, firstgenerationflag <fct>, \# homeprimarylang <fct>, admissionsstatusdetail <fct>, hsgpa <dbl>, \# transfergpa <dbl>, gpacumulative <lgl>, firstregacadyr <fct>, \# firstregacadterm <fct>, major1 <fct>

``` r
str(demodata)
```

Classes 'tbl\_df', 'tbl' and 'data.frame': 192 obs. of 19 variables: $ roster\_randomid : int 672849 872962 482931 455346 491579 608378 714417 508735 407162 529371 ... $ officialroster : Factor w/ 3 levels "","NO","Yes": 3 3 3 3 3 3 3 3 3 3 ... $ ingradebookdata : Factor w/ 2 levels "","Yes": 2 2 2 2 2 2 2 2 2 2 ... $ insurveyparticipatedata : Factor w/ 2 levels "","Yes": 2 2 2 2 2 2 2 2 2 2 ... $ status : Factor w/ 2 levels "","Enrolled": 2 2 2 2 2 2 2 2 2 2 ... $ gender : Factor w/ 4 levels "","Female","Male",..: 3 3 3 3 2 2 3 2 3 3 ... $ eth2009rollupforreporting: Factor w/ 6 levels "","Asian / Pacific Islander",..: 4 2 6 2 2 3 2 2 5 2 ... $ agegroup : Factor w/ 9 levels "","18","19","20",..: 4 4 8 3 4 3 4 3 4 3 ... $ lowincomeflag : Factor w/ 4 levels "","N","NAT","Y": 2 2 2 2 4 2 2 2 2 4 ... $ fulltimestatus : Factor w/ 3 levels "","Full-time",..: 3 3 3 2 2 2 2 3 2 3 ... $ firstgenerationflag : Factor w/ 5 levels "","MDT","N","NAT",..: 3 3 5 5 5 5 3 5 5 5 ... $ homeprimarylang : Factor w/ 5 levels "","English only",..: 3 2 5 2 5 2 3 2 5 3 ... $ admissionsstatusdetail : Factor w/ 4 levels "","Freshman",..: 2 2 4 2 2 2 2 2 2 2 ... $ hsgpa : num 4.18 4 NA 4.04 4.14 ... $ transfergpa : num NA NA 3.22 NA NA NA NA NA NA NA ... $ gpacumulative : logi NA NA NA NA NA NA ... $ firstregacadyr : Factor w/ 6 levels "","2009-10","2012-13",..: 5 4 6 6 5 5 5 5 5 5 ... $ firstregacadterm : Factor w/ 2 levels "","Fall": 2 2 2 2 2 2 2 2 2 2 ... $ major1 : Factor w/ 27 levels "","Anthropology",..: 5 5 19 13 5 21 5 5 5 5 ...

Examining specific variables

``` r
str(demodata$gender)
```

Factor w/ 4 levels "","Female","Male",..: 3 3 3 3 2 2 3 2 3 3 ...

``` r
head(demodata$gender)
```

\[1\] Male Male Male Male Female Female Levels: Female Male Not stated

``` r
table(demodata$gender)
```

               Female       Male Not stated 
        33         91         67          1 

overwriting original data import, but now declaring how to deal with empty cells

``` r
demodata <- read.csv("/Volumes/GoogleDrive/My Drive/R Workspace/R-for-Ed-Data-Science/Data/Physics Course Demo Data.csv", header = T,
                     na.strings=c("","NA"))
```

Examining specific variables

``` r
str(demodata$gender)
```

Factor w/ 3 levels "Female","Male",..: 2 2 2 2 1 1 2 1 2 2 ...

``` r
head(demodata$gender)
```

\[1\] Male Male Male Male Female Female Levels: Female Male Not stated

``` r
table(demodata$gender)
```

    Female       Male Not stated 
        91         67          1 

But wait, don't I want to know what the NAs are?
================================================

How can we find out what the function table() can do, and can we find some script that displays the NAs?

``` r
table(demodata$gender, useNA = ("always"))
```

    Female       Male Not stated       <NA> 
        91         67          1         33 

The next library will change your life.

``` r
library(summarytools)
```

``` r
print(dfSummary(demodata), method = 'rmarkdown')
```

<!--html_preserve-->
<div class="container st-container">
<h3>
Data Frame Summary
</h3>
<h4>
demodata
</h4>
<strong>N</strong>: 192
<table class="table table-striped table-bordered st-table st-table-striped st-table-bordered st-multiline ">
<thead>
    <tr>
      <th align="center"><strong>No</strong></th>
      <th align="center"><strong>Variable</strong></th>
      <th align="center"><strong>Stats / Values</strong></th>
      <th align="center"><strong>Freqs (% of Valid)</strong></th>
      <th align="center"><strong>Graph</strong></th>
      <th align="center"><strong>Valid</strong></th>
      <th align="center"><strong>Missing</strong></th>
    </tr>

</thead>
<tbody>
    <tr>
      <td align="center">1</td>
      <td align="left">roster_randomid

\[integer\]
</td>
      <td align="left">mean (sd) : 514434.11 (243939.78)

min &lt; med &lt; max : 104500 &lt; 543478 &lt; 994588 IQR (CV) : 409408.75 (0.47)
</td>
      <td align="left">192 distinct values</td>
      <td align="center" border="0"><img src="data:image/png;base64,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"></td>
      <td align="center">192

(100%)
</td>
      <td align="center">0

(0%)
</td>
    </tr>
    <tr>
      <td align="center">2</td>
      <td align="left">officialroster

\[factor\]
</td>
      <td align="left">1. NO

1.  Yes
    </td>
    <td align="left">
    14 (7.4%) 176 (92.6%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAAA0CAYAAABo1cEHAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAIqSURBVHgB7Zy7agJREIZ3vSEWm3QxpEydOtVCKqvUqSVPY5038B0C9jZbmZeQVBosBNFdXHNc0p80A7Mzn42Fw/BfPg4iZ00SXiRAAiTQlgTSq9D5fP6RpulLt9stY8Lruu6dz+ev6XT6Hpvlc78J9K7WA1DPk8nkKbxHk7hcLslisehEBxlwnUADVkigDidWMhwOo2GUZZmE2To6yIDrBDh5XNcvZx6w5LJ1vRmwXNcvZx6w5LJ1vRmwXNcvZx6w5LJ1vRmwXNcvZx6w5LJ1vRmwXNcvZx6w5LJ1vRmwXNcvZx6w5LJ1vRmwXNcvZx6w5LJ1vRmwXNcvZx6w5LJ1vRmwXNcvZx6w5LJ1vbm5mhzusQ/W63XS6cQ5u955Px6Pd65Tw3w0gQas3W73VhRFHp3+G6iqqvjvLHMkQAIkQAIkoDuB5oHV2Wx2MxqNHnRLRV2LEjg137HG4/FnlmWPg8GgapF4pCpNYLPZZA1YvfDK8/w+nFpKpSKrTQmsVquf+O8LbXKEVjUJAJaaKmwJASxbfapxA1hqqrAlBLBs9anGDWCpqcKWEMCy1acaN4ClpgpbQgDLVp9q3ACWmipsCQEsW32qcQNYaqqwJQSwbPWpxg1gqanClhDAstWnGjeApaYKW0IAy1afatwAlpoqbAkBLFt9qnHT3HkPD6Celsvld7/f52EKNdW0V8h2u71twDocDq/7/Z7H5tvbpSrl4W8YOKBUNWJIzC+SOE5VoxsXVAAAAABJRU5ErkJggg==">
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
        176 (100.0%)
        </td>
        <td align="center" border="0">
        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAAAaCAYAAABVc6VBAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAEMSURBVGgF7ZsxDoJAFETZxRBDZbyLtRa0XoxbcBGOwQ0skcrGNerCGdhp5pkYuz+ZNy+x2qriA4ECBMJ6cxiGPsZ4CyGkAhmcNCOQUjoe1s51XV+7rrvkXzME1C1BYJqm5yZWPv5dpWrbtkQON80I5H++XzTrTF0RAcQSgXaLQSy3xUV9EUsE2i0GsdwWF/VFLBFotxjEcltc1BexRKDdYhDLbXFRX8QSgXaLQSy3xUV9EUsE2i0GsdwWF/VFLBFotxjEcltc1BexRKDdYhDLbXFRX8QSgXaLQSy3xUV9EUsE2i1me0yRn+u8xnF8NE3zdgNA3/0JzPN82sRaluWev+f9I7joSCC/Uf38AQpcH7AT02JyAAAAAElFTkSuQmCC">
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
            190 (100.0%)
            </td>
            <td align="center" border="0">
            <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAAAaCAYAAABVc6VBAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAEMSURBVGgF7ZsxDoJAFETZxRBDZbyLtRa0XoxbcBGOwQ0skcrGNerCGdhp5pkYuz+ZNy+x2qriA4ECBMJ6cxiGPsZ4CyGkAhmcNCOQUjoe1s51XV+7rrvkXzME1C1BYJqm5yZWPv5dpWrbtkQON80I5H++XzTrTF0RAcQSgXaLQSy3xUV9EUsE2i0GsdwWF/VFLBFotxjEcltc1BexRKDdYhDLbXFRX8QSgXaLQSy3xUV9EUsE2i0GsdwWF/VFLBFotxjEcltc1BexRKDdYhDLbXFRX8QSgXaLQSy3xUV9EUsE2i1me0yRn+u8xnF8NE3zdgNA3/0JzPN82sRaluWev+f9I7joSCC/Uf38AQpcH7AT02JyAAAAAElFTkSuQmCC">
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
                176 (100.0%)
                </td>
                <td align="center" border="0">
                <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAAAaCAYAAABVc6VBAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAEMSURBVGgF7ZsxDoJAFETZxRBDZbyLtRa0XoxbcBGOwQ0skcrGNerCGdhp5pkYuz+ZNy+x2qriA4ECBMJ6cxiGPsZ4CyGkAhmcNCOQUjoe1s51XV+7rrvkXzME1C1BYJqm5yZWPv5dpWrbtkQON80I5H++XzTrTF0RAcQSgXaLQSy3xUV9EUsE2i0GsdwWF/VFLBFotxjEcltc1BexRKDdYhDLbXFRX8QSgXaLQSy3xUV9EUsE2i0GsdwWF/VFLBFotxjEcltc1BexRKDdYhDLbXFRX8QSgXaLQSy3xUV9EUsE2i1me0yRn+u8xnF8NE3zdgNA3/0JzPN82sRaluWev+f9I7joSCC/Uf38AQpcH7AT02JyAAAAAElFTkSuQmCC">
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

2.  Male
3.  Not stated
    </td>
    <td align="left">
    91 (57.2%) 67 (42.1%) 1 (0.6%)
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

4.  Hispanic
5.  International student
6.  Unknown / declined to sta
7.  White, non-Hispanic
    </td>
    <td align="left">
    102 (64.1%) 18 (11.3%) 15 (9.4%) 13 (8.2%) 11 (6.9%)
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

8.  19
9.  20
10. 21
11. 22
12. 23
13. 24
14. 25-29
    </td>
    <td align="left">
    6 (3.8%) 59 (37.1%) 67 (42.1%) 17 (10.7%) 6 (3.8%) 1 (0.6%) 1 (0.6%) 2 (1.3%)
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

15. NAT
16. Y
    </td>
    <td align="left">
    102 (64.1%) 2 (1.3%) 55 (34.6%)
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

17. Part-time
    </td>
    <td align="left">
    93 (58.5%) 66 (41.5%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAAA0CAYAAABo1cEHAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAJESURBVHgB7Zu/asJwFEb9G8RShS6ldOzcuVNKJ6fOfQv1NZz7BPoqdhCc49zBdChapAqWNKCN6eRy0TvovXBcRG4uv4/zHQKKKRR4QQACEPBCoLgLOhgMXovF4lO5XP71EpycdgkkSXJR2cXLhHpotVr32bvdtCRzQyCKoq9crCzxJrtjFWq1mpvwBLVLYOdSyW48knkmgFie2zOcHbEMl+M5GmJ5bs9wdsQyXI7naIjluT3D2RHLcDmeoyGW5/YMZ0csw+V4joZYntsznB2xDJfjORpieW7PcHbEMlyO52iI5bk9w9kRy3A5nqMhluf2DGdHLMPleI6GWJ7bM5w9/2vydrsNptNpoVTCM8NduYkWx/H/wxSLxeJlNBqFbpIT1DSB7Eb1bTog4SAAAQjsEcgfWO31es16vX67N+GDKQLZI1U/7Xb73VQoIUwuVr/ff2s0GndBEKTCtYzOSGA2m10ul8vHbrcbnTHGwUfn3wor2SsMw5vsrnXwIheelsB4PP6cTCZXpz1Vfxq/L+jZsSkQQCwBDiM9AcTSs2NTIIBYAhxGegKIpWfHpkAAsQQ4jPQEEEvPjk2BAGIJcBjpCSCWnh2bAgHEEuAw0hNALD07NgUCiCXAYaQngFh6dmwKBBBLgMNITwCx9OzYFAgglgCHkZ4AYunZsSkQQCwBDiM9AcTSs2NTIJD/5z1N02Q4HH5Uq1UephBgnXM0n8+bm81mfs4Mx5ydi7Ver59Xq9X1MYtce3ICSafTiU9+KgdCwBKBP2tzTucDzUPbAAAAAElFTkSuQmCC">
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

18. N
19. NAT
20. Y
    </td>
    <td align="left">
    7 (4.4%) 77 (48.4%) 2 (1.3%) 73 (45.9%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAABoCAYAAAATmQmLAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAR+SURBVHgB7d2xT1pRFMfxh6AIQw3S1KUNaetiRxO7dKoLQ/+MOtXJ/8M4OZo4tbNT290YXdy0UwfSxCAmRKyEYkHo9SUvafBeL97jwJGviUGO917P+9xfLCXv+aKIDwQQQAABBBBAAIGHFkjdLLi9vf15YmLinfn8O+wPaLfbxVQq9XFlZWVn2DmMGx+BzM2hTk5OviqXy6Xp6emhj/zk5CTa29tbNBMI1tBq4zMwDlZyuOY3VvIljwiIBEiSiI/JLgGC5ZKhLhIgWCI+JrsECJZLhrpIgGCJ+JjsEiBYLhnqIgGCJeJjskuAYLlkqIsECJaIj8kuAYLlkqEuEiBYIj4muwQIlkuGukiAYIn4mOwSIFguGeoiAYIl4mOyS4BguWSoiwQIloiPyS6B5AzSdLPZjFqtlmvcrXqn04nMOe/J/FvfpzDeAnEw+v3+1u7ubsWcmtwdlsPMSfd6vS/DjmccAggggAACoykQX1e4sbGRy2azM6PZIl1pE7g2H/FrrNnZ2Z1cLvcmnU53tB0E/Y6ewMXFxUwcrEwm82R5efl5Pp8fvS7pSJ3A4eFhnfex1G2bjoYJlo59UtclwVK3ZToaJlg69kldlwRL3ZbpaJhg6dgndV0SLHVbpqNhgqVjn9R1SbDUbZmOhgmWjn1S1yXBUrdlOhomWDr2SV2XBEvdlulomGDp2Cd1XRIsdVumo2GCpWOf1HVJsNRtmY6GCZaOfVLXZXJd4eTp6WlkznlXdwA0PHoC1Wo1HwfLXAG9enBw8N5c2dwfvTbpSJuAuZj5j7ae6RcBBMZZIL5gdX19/am5V+HrBML8wY9fa2tr1eQ5jwjcVyB+jVUsFr/Ozc2Vpqamuubfx1SlUrk2C72472KMRyARiINl7rB6vbS09OzmglXzF2Qi8z/En8kAHhEIEeB9rBA15ngFCJaXiAEhAgQrRI05XgGC5SViQIgAwQpRY45XgGB5iRgQIkCwQtSY4xUgWF4iBoQIEKwQNeZ4BQiWl4gBIQIEK0SNOV4BguUlYkCIAMEKUWOOV4BgeYkYECJAsELUmOMVIFheIgaECBCsEDXmeAUIlpeIASEC8anJV1dXM8fHxy1zQUXPnPMetdvtQshizEEgEYiD1Wg0ykdHR4tJ0dwV7EfyNY8IIIAAAgg8boH4gtXNzc2SeW319nEfKkf3kALmxvTfVldXm64149dY5nrC7/Pz8y/NXVZ7roHUEUgEzs7OMrVabcs8/5TUBh/jYJkroBsLCwtZ7rA6yMNzm0ChUIjq9fqdt3nmfSybHDWxAMESE7KATYBg2VSoiQUIlpiQBWwCBMumQk0sQLDEhCxgEyBYNhVqYgGCJSZkAZsAwbKpUBMLECwxIQvYBAiWTYWaWIBgiQlZwCZAsGwq1MQCBEtMyAI2AYJlU6EmFiBYYkIWsAkQLJsKNbEAwRITsoBNID412dztK9rf369ls9k7Tze1LUBt/AS63W7a3HPp911HHgfr/Pz8w+XlZemugXwPgQEBLmoeAOEpAggggAAC/wn8A3lspuy4FkDEAAAAAElFTkSuQmCC">
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

21. English/non-English
22. Missing data
23. Non-English
    </td>
    <td align="left">
    37 (23.3%) 67 (42.1%) 2 (1.3%) 53 (33.3%)
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAABoCAYAAAATmQmLAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAR1SURBVHgB7Z0/S5tRFIcTkxgTqEIsdSmEti52LNildKhLhg79EI4NfgY/gDg5FqVD9wptl06ioFDcDIJTNv9gk4iS4pva9OZCIIt4LwTOfc99BGk0J/ee8/weJIT39s1k+IIABCAAAQhAAAIQGDeB7GDBra2tLxMTE2/MdzLuDWJaL0mS8+Xl5bcxzXzfrPnBE4VC4XmtVqtOTU3dV8fvHyDQ7/cz29vbuQfKonnaijWc1vzFGj7kX08CA7HMd9/zZWrLMUlttLKDIZYsf7W7I5baaGUHQyxZ/mp3Ryy10coOhliy/NXujlhqo5UdDLFk+avdHbHURis7GGLJ8le7O2KpjVZ2MMSS5a92d8RSG63sYIgly1/t7oilNlrZwRBLlr/a3RFLbbSygw2vIM3d3Nxkut2ubDcp373X6z1K+Qhja9+KZa6o/bS7u9s0lyb/HdvKES6Uz+ePIxybkSEAAQiknIA9V7i+vl4qFoszKZ+F9gMhcGe+7HusSqXytVQqvczlcr1AeqONFBO4urqasWKZN53TS0tLT8vlcorHofVQCBweHv7mc6xQ0lDWB2IpCzSUcRArlCSU9YFYygINZRzECiUJZX0glrJAQxkHsUJJQlkfiKUs0FDGQaxQklDWB2IpCzSUcRArlCSU9YFYygINZRzECiUJZX0glrJAQxkHsUJJQlkfiKUs0FDGQaxQklDWB2IpCzSUcYbnCgtnZ2cZc817KH3RR4oJnJ6elq1Y5gT0x4ODg3fZbJZ7waQ40FBaNweg/4TSC31AAAIQeJiAPbC6trb22Nyr8MVo+eXl5a/V1dV/o7/jMQRcCdj3WLOzsz/m5uaqk5OT9j8Fubi4mDY3x6ybRT67LkQdBEYJWLGMRHeLi4tPhgdWm81mZm9vrzJayGMI+BDgcywfWtQ6E0AsZ1QU+hBALB9a1DoTQCxnVBT6EEAsH1rUOhNALGdUFPoQQCwfWtQ6E0AsZ1QU+hBALB9a1DoTQCxnVBT6EEAsH1rUOhNALGdUFPoQQCwfWtQ6E0AsZ1QU+hBALB9a1DoTQCxnVBT6EEAsH1rUOhNALGdUFPoQsJcm397ezjQaja45UGEPT5ifs+ammInPQtRCYJSAFavT6dSOjo5ejT6xs7PzbfRnHkMAAhCAAAR0ErAHVjc2NqrmvP1rnSPGOZXJs7uysvJdanor1ubm5vH8/Pwzc5dVTj5LJTHmfU9OTjLtdvtDvV7/OealnZazb97NCejOwsJCcXhg1emVFAVNIEmSdqvVsvlKNMrnWBLUI9gTsSIIWWJExJKgHsGeiBVByBIjIpYE9Qj2RKwIQpYYEbEkqEewJ2JFELLEiIglQT2CPRErgpAlRkQsCeoR7IlYEYQsMSJiSVCPYE/EiiBkiRERS4J6BHsiVgQhS4yIWBLUI9gTsSIIWWJEe+lqr9fL7O/vnxeLxZ5EE+w5fgLmLqfT5samrfGv7LaiFctcdP/++vq66vYSqtJAYHCS3RykaKShV3qEAAQgAAEIKCTwH928p+nBXfvjAAAAAElFTkSuQmCC">
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

24. Not applicable
25. Transfer
    </td>
    <td align="left">
    151 (95.0%) 2 (1.3%) 6 (3.8%)
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
    mean (sd) : 4 (0.22) min &lt; med &lt; max : 3.16 &lt; 4.04 &lt; 4.4 IQR (CV) : 0.23 (0.06)
    </td>
    <td align="left">
    59 distinct values
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
    mean (sd) : 3.33 (0.28) min &lt; med &lt; max : 3.01 &lt; 3.25 &lt; 3.71 IQR (CV) : 0.38 (0.08)
    </td>
    <td align="left">
    3.01 : 1 (16.7%) 3.14! : 1 (16.7%) 3.22 : 1 (16.7%) 3.28 : 1 (16.7%) 3.63! : 1 (16.7%) 3.71 : 1 (16.7%) ! rounded
    </td>
    <td align="center" border="0">
    <img src="data:image/png;base64,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">

</td>
      <td align="center">6

(3.12%)
</td>
      <td align="center">186

(96.88%)
</td>
    </tr>
    <tr>
      <td align="center">16</td>
      <td align="left">gpacumulative

\[logical\]
</td>
      <td align="left"></td>
      <td align="left">All NA's</td>
      <td align="center" border="0"></td>
      <td align="center">0

(0%)
</td>
      <td align="center">192

(100%)
</td>
    </tr>
    <tr>
      <td align="center">17</td>
      <td align="left">firstregacadyr

\[factor\]
</td>
      <td align="left">1. 2009-10

1.  2012-13
2.  2013-14
3.  2014-15
4.  2015-16
    </td>
    <td align="left">
    1 (0.6%) 5 (3.1%) 21 (13.2%) 109 (68.5%) 23 (14.5%)
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
        159 (100.0%)
        </td>
        <td align="center" border="0">
        <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJYAAAAaCAYAAABVc6VBAAAEGWlDQ1BrQ0dDb2xvclNwYWNlR2VuZXJpY1JHQgAAOI2NVV1oHFUUPrtzZyMkzlNsNIV0qD8NJQ2TVjShtLp/3d02bpZJNtoi6GT27s6Yyc44M7v9oU9FUHwx6psUxL+3gCAo9Q/bPrQvlQol2tQgKD60+INQ6Ium65k7M5lpurHeZe58853vnnvuuWfvBei5qliWkRQBFpquLRcy4nOHj4g9K5CEh6AXBqFXUR0rXalMAjZPC3e1W99Dwntf2dXd/p+tt0YdFSBxH2Kz5qgLiI8B8KdVy3YBevqRHz/qWh72Yui3MUDEL3q44WPXw3M+fo1pZuQs4tOIBVVTaoiXEI/MxfhGDPsxsNZfoE1q66ro5aJim3XdoLFw72H+n23BaIXzbcOnz5mfPoTvYVz7KzUl5+FRxEuqkp9G/Ajia219thzg25abkRE/BpDc3pqvphHvRFys2weqvp+krbWKIX7nhDbzLOItiM8358pTwdirqpPFnMF2xLc1WvLyOwTAibpbmvHHcvttU57y5+XqNZrLe3lE/Pq8eUj2fXKfOe3pfOjzhJYtB/yll5SDFcSDiH+hRkH25+L+sdxKEAMZahrlSX8ukqMOWy/jXW2m6M9LDBc31B9LFuv6gVKg/0Szi3KAr1kGq1GMjU/aLbnq6/lRxc4XfJ98hTargX++DbMJBSiYMIe9Ck1YAxFkKEAG3xbYaKmDDgYyFK0UGYpfoWYXG+fAPPI6tJnNwb7ClP7IyF+D+bjOtCpkhz6CFrIa/I6sFtNl8auFXGMTP34sNwI/JhkgEtmDz14ySfaRcTIBInmKPE32kxyyE2Tv+thKbEVePDfW/byMM1Kmm0XdObS7oGD/MypMXFPXrCwOtoYjyyn7BV29/MZfsVzpLDdRtuIZnbpXzvlf+ev8MvYr/Gqk4H/kV/G3csdazLuyTMPsbFhzd1UabQbjFvDRmcWJxR3zcfHkVw9GfpbJmeev9F08WW8uDkaslwX6avlWGU6NRKz0g/SHtCy9J30o/ca9zX3Kfc19zn3BXQKRO8ud477hLnAfc1/G9mrzGlrfexZ5GLdn6ZZrrEohI2wVHhZywjbhUWEy8icMCGNCUdiBlq3r+xafL549HQ5jH+an+1y+LlYBifuxAvRN/lVVVOlwlCkdVm9NOL5BE4wkQ2SMlDZU97hX86EilU/lUmkQUztTE6mx1EEPh7OmdqBtAvv8HdWpbrJS6tJj3n0CWdM6busNzRV3S9KTYhqvNiqWmuroiKgYhshMjmhTh9ptWhsF7970j/SbMrsPE1suR5z7DMC+P/Hs+y7ijrQAlhyAgccjbhjPygfeBTjzhNqy28EdkUh8C+DU9+z2v/oyeH791OncxHOs5y2AtTc7nb/f73TWPkD/qwBnjX8BoJ98VQNcC+8AAAEMSURBVGgF7ZsxDoJAFETZxRBDZbyLtRa0XoxbcBGOwQ0skcrGNerCGdhp5pkYuz+ZNy+x2qriA4ECBMJ6cxiGPsZ4CyGkAhmcNCOQUjoe1s51XV+7rrvkXzME1C1BYJqm5yZWPv5dpWrbtkQON80I5H++XzTrTF0RAcQSgXaLQSy3xUV9EUsE2i0GsdwWF/VFLBFotxjEcltc1BexRKDdYhDLbXFRX8QSgXaLQSy3xUV9EUsE2i0GsdwWF/VFLBFotxjEcltc1BexRKDdYhDLbXFRX8QSgXaLQSy3xUV9EUsE2i1me0yRn+u8xnF8NE3zdgNA3/0JzPN82sRaluWev+f9I7joSCC/Uf38AQpcH7AT02JyAAAAAElFTkSuQmCC">
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

5.  Art
6.  Art History
7.  Biological Sciences
8.  Biology/Education
9.  Business Administration
10. Business Economics
11. Computer Game Science
12. Computer Science
13. Dance \[ 16 others \]
    </td>
    <td align="left">
    1 (0.6%) 2 (1.3%) 1 (0.6%) 89 (56.0%) 1 (0.6%) 1 (0.6%) 1 (0.6%) 6 (3.8%) 5 (3.1%) 3 (1.9%) 49 (30.8%)
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
    Generated by <a href='https://github.com/dcomtois/summarytools'>summarytools</a> 0.8.8 (<a href='https://www.r-project.org/'>R</a> version 3.5.2)<br/>2019-01-16
    </p>
    </div>
    <!--/html_preserve-->
