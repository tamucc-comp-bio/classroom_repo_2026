# Computational Skills for 21st Century Biologists
#### BIOL 4360, MARB 6360
#### Department of Life Sciences, Texas A&M University - Corpus Christi

---

_bookmark this webpage_

---

[FULL SYLLABUS](syllabi)

[RESOURCES](resources/README.md)

<details><summary>OVERVIEW</summary>
<p>

This is a 3-credit course for graduate students that introduces the powerful open-source computing tools that are used in biological research for the creation, organization, manipulation, processing, analysis, and archiving of both small data sets and “big data”. This course is designed to prepare and enable students to use computational tools for biological applications in advanced courses and independent research projects. The primary topics covered are: data formats and repositories, command line Linux computing and scripting, regular expressions, super-computing, data wrangling and visualization with R (tidyverse), computer programming with PYTHON, version control and dissemination of scripts and programs with git and GitHub, and typesetting with markdown.

</p>
</details>


<details><summary>STUDENT LEARNING OUTCOMES</summary>
<p>

Upon the successful completion of this course, students should be able to:

1.	Recognize, describe, and organize data into “tidy” data structures
2.	Locate scientific data repositories and download data
3.	Operate UNIX/LINUX (super)computers from command line
4.	Construct and modify computer programming/scripting logic structures for processing biological data
5.	Describe and use regular expressions to query data
6.	Use version control software (git) in coordination with GitHub to organize and manage projects
7.	Typeset with MarkDown
8.	Use the most popular open-source tools for biological data manipulation
	a.	Shell scripting (bash)
	b.	Statistical computing (R, tidyverse)
	c.	Scientific computing (python)
9.	Use large language models effectively to assist in data processing.


</p>
</details>

<details><summary>INSTRUCTIONAL METHODS AND ACTIVITIES</summary>
<p>

Computation for 21st Century Biologists will convene on Fridays for 2.5 hours.  Class periods will involve interactive lectures that require each student to have a computer designed for content creation (Linux, OSX, Windows, not chrome, not iOS, not Android). Homework exercises will embellish upon concepts addressed in lecture. Participation involves attending lectures and performance on unannounced quizzes.  Weekly Assignments will be given to reinforce concepts covered in lectures and encourage students to start using computational tools.  Exams will be used to evaluate comprehension of the materials covered in lectures and assignments. For undergraduates only, a comprehensive Final Exam will be used to assess the learning objectives detailed above.

