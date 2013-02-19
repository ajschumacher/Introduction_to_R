---
title       : Introduction to R
subtitle    : bit.ly/NYUintroR
author      : Aaron Schumacher
job         : Senior Data Services Specialist
biglogo        : data_services_logo.png
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # {tomorrow, solarized_light}
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
license     : by-nc-sa
github:
  user: ajschumacher
  repo: Introduction_to_R
--- &twocol

## [NYU Data Services](http://bit.ly/nyudataservices)

*** left

* [Computer lab, Bobst 5](http://nyu.libguides.com/content.php?pid=38898&sid=1496756)
* [Workshops/Tutorials](http://bit.ly/datatutorials)
* [Individual consultations](http://bit.ly/datameeting)

*** right

* ArcGIS
* Google Earth
* SPSS
* Stata
* SAS
* R
* MATLAB
* ATLAS.ti
* Qualtrics Surveys
* High Performance Computing
* Data Finding
* Data Management Planning

---

## Introduction to R

* Why use R?
* What is R / RStudio?
* Everything is a function.
* Everything is a vector.
* Super-vectors
* Simple statistics
* Base graphics
* More!

---

## Why use R?

* Open Source / Free
* Increasingly popular
* Powerful and Extensible
* Makes reproducible research easy, convenient and diverse visualization options, more statistics than you can shake a stick at, excellent for exploratory data analysis, many support options, often first for cutting-edge techniques, ...
* Available:
    * Download: [R](http://cran.r-project.org/mirrors.html) / [RStudio](http://www.rstudio.com/ide/download/)
    * Data Services lab, fifth floor Bobst
    * Most ITS labs
    * Virtual Computing Lab ([VCL](https://vcl.nyu.edu/)) (for students)
    * High Performance Computing ([HPC](https://wikis.nyu.edu/display/NYUHPC/High+Performance+Computing+at+NYU)) clusters (requires account)

---

<center>
 <a style='border-bottom:none;' href='http://www.nytimes.com/2009/01/07/technology/business-computing/07program.html'>
  <img src='assets/img/nytimes_article.png' height='600px' />
 </a>
</center>

---

<center>
 <a style='border-bottom:none;' href='http://blog.kaggle.com/2011/11/27/kagglers-favorite-tools/'>
  <img src='assets/img/kaggler_prefs.png' height='600px' />
 </a>
</center>

---

<center>
 <a style='border-bottom:none;' href='http://rpubs.com/bbolker/3153'>
  <img src='assets/img/reproducible.png' height='600px' />
 </a>
</center>

---

<center>
 <a style='border-bottom:none;' href='https://www.facebook.com/notes/facebook-engineering/visualizing-friendships/469716398919'>
  <img src='assets/img/facebook_map.jpg' width='950px' />
 </a>
</center>

---

<center>
 <a style='border-bottom:none;' href='http://csgillespie.wordpress.com/2010/12/08/new-paper-survival-analysis/'>
  <img src='http://csgillespie.files.wordpress.com/2010/12/gastrostomy.png' height='600px' />
 </a>
</center>

---

<center>
  <img src='assets/img/packagecounts.png' width='950px' />
</center>

---

## Why not use R?

* It's not Excel.
* It's not SAS/Stata/SPSS/etc.
* It's not C.
* Defaults to in-memory.
* Often not best for building interactives.

---

## What is R?

<center><img src="assets/img/what_is_R.png" height=540 /></center>

---

## What is RStudio?

An Integrated Development Environment (IDE) for R. Check it out!
<center><img src="assets/img/RStudio.png" height=500 /></center>

---

## Everything is a function.

Anything you want to do in R is done by telling R to run a function.

To run a function with no arguments, follow its name with parentheses.

```r
help()
```


Arguments are passed inside the parentheses. Arguments are usually named, but names can be omitted if it's unambiguous.

```r
help(topic = getwd)
help(getwd)
```


If you don't include parenthes, R will try to return the function itself.

```r
help
```


---

## Working Directories

* A working directory is the current file directory used reference importing and exporting files to/from R.
* Paths are used to reference locations outside of the current directory.
    * Folders are denoted by forward slashes: `/`
    * Moving up a folder is denoted by two periods: `..`
* Check the current working directory: `getwd()`
* Change the working directory: `setwd("<path>")`

---

## Writing R Programs

* R scripts should be written and saved instead of interactively using R's CLI.
* Some advantages to writing R scripts include:
    * Possibility to reuse code
    * Allows for editing of code
    * Easier to write and read complex expressions
* Comments can be added to a script with "`#`"
* Programs can be written in any text editor, including R's document editor, and called using the `source()` function.

---

## Using Functions

* Functions allow users to easily perform complex tasks using custom input and specifications.
* To call a function type its function name followed by the desired set argument(s) enclosed in parenthesis.


```r
sqrt(4^2)
```

* Parenthesis are still required when a function takes no arguments.

```r
getwd()
```

* The most important function is likely `help()`.
* Take note of the default arguments for each function.

```r
sum(c(1, 2, 3, NA))
sum(c(1, 2, 3, NA), rm.na = TRUE)
```


---

## Packages

* Collections of user-created functions that are tested by and freely distributed to the R community.
* Users submit packages on a regular basis (4063 available as of 9/2012).
* Using a package requires a 3 steps:

1\. Install the package on your local machine (note: only needs to be done once per machine)

```r
install.packages("<package name>")
```

2\. Load the install package (note: needs to be done each time R is opened)

```r
library(<package name>)
```

3\. Use the packages' objects

---

## Objects

* Objects are symbolic names that represent some form of information.
* In R there is no need to define an object's type upon declaration.

```r
var1 = 5
var2 = "a"
```

* R utilizes generic functions based upon an object's class. Use the `class()` function to check an object's class.

```r
class(var1)
```


---

## Vectors

* Vectors are basically one-dimensional arrays that hold one type, or class, of information.
* The `c()` function can be used to combine elements into a vector.

```r
v1 = c("a", "b", "c", "d")
```

* Elements of a vector can be referenced via brackets and their corresponding index, which ranges from 1 to the number of elements in the vector.

```r
v1[2]
```

```
## [1] "b"
```

```r
v1[c(4, 1)]
```

```
## [1] "d" "a"
```


---

## Workspace

* R's workspace contains all currently accessible objects.
* The workspace can be viewed with the `ls()` function.
* Objects can be deleted with the `rm()` function.
* the entire workspace can be saved to a .Rdata file with the `save.image()` function.
* An entire workspace can be loaded, and used later, with the `load()` function.

---

## Data Frames

* R's class for tabular datasets is data frame.
* The `data.frame()` function can be used convert a set of vectors of equal length, but potentially different classes, into a data fram.
* Data frame elements can be referenced using brackets and indices, like so: `<dataframe>[<row>,<column>]`.
* Columns also have names that can be referenced vis "$".

```r
names(data)
data$score
```

* Since one column is a vector, elements of a column can still be referenced with brackets and an index.

```r
data$score[2]
```


---

## Importing Datasets

* Datasets of virtually any format can be imported into R, however some formats may require packages.
* Raw data can be read in using functions like `read.csv()`, `read.table()` or `scan()`, and the "foreign" package offers a number of functions that can import datasets from other statistically packages, including SPSS, SAS, and Stata.
* Remember that calling a function does not automatically save the result to an object, so make sure to save the imported dataset to specified object.

```r
data = read.csv(file = "<rtut.csv>")
```


---

## Editing Data

* Raw data can manually be edited by referencing the elements you would like to change and their desired new value(s).

```r
data$id[1] = -99
```

* The `edit()` function can also be used to edit data in a spreadsheet-like fashion.

```r
data = edit(data)
```

* Variables may also need to be edited.
    * Check the class of each variable via `str()` or `class()`.
    * Use functions to update classes, such as `as.factor()`.

---

## Recoding & Computing Variables

* Variables can be recoded in a number of ways, particularly the `recode()` function in the "car" package.
* Recoded variables can either be new or replace already existing variables depending on the object that is stored in.

```r
data$health2 = recode(data$health2, "1=5;2=4;3=3;4=2;5=1")
data$health2_R = recode(data$health2, "1=5;2=4;3=3;4=2;5=1")
```

* Variables can be created referencing a new variable name in a data frame.

```r
<dataframe>$<new name> = <vector of desired information>
data$health = mean(data[,c(“health1”, “health2”, … , “health6”)])
```


---

## Creating Subsets

* Subsets may be created by manually referencing elements.

```r
sub1 <- data[2:5, c("age", "health")]
```

* The `which()` function can also be used to select element indices based upon a conditional statement.

```r
sub2 <- data[which(data$age > 40), c("age", "health")]
```

* The `subset()` function can also be used and is likely the best choice for more complex subsets.

```r
sub3 <- subset(data, age > 40, select = c("age", "health"))
```


---

## Descriptive Statistics & Graphics

* R offers a great deal of descriptive statistics and graphics applications via base functions and in numerous packages.
* Some commonly used functions include:
    * Descriptives: `summary()`, `table()`, `mean()`, and `sd()`
    * Graphics: `plot()`, `boxplot()` and `barplot()`
* Some commonly used graphics packages include "ggplot2" and "lattice".

---

## Statistical Analysis

* R offers functions to conduct the vast majority of commonly used statistical procedures and the ability to write your own.
* Packages frequently offer improvements upon existing procedures or new functions entirely.
* Commonly used statistical function include:
    * `cor()` - Correlations
    * `t.test()` - T-Tests
    * `aov()` - ANOVA
    * `lm()` - Linear Regression
    * `glm()` - Generalized Linear Models

---

## Evaluation

* Please help the DSS improve our services and this tutorial by completing the following brief (anonymous) survey:

### [tinyurl.com/DSSIntro](http://tinyurl.com/DSSIntro)

---

## Additional Help

* The Data Service Studio is available to answer R-related questions.
    * Email: [data.service@nyu.edu](mailto:data.service@nyu.edu)
    * Phone: (212)-998-3434
    * Location: 5<sup>th</sup> Floor of Bobst Library
* Attend the Intermediate Topics in R Tutorial.
* Please refer to the DSS's training page:

[nyu.libguides.com/content.php?pid=38898&sid=1554472](http://nyu.libguides.com/content.php?pid=38898&sid=1554472)
