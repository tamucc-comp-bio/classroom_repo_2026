# Week09 R Markdown (Lite) 

###  No assignments were due today

[Lecture Stream](https://tamucc.zoom.us/rec/share/n-vLAmB1U6V9HPmYyPCAEJen-n60O4tDw5HdyGrQR001p8NCAqXcI78eZjfX4frn.1IcylHCClEx-nSSO)

Passcode: xqfR0*Bv

___

## Computer Preparation

Before class, complete the [Computer Setup Checklist](../resources/computer_setup_checklist.md).

Confirm that Git, R, RStudio, and the `~/CSB` repository work before continuing.

You are expected to start this lecture with R Studio open with a fresh and empty text document in the upper left panel and a clean environment.

### *_ADDITIONAL COMPUTER SETUP (NEW FOR TODAY)_* 

R Markdown is a typesetting language that allows you to also incorporate R code chunks.  If you did not notice yet, the solutions for the Data Wrangling chapter of CSB are written in R Markdown.  There are a variety of applications of R Markdown.  The one I have used the most is making a report where the data changes through time, but the layout of figures and text does not change.

> [!CAUTION]
> RMarkdown runs much more slowly than normal R code. If you need the fastest processing possible in R, don't use RMarkdown.

1. For R Markdown to work properly, you need some additional packages installed in R Studio. Realize that R can also process R Markdown scripts from terminal without R Studio.

```r 
install.packages("rmarkdown")
install.packages("knitr", dependencies=TRUE)
install.packages("tinytex")
tinytex::install_tinytex()

library(rmarkdown)
library(knitr)

```

2. (OPTIONAL) As of 2025, RStudio installs a lite version of `pandoc`, so you don't need to install it.  If you want the full featured version of `pandoc`, you can install it on your computer outside of RStudio following the instructions [here](https://pandoc.org/installing.html).  Windows people, do the windows install (the `*.msi` installer, not the `*.zip`). 

3. (OPTIONAL ) As of 2025, [TinyTex](https://yihui.org/tinytex/) can be used to install a lite version of LaTeX and if you followed the instructions above, you've already installed it. A LaTeX package enables the ability to create PDFs and other file types.  TinyTex is a small LaTeX package designed to work with `knittr`. If you want a full featured LaTeX distribution, you should install scientific typesetting software `LaTeX` that operates independently of R and RStudio. Like `Linux`, there are several flavors of `LaTeX`.  For linux: `sudo apt-get install texlive`.  For mac, [install MacTex](https://www.tug.org/mactex/mactex-download.html).  For windows, [install MikTex](https://miktex.org/download) - be sure to install as administrator and run updates.


![](Week09new_files/miktex-updates.png)

> If you are successful, you will be prompted to restart `MiKTex`


---


## I. R Markdown

R Markdown is a flavor of the markdown typesetting language that works specifically with R.  You can use R markdown to create web pages, pdfs, slide shows, and other types of documents.

There is an [R Markdown Chapter in R for Data Science](https://r4ds.had.co.nz/r-markdown.html) that will cover more details than we will here. 

![](https://d33wubrfki0l68.cloudfront.net/61d189fd9cdf955058415d3e1b28dd60e1bd7c9b/9791d/images/rmarkdownflow.png)

<details><summary>Creating an R Markdown Document</summary>
<p>

### Creating an R Markdown Document

In R Studio, make a new R Markdown document using the `File` pulldown menu

* name it `lesson-0`

* use default settings

If you were successful, your document will already be populated with several lines of text and code that fall into three categories.

![](Week09new_files/rmd_layout.png)

Make sure you save the file as lesson-0 into your `CSB/data_wrangling/sandbox` and make sure that you use `setwd()` to set your present working directory to `CSB/data_wrangling/sandbox`.

___

</p>
</details>

<details><summary>Run `lesson-0.rmd` With `knitr`</summary>
<p>

## Run `lesson-0.rmd` With `knitr`

As is our custom in Computational Biology, jump in head first and click the `knit` button above the upper left panel. It will run the Rmd and create an `html` report in a new window.

Next, we will cover the primary sections of the Rmd file.

___

</p>
</details>

<details><summary>YAML Header</summary>
<p>

### YAML Header

YAML stands for YAML Aint Markup Language.

Lines 1-8 in the Rmd are the YAML header, which contains the title of the document and the default output format.  `html` is hyper text markup language, i.e. web pages.  The YAML header is always at the beginning of an Rmd.

Several other characteristics of the Rmd document can be set in the YAML header.  This [tutorial](https://zsmith27.github.io/rmarkdown_crash-course/lesson-4-yaml-headers.html) is pretty good.

---

</p>
</details>

<details><summary>Code Chunks</summary>
<p>


### Code Chunks

Lines 10-12, 20-22, and 28-30 are code chunks.  They start with three tick marks (the key in the upper left of you keyboard) and you can specify the language (r and other languages like python are possible), as well as basic settings of how the output from the code should be handled. For example, you can suppress warnings, error messages, etc.

The output of the code chunks are included in the resulting document.

---

</p>
</details>

<details><summary>Markdown Text</summary>
<p>


### Markdown Text 

Everything else in the Rmd is markdown text if it is not code or YAML.  

For example, line 14 is the first line of text.  The `##` indicates that the text `R Markdown` should be a secondary heading.

Markdown is a class of typesetting languages.  There are broad similarities across markdown languages but there can also be small differences.  This lecture document is written in GitHub markdown.  The markdown in an `Rmd` file has similarities to that in GitHub and other flavors, but can be slightly different and allows you to run R code. 


---

</p>
</details>

<details><summary>R Markdown Resources</summary>
<p>

[Official RMarkdown Tutorial](https://rmarkdown.rstudio.com/lesson-1.html)

[Official R Markdown Reference Guide](https://bookdown.org/yihui/rmarkdown/html-document.html) 

[Official R Markdown Cheatsheet](https://posit.co/wp-content/uploads/2022/10/rmarkdown-1.pdf)

[Zachary Smith's R Markdown Crash Course](https://zsmith27.github.io/rmarkdown_crash-course/index.html)

[R for Data Science: R Markdown Chapter](https://r4ds.had.co.nz/r-markdown.html)

[R Markdown Cookbook - most comprehensive](https://bookdown.org/yihui/rmarkdown-cookbook/)

---

</p>
</details>

<details><summary>Quarto, the New RMarkdown</summary>
<p>

Quarto was spawned from RMarkdown, but can be used with more than just the R coding language.  I think you should know it exists, but we will stick with RMarkdown for this year.  Quarto is very similar to RMarkdown and if you can use RMarkdown, you'll be able to transistion to Quarto easily.

To use quarto, you have to [install the Quarto CLI](https://quarto.org/docs/get-started/). But again, we will not delve further into Quarto in this course.

[R for Data Science: Quarto Chapter](https://r4ds.hadley.nz/quarto.html)

---

</p>
</details>

<details><summary>R Markdown Tutorial</summary>
<p>

### [Lesson 1](https://rmarkdown.rstudio.com/lesson-1.html)

R Markdown has a very nice lesson plan that we will use to review its features.  We will link to the lesson below and then work within the R Markdown website. There is also the very thorough [R Markdown Crash Course](https://zsmith27.github.io/rmarkdown_crash-course/index.html) by Zachary M. Smith (I love `open source`) which goes beyond the scope of this class.

Files needed for R Markdown lesson are in the `Week09new_files` dir in [the repo for todays lecture](https://classroom.github.com/a/57Ld7XZw), otherwise they are here:

* [all *.Rmd` files here](https://github.com/tamucc-comp-bio/classroom_repo_2025/tree/main/lectures/Week09new_files)

---

</p>
</details>

---

## II. Complete Assignment 8, Data Wrangling

Complete these exercises and push your changes to the repo before the end of class.