Rather than having a final exam, graduate students are expected to complete a Final Project involving the automation of the manipulation and/or analysis of data, This project, including the code should be archived on GitHub.  A report written in Latex or Markdown will be due during the final exam period (this can be a markdown document in your GitHub repo, such as the README.md.  The report should be concise in stating what the problem is, describing the strategy used for the solution, and describing how the code works (be sure to include a flow-chart or outline describing what code does).  Those taking MARB 6360 will give a 10-15 minute presentation during the Final period on their project.

Project examples: automatically process data from experimental apparatus; image analysis; automated reporting of experimental results; downloading and organizing data from online repositories; etc…

</p>
</details>

<details><summary>CLASSROOM & OFFICE LOCATIONS</summary>
<p>

Lectures are F 2-4:30 OCNR 241

Office hours are M-W 4-5:30 on Zoom or TH234

[Grades](https://canvas.tamucc.edu) will be maintained on Canvas.

</p>
</details>

---

## SCHEDULE

---

<!-- This is a hidden comment. It will not be visible in the rendered markdown. 



the hidden section ends here
-->

<details><summary>SECTION 1.  WELCOME TO THE MATRIX</summary>
<p>

### SECTION 1.  WELCOME TO THE MATRIX



* [08/29  Week00  Introduction & Data](lectures/lecture00.md)
  * [Assignment_0  Due, 09/05](assignments/assignment_0_codespaces.md)

* [09/05  Week01 Unix I](lectures/lecture01.md)

  * [Assignment_1,  Due 09/12](assignments/assignment_1.md)

  * [Grad Student Course Project: Ideas, Due 09/13](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUOUo2UVRUMVgwTUlQMlpUQzUzOTIzME9LNi4u)

* [09/12  Week02 Unix II](lectures/lecture02.md)

  * [Assignment_2,  Due 09/19](assignments/assignment_2.md)

* [09/19  Week03 Unix III](lectures/lecture03.md)

  * [Assignment_3,  Due 09/26](assignments/assignment_3.md)

  * [Request Account On TAMUCC Super Computer Due 9/26](http://hpc.tamucc.edu/)

  * [Grad Student Course Project: Plan/Outline, Due 09/26](https://forms.office.com/r/4ANAsh1v5Z)
  
<!-- This is a hidden comment. It will not be visible in the rendered markdown. 
 
    * [Old Link To Grad Student Course Project](https://classroom.github.com/a/VuB4iKjR).  If you started with this link, then just click the link above, clone the 2022 version of this repo, and copy your work from the old repo to the new one.
-->

* [09/26  Week04 Version Control w/ Git](lectures/lecture04.md)

  * [Exam_1,  Due 10/03](https://classroom.github.com/a/aDSDqYJ5)

 <!-- 
 
  * [Grad Student Course Project: GitHub Repo w/ ReadMe, Due 10/03]()


</p>
</details>


 
<details><summary>Quiz Results and Answers</summary>
<p>

* [Quiz 0.0](https://forms.office.com/Pages/AnalysisPage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMlExSEtYN0pTTFVXUzJJUlpYRUNGQzU1Ti4u&AnalyzerToken=xEeP1kCHWBVvr2lUyEOtLJ63vGJEY4Nq)

* [Quiz Wk 2](https://forms.office.com/Pages/AnalysisPage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMjIySEJCNFlSMVJRSUo0SU5HSFNKMVRHWC4u&AnalyzerToken=EoUZORmaO6qYwQJjsmmNDCGnDljXugop)

-->

</p>
</details>



---


<!-- This is a hidden comment. It will not be visible in the rendered markdown. 



This is the end of the hidden section
-->

<details><summary>SECTION 2. DATA WRANGLING AND VISUALIZATION WITH R</summary>
<p>
	
### SECTION 2. DATA WRANGLING AND VISUALIZATION WITH R

* [10/03  Week05 Base R Bootcamp I](lectures/lecture05new.md)

  * [Assignment 5 Due 10/10](assignments/assignment_5.md)

* [10/10  Week06 Base R Bootcamp II](lectures/lecture06new.md)

  * [Assignment 06 Q1, Due 10/17](https://classroom.github.com/a/pq4mmgoC)

  * Install tidyverse in RStudio

	```r
	install.packages("tidyverse")
	install.packages("janitor")
	```

* [10/17  Week07 Data Visualization w/ Tidyverse](lectures/lecture07new.md)

  * Finish Assignment 6 Q 2-3, Due 10/24
  * [Assignment 7, Due 10/24](https://classroom.github.com/a/cnB6wvv6)

* [10/24  Week08 Data Wrangling w/ Tidyverse](lectures/lecture08new.md)

  * [Assignment 8, Due 10/31](https://classroom.github.com/a/exyYQOJC)
     
* [10/31  Week09 R Markdown](lectures/lecture09new.md)

  * [Exam 2 Part 1, Due 11/07](https://forms.office.com/r/yEyDY7DRts)
	* [Exam 2 Part 1 (Outside TAMUCC)](https://forms.office.com/r/TycAwVuDEW)

  * [Exam 2 Part 2, Due 11/07](https://classroom.github.com/a/49v1Y0Af)

 <!--
 
* [10/28 Week09 Data Wrangling Exercises: 1](https://classroom.github.com/a/TiIvuIKy)
 
  * Dr. Bird is at conference, SO PLEASE WORK ON THE EXERCISES ABOVE DURING THE CLASS PERIOD
  * PUSH WHAT YOU COMPLETED AT 4:30, you will be graded on what you complete during the class period.  
  * Then complete the exercises for homework and keep pushing your progress.
    

* 11/11 Week 11 Data Wrangling 2  

	* [Lecture Recording](https://tamucc.zoom.us/rec/share/64wflMEPzxHGxZz2FwtboTfiKnMTiaJI_Pv-oRuqgsiaEHFYGV_Pdqc04eqU7zRa.mzoMZsAcGSIaEtv9), Passcode: !yrj2A=L

* [11/18  Week 12 R Markdown (Lite) & Data Wrangling Exercises](lectures/lecture09new.md)

	* [Lecture Stream](https://tamucc.zoom.us/rec/share/n-vLAmB1U6V9HPmYyPCAEJen-n60O4tDw5HdyGrQR001p8NCAqXcI78eZjfX4frn.1IcylHCClEx-nSSO), Passcode: xqfR0*Bv

  * [Lecture 12 Exercises](https://classroom.github.com/a/fpunalz0) 
	
  * [Exam 2, Due 12/01](https://forms.office.com/r/yEyDY7DRts)

-->

 <!--

  * [Install Anaconda & Jupyter, Due 10/04](http://computingskillsforbiologists.com/setup/basic-programming/), Due 10/04
-->

</p>
</details>

---

<!-- This is a hidden comment. It will not be visible in the rendered markdown. 

<details><summary>SECTION 3. PROGRAMMING WITH PYTHON</summary>
<p>

-->



### SECTION 3. PROGRAMMING WITH PYTHON

* [11/07  Week10 Basic Python Programming I](lectures/lecture10.md)
* [11/07  Week11 Basic Python Programming II](lectures/lecture11.md)
    * [Assignment 11, Due 11/14-21](https://classroom.github.com/a/4JCYaOLH)

* [11/14  Week11 Basic Python Programming II](lectures/lecture11.md)
* [11/14  Week12 Writing Good Code](lectures/lecture12.md)
    * [Assignment 12, Due 12/3](https://classroom.github.com/a/LJPtScMZ)
 
* [11/21  Week12 Writing Good Code](lectures/lecture12.md)
* [11/21  Week13 Scientific Computing](lectures/lecture13.md)


</p>
</details>

</p>
</details>

---

<!-- This is a hidden comment. It will not be visible in the rendered markdown. 


<details><summary>FINAL EXAM: "Welcome to the Desert of the Real"</summary>
<p>

-->

### FINAL EXAM: "Welcome to the Desert of the Real"

We have spent the semester learning:
* the philosophy of data science and linux
* how to control a computer from the command line
* the basics of 3 computer languages that are critical in processing, analyzing, and visualizing biological data
  * `bash`
  * `R`
  * `python`
* version controling our work using git
* distributing our work using GitHub

#### Undergraduates:  
I will issue a Final Exam in much the same way I have issued assignments, in a MS Form and a Repo. You can use all resources at your disposal to complete the exam and extra credit.

* [Final Exam (Python) Due 12/8 11:59 pm](https://forms.office.com/r/uYHNJTdBgQ)  LIVE!

* [Final Exam Extra Credit Due 12/8 11:59 pm](https://classroom.github.com/a/czMTVVik)  LIVE!



#### Graduate Students
Your "final" is completing your independent project by pushing the last changes to your repo by 12/11 9:45 pm.  Graduate students have a presentation also on Friday Dec 5 at 1:45PM in the OCNR 241 (same as the lectures).  Undergrads are invited to attend.   

</p>
</details>




---
