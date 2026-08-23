# Week05 R Boot Camp I: Statistical Computing Ch 8

> [!IMPORTANT]
> Exam 1 is due at the beginning of this lecture

> [!NOTE]
> [Lecture Stream](https://tamucc.zoom.us/rec/share/5oTEFguSs5hjKLwLgRrNUP5dWToM-SLnQ2rv7a2fsgCLOehiHPLX-Xi9eUNUbKcX.YzmL5DfjpC1z9sdh)
> Passcode: Qft0Te?5

> [!NOTE]
> I converted the [Lecture_05 Slides](Week05new_files/Introduction%20to%20R%201.pptx) to a more screen-splitting friendly format here in GitHub.


---

## Computer Preparation

> [!IMPORTANT]
> Make sure your computer is ready for the lecture

<details><summary>Windows, Mac, Linux</summary>
<p>

- [ ] Step 0. Open Terminal

  > Search for the terminal app and open it.  For Windows, make sure you are using Ubuntu.

  > You should have already prepared your computer during Lecture 0.  If you did not then:  

  > * Complete the tasks listed in the [How to Set Up Your Computer for Computational Biology](https://github.com/tamucc-comp-bio/how_to/blob/main/howto_setup_computer.md), up to, but not including R and RStudio.
  >    * If you are having difficulty installing ubuntu, use Launch if your account is activated.

- [ ] Step 1. Update Your apps

  > It's always a good idea to keep your apps in your terminal up to date. 
  
  > For Ubuntu (Linux), enter the following commands to load the newest versions of your apps

  ```bash
  sudo apt update
  sudo apt upgrade
  ```

  > For Mac (Homebrew), enter the following commands to load the newest versions of your apps

  ```bash
  brew update
  brew upgrade
  ```

- [ ] Step 2. Confirm you have cloned the CSB (Computing Skills For Biologists) Repo into your home dir

    > In your terminal, enter the following commands:

    ```bash
    # make sure you're in your home dir
    cd ~
    
    # list the directories and files in the CSB dir to confirm it's in your home dir
    ls CSB
    ```

    > You should see the following output because we cloned the CSB Repo to your home dir in [Lecture 0](https://github.com/tamucc-comp-bio/classroom_repo_2024/blob/master/lectures/lecture00.md).  

    ```bash
    LICENSE  README.md  data_wrangling  git  good_code  latex  python  r  regex  scientific  sql  unix
    ```

    > If you see the output above, you're done! Goto the next section.

- [ ] Step 3. If you didn't have the CSB Repo, clone it now

  > If you **do not** see the output above, then clone the CSB repo by entering the following commands:

    ```bash
        git clone git@github.com:tamucc-comp-bio/CSB.git
    ``` 

  > You should see the following output:

    ```bash
    Cloning into 'CSB'...
    remote: Enumerating objects: 1005, done.
    remote: Total 1005 (delta 0), reused 0 (delta 0), pack-reused 1005 (from 1)
    Receiving objects: 100% (1005/1005), 26.68 MiB | 7.74 MiB/s, done.
    Resolving deltas: 100% (389/389), done.
    ```

  > Goto Step 2 above.

<hr style="height: 0.1px; border: none; background-color: black;">

</p>
</details>

<details><summary>ChromeOS, iOS, Android</summary>
<p>

 Launch a CodeSpaces VM Using the [Lecture 5 CodeSpaces VM Link](https://classroom.github.com/a/U1sx189C)
 
 Follow the Win/Mac/Linux instructions above

 </p>
</details>


---

## Lecture Activities

We will not use [`R Studio`](https://posit.co/download/rstudio-desktop/) today.  I want you to use the terminal to run `R` for now.  I will introduce `R Studio` in a future lecture.

___

<details><summary>What is R?</summary>
<p>

[`R`](https://cran.revolutionanalytics.com/) is a powerful statistical computing language

![](Week05new_files/R.png)

* Free
* Open source
* Popular among biologists
* Almost any analysis is available for free
* Easy to use
* Flexible
* Command line interface
* Linux, Win, Mac

___
</p>
</details>


<details><summary>Checking to see if you have R</summary>
<p>

> [!NOTE]
> there are differences here if you have a Mac or Windows computer.

To check if you have `R`, goto your terminal window and enter the following command:

```
$ R
```

If you see this (or similar), then R is installed and you can proceed.  You should have a version at least as new as that listed below.

```
$ R

R version 4.4.2 (2024-10-31) -- "Pile of Leaves"
Copyright (C) 2024 The R Foundation for Statistical Computing
Platform: x86_64-pc-linux-gnu

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

>
```

If you see this message (or something similar) then you need to install `R`

```
Command 'R' not found, but can be installed with:
```

___
</p>
</details>

<details><summary>Install R</summary>
<p>

Consult the [Install R Instructions](https://github.com/tamucc-comp-bio/how_to/blob/main/install_r.md) in the [How to Set Up Your Computer for Computational Biology](https://github.com/tamucc-comp-bio/how_to/blob/main/howto_setup_computer.md) tutorial

___
</p>
</details>

<details><summary>Running R from terminal</summary>
<p>

To run `R`, just type `R` and hit your enter/return key

```
$ R

R version 3.6.3 (2020-02-29) -- "Holding the Windsock"
Copyright (C) 2020 The R Foundation for Statistical Computing
Platform: x86_64-pc-linux-gnu (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

>
```

That is it, you are in an `R` shell, and `bash` commands will no longer work.  Notice the command prompt is now a `>` instead of a `$` or a `%` depending on your computer.

---
</p>
</details>

<details><summary>Exiting R Shell</summary>
<p>

The keys `ctrl+d` will exit the R shell. You will be prompted to save your session.  If you say yes, all of your work will be saved and available when you open the R shell again.

Now that you see how to enter and exit the R shell, enter the R shell again.

```bash
$ R

>
```

---
</p>
</details>

<details><summary>Arithmetic in R</summary>
<p>

R is built for statistics and so has all of the mathematical operations that you would expect from a calculator, and much more.

To do arithmetic, simply type in the mathematical statement to calculate and hit enter.

```R
> 34+5
> 34 + 5
> 34 - 5
> 34 * 5
> 34 / 5
> 34 %% 5
> 34 %/% 5
>
```

`+`		Addition

`-` 	Subtraction

`*`		Multiplication

`/`		Division

`^`		Exponentiation

`%%`	Modulo (remainder from division)

`%/%`	Integer Division

---
</p>
</details>

<details><summary>Equalities & Logic in R</summary>
<p>

R can compare values and return either `TRUE` if the statement is true or `FALSE`.  

```R
34 == 5
34 != 5
34 >= 5
34 <= 5
34>5 | 34<5
34>5 & 17>3
```

`==`	Equal to

`!=`	Not equal to

`>`	Greater than

`<`	Less than

`>=`	Greater than or equal

`<=` 	Less than or equal

`&`	And

`|`	Or

`!`	Not

---
</p>
</details>

<details><summary>R Variables</summary>
<p>

Variables hold data. There are different types of data that can be stored. Here we start by discussing *_values_*.

* *_Values_* are numbers or strings

* *_Values_* can be assigned to variables using <-

The name of a variable can be almost anything you want, but try to avoid punctuation other than `.` or `_` and do not begin a variable name with a number.

```R
# put the value -1.2345 into a variable named 'x'
> x <- -1.2345

# put the value "Hi" into a variable named 'greeting'
> greeting <- "Hi"

```

> [!NOTE]
> numbers should not be quotified, but character strings need to be quotified

You can view the contents of variables by simply typing their name
```R
> x
[1] -1.2345
> greeting
[1] "Hi"
```

Clear all variables:   

```
rm(list=ls())
```

---
</p>
</details>

<details><summary>R Data Types</summary>
<p>

`integer`		Whole Numbers

`numeric`		Real Numbers

`complex`		Complex Numbers

`logical`		TRUE or FALSE

`character`	String

You can specify a data type for a variable as follows where you replace "DataType" and "NameOfVariable" with the appropriate data type and variable name:

```
# do not type this, it is pseudo code
as.DataType(NameOfVariable)
```

Try it out by creating the following variables

```R
> z <- as.numeric(x^2)
> y <- as.character("Bye")
> q <- as.complex(1+3i)
> r <- 3==4
```

> [!NOTE]
> that R will automatically choose a data type if you do not specify one.  It usually gets the data type right, but not always.

We can query the data type of a variable using `is.type(variable)`

```R
> is.numeric(x)
> is.complex(x)
> is.character(greeting)
> is.complex(q)
```


---
</p>
</details>

<details><summary>Mathematical Functions in R</summary>
<p>

`abs(x)`			absolute value
`sqrt(x)`			square root
`ceiling(x)`		round up
`floor(x)`			round down
`trunc(x)`			remove decimals
`round(x,digits=n)` 	round x to n digits
`cos(x)`, `sin(x)`, `tan(x)`, etc	trig
`log(x)`			natural log
`exp(x)`			ex
`log10(x)`			base 10 log

```R
# delete all variables
> rm(list=ls())

> x <- -1.234

> abs_x <- abs(x)
> abs_x

> sqrt_abs_x <- sqrt(abs_x)
> sqrt_abs_x

> floor(x)
> floor(abs_x)

> trunc(x)
> trunc(abs_x)

> y <- round(x,2)
> y

> cos_y <- cos(y)
> cos_y

> z <- log(abs(y))
> z

> exp_z <- exp(z)
> exp_z
```

---
</p>
</details>

<details><summary>R Data Structures: Vectors</summary>
<p>

* Data structures store your data

* Simplest data structure is a single element

* A vector is a collection of elements

 * 1, 2, 3, 4, 5, 6

* Vectors can be specified using `c()` or `seq()` or `rep()`

* Particular values in the vector can be specified by their index `[index_num]`

```R
rm(list=ls())
1:6
x <- c(1:6)
y <- c("a", "B", "c", "D")
y[3]
z <- seq(1, 40, 4)
z
z[3:6]
z[c(2,8,10)]
```

---
</p>
</details>

<details><summary>R Statistical Functions for Vectors</summary>
<p>

A variety of statistical functions are available in R. Here are a few:

`length(x)`	number of elements
`min(x)`		minimum
`max(x)`		maximum
`sum(x)`		sum, +
`prod(x)`		product, *
`median(x)`	central value
`mean(x)`	average
`summary(x)`

```R
length(y)
min(x); max(x)
sum(x); prod(x)
median(z)
mean(z)
var(z)
summary(z)
```

</p>
</details>

---

### [Mind Expander 8.1](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMFpONVRLSkNYUU9VQ1RXVzhGODBPTFM1UC4u) If you have a TAMUCC email address, use this link to receive credit
* [Mind Expander 8.1 (Outside TAMUCC)](https://forms.office.com/r/t1Ljzp9FAN)

___

<details><summary>Overview of R Data Structures</summary>
<p>

A [data structure](https://en.wikipedia.org/wiki/Data_structure) is a container for data with a particular format.

* Element		-	a single value or string

* Vector		-	several elements of same data type

* Matrix		-	2-dimensional table of elements of same data type

* Array		-	3-dimensional table of elements of same data type

* Data frame	-	2-dimensional table of elements, different data types

* List		-	several elements or data structures of any type

---
</p>
</details>

<details><summary>R Data Structures: Matrix</summary>
<p>

`matrix(v,r,c,byrow=FALSE)`

create matrix, v=vector of values, r=#rows, c=#cols,

if `byrow=TRUE` then values are filled in by row

Matrix math

* %*%		matrix product

* solve()	matrix inverse

* diag()	diagonal values

* t()		transpose

Matrix functions

* dim()		dimensions, rows cols

* nrow()	# rows

* ncol()	# cols


```R
rm(list=ls())
x <- c(1, 2, 3, 4)
matrix(x, 2, 2)
matrix(x, 2, 2, byrow=TRUE)
A <- matrix(x, 2, 2)
A %*% A
solve(A)
diag(A)
B <- matrix(1,3,2)
B
t(B)
B %*% t(B)
dim(A)
dim(B)
nrow(B)
ncol(B)
```

Matrix elments are indexed by row and col.

* `matrixName[rowNum,colNum]`

Arithmetic functions are typically applied to all elements in matrix

* `sum()`, `mean()`, etc…

```R
Z <- matrix(1:9, 3, 3)
Z     #whole matrix
Z[1,] #vector with first row
Z[,3] #vector with third column
Z[1:2, 2:3] #submatrix
Z[c(1,3), c(1,3)] #submatrix
mean(Z)
```

---
</p>
</details>

<details><summary>R Data Structures: Array</summary>
<p>

`array(v,dim=c(row,col,m))`

* create array, v=vector of values, row=#rows, col=#cols, m=#matrices

Number of elements in `v` should equal `row*col*m`

Most matrix functions work on arrays

* `dim()`; `nrow()`; `ncol()`

Subsetting arrays similar to matrices

* `array[row,col,matrix]`


```R
rm(list=ls())
M <- array(1:24, dim=c(4,3,2))
M
dim(M)
#return first matrix as matrix
M[,,1]  
#return first matrix as array
M[,,1, drop=FALSE]
```

---
</p>
</details>

<details><summary>R Data Structures: List</summary>
<p>

Used to store elements of different types and structures, e.g. vectors, matrices, etc

`list(x=v1, y=v2, …)`

create list, x=name of 1st data structure, v1=value(s), y=name of 2nd data structure, v2=value(s)

Referencing specific values is similar to vectors, matrices, and arrays, but names can be used as well as indices.  

Number of brackets specifies hierarchical level of data

* first set of brackets are top level in hierarchy


```R
rm(list=ls())
list(1,"A",3000)
mylist <- list(Names=c("a","b","c","d"),
               Values=c(3,1,2))
mylist
mylist[[1]]       #first item in list
mylist[["Names"]] #item named "Names"
mylist$Values     #item named "Values"
mylist[[1]][4]    #4th element of 1st item

```

---
</p>
</details>

<details><summary>R String Manipulation</summary>
<p>

There are several tools for manipulating text strings.  Here are a few examples

`strsplit`   divide string into list

`substr`        return part of string

`sub`                substitute charcters

`paste`           join strings into 1

`nchar`           return number of characters

`toupper`  change case

`tolower`  change case


```R
rm(list=ls())
x <- "Sample-36"
strsplit(x,'-')
substr(x, start=8, stop=9)
sub("36", "39", x)
paste(x, "is smaller", sep=" ")
nchar(x)
toupper(x)
tolower(x)
```

---
</p>
</details>

<details><summary>R Data Structures: Data Frame</summary>
<p>

A data frame holds "tidy" data

Like a spreadsheet, each column is a type of categorization or measurement and each row is a different sample.  

Each column can have a different data type.

We can load an example data frame included with R called trees.  

```R
rm(list=ls())
data(trees)   #load example data frame
str(trees)    #structure of data frame
ncol(trees)   #num cols
nrow(trees)   #num rows
head(trees)   #display first few rows
trees$Girth   #get column
trees$Girth[1:5] #get 1st 5 rows of col Girth
trees[1:5,1]    #get 1st 5 rows of 1st col
trees[1:5,]$Girth #get 1st 5 rows of col Girth
colnames(trees) <- tolower(colnames(trees)) # change column names to all lowercase
str(trees)
```

---
</p>
</details>

### [Mind Expander 8.2](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlURDZQWkY5U1VSWU84WDU5Sk1HWE80NjdVVy4u)

* [Mind Expander 8.2 (Outside TAMUCC)](https://forms.office.com/r/YiLKYYguir)

___


<details><summary>R Working Directory</summary>
<p>

Before you start reading and writing files, it is important to know where the working directory is

`getwd()`  shows where you are, like `pwd` in `bash`

`setwd(“path”)`	changes where you are, like `cd` in `bash`

> [!NOTE]
> root in windows is `C:/` rather than `/`

```R
rm(list=ls())

# where ever you were in bash when you opened R is where you will be in R
getwd()

# change working directory to CSB/r/sandbox
setwd("~/CSB/r/sandbox")
getwd()

```

---
</p>
</details>


<details><summary>R Reading in Data from File</summary>
<p>

You will typically read in your data from a comma or tab delimited file.  It is read in as a data frame by default

Comma delimited files:

	`read.csv(“MyFile.csv”)`

	`read.csv(“MyFile.csv”, header=TRUE) #csv has col headers`

	`read.csv(“MyFile.csv”, sep=“;”) #separator is semicolon`

	`read.csv(“MyFile.csv”, skip=5)   #skip 1st 5 lines`


Tab delimited files: `read.table()`

See the help pages for both `read.csv` and `read.table` for complete functionality


```R
help(read.csv)
# to exit type 'q'
```

We will read  `H938_Euro_chr6.geno` into a variable called `ch6` in R.

```R
#read in data
#make sure you use the correct path for your computer
ch6 <- read.table("../data/H938_Euro_chr6.geno", header=TRUE)
str(ch6)
dim(ch6)
head(ch6)
tail(ch6)

```

* This file contains 7 columns

 * CHR – chromosome

 * SNP – single nucleotide polymorphism

 * A1 – allelic state 1

 * A2 – allelic state 2

 * nA1A1 - # homozyg A1

 * nA1A2 - # heterozyg

 * nA2A2 - # homozyg A2

 ---
 </p>
 </details>

<details><summary>R Writing Data</summary>
<p>

You will typically write a dataframe to a csv or tab delimited file.

Comma delimited files (this is pseudo code, do not type in):

`write.csv(MyDF, “MyFile.csv”) `

#don’t overwrite

`write.csv(MyDF, “MyFile.csv”, append=TRUE) `

#no header row

`write.csv(MyDF, “MyFile.csv”, col.names=FALSE)`

See documentation for write, write.csv, write.table for full functionality

Here we will save the file we just read into the variable `ch6` as a new comma delimited file named `H938_Euro_chr6.csv`

```R
write.csv(ch6, "H938_Euro_chr6.csv")

# view files in present working directory
list.files()
```

---
</p>
</details>



### [Mind Expander 8.3](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUQTRGOTA5UDRZMzlPSjEwTUxCVzBIOEdKRi4u)
* [Mind Expander 8.3 (Outside TAMUCC)](https://forms.office.com/r/srFGhBuqCD)
___


