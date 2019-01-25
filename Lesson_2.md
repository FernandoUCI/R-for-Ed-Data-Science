---
title: "Lesson 2"
author: "Fernando Rodriguez"
date: "1/17/2019"
output: html_document
editor_options: 
  chunk_output_type: inline
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
<br><br>

# Table of Contents
0. Loading libraries
1. More workflow basics
    - Code chunks
    - Dangers of navigating
    - Code comments / commenting-out code
2. Importing data using read.csv()
    - Getting dataframe struture using str()
3. Vector types and classes
    - Factors
4. Data reduction (How do you do this?)
    - Using dfSummary()
    - Importing csv files with correct NAs
    - Re-running dfSummary()


# 0. Load libraries
```{r}
# install.packages("summarytools")
library(ggplot2) # for plotting
library(summarytools) # for getting data summaries
```
<br><br>

# 1. More workflow basics

code chunks
alt + command + i (mac)<br>
control + alt + i (windows)<br>

### Dangers of navigating multiple R-Markdown files
```{r}
# using same variable name
a <- 6 + 10
```
<br>

### Code comments / commenting out code<br>

Commenting out multiple lines of code<br>
First highlight the code, the run this<br>

control + shift + c (windows and mac)<br>
command + shift + c (mac)<br>
```{r}
# add comments. It doesn't effect the caculations

# a <- 6 + 10
# b <- 10 + 10

```
<br><br>

# 2. Importing Data using `read.csv()`

We are going to use the `read.csv()` function.<br>
There are some pros and cons to using this, but the purpose is to get familiar
with finding full path directories and the consequences of including and excluding
specific arguments. 
```{r}
demog <- read.csv("/Volumes/GoogleDrive/My Drive/R Workspace/R-for-Ed-Data-Science/Data/Physics Course Demo Data.csv", header = TRUE)
```
<br>

### Getting dataframe structure using `str()` function

```{r}
str(demog)
```
<br><br>

## 3. Vector Types and Classes
R has 6 atomic vector types<br>
Atomic means that it only holds data of a single type<br>
- character: "a" "string values"<br>
- numeric: 2, 1.4, 503<br>
- iteger: 2L (the L tells R to store this as an integer)<br>
- logical: TRUE or FALSE<br>
- complex: 1+4i (complex numbers with real and imaginary parts)<br>
<br><br>

### Factors
Factors are stored as a vector of integer values WITH a cooresponding set of character values.<br>

In many ways factors are a special case of integers.<br>
```{r}
str(demog$agegroup)
```
<br><br>

# 4. Data Reduction (How do you do this?)
Using the `summarytools` library to get overall descriptive info and NAs.<br><br>

However, as you'll see next week, the `dfSummary()` function s is not generating the 
correct Ns. This has to do with how we imported our data. We need to include an
argument that instructs R what to do with our NAs in the .csv file.

```{r}
# view(dfSummary(demog, style = 'rmarkdown'))
```
<br>

Use these additional arguments to have the table display correctly when 
knitting your R-Markdown
```{r}
print(dfSummary(demog, graph.magnif = 0.65), method = 'rmarkdown')
```
<br><br>

### Importing csv files with correct NAs
```{r}
demog2 <- read.csv("/Volumes/GoogleDrive/My Drive/R Workspace/R-for-Ed-Data-Science/Data/Physics Course Demo Data.csv", header = TRUE,
                   na.strings = c ("", NA))
```
<br>

### Re-running dfSummary
```{r}
print(dfSummary(demog2, graph.magnif = 0.65), method = 'rmarkdown')
```