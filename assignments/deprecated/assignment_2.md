# Assignment 2 

---

## Computer Preparation

Before class, complete the [Computer Setup Checklist](../resources/computer_setup_checklist.md).

Confirm that your terminal, Git, and the `~/CSB` repository work before continuing.

---

## Description of Assignment

1. Reading: [Wilson_et_al_2014_Best_practices_for_sci_comp](../literature/Wilson_et_al_2014_Best_practices_for_sci_comp.pdf)

2. Complete [Mind Expander 01.04](https://forms.office.com/r/uvi6cGMSMJ)

3. *OPTIONAL*: In Software Carpentry, complete The [Unix Shell Sections 5-6](https://swcarpentry.github.io/shell-novice/)

4. Work through *Computer Programming with `bash` (CSB 1.7-1.9) in [Lecture_02](../lectures/lecture02.md)

<details><summary>5. Complete exercises 1.10.2 and 1.10.3</summary>
<p>

Then, complete the exercise(s) below by answering the question(s) in the online form and submitting.  You must be logged into your TAMUCC email account to have your identity attached to your answers. 

You may work in groups, but each person must fill out the online answer form.

The exercises in the online forms closely follow those in the book.  I do make minor modifications and provide tips in the online form.  

&#x2757; IMPORTANT  _To ensure that your work is saved, **I highly recommend that you first record your answers in a text document in either Notepad++ or BBedit and save them to your computer**.  For an excellently formatted example, see the solutions provided by the book in `CSB/unix/solutions`._ 

* [Exercise 1.10.2 Hormone Levels in Baboons](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUQldJQTVHMTlYMFVYTkhZSDBZR1A0Q1E2Ny4u)

* [Exercise 1.10.3 Plant-Pollinator Networks](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMlpVSUQ0U1hTSFZERDE1WUdZWjRYUlhaWi4u)

</p>
</details>

---


### Extra Credit, worth 1 whole assignment  

Complete Exercise 1.10.4 Data Explorer (data from Buzzard *et al.*, 2016), and submit script by updating your repository (see below). You may work in groups but each student must submit their own work.

[Click on this Link to Initiate this Assignment](https://classroom.github.com/a/bpGFIcSJ)

Please try to at least click the link at the end of this paragraph and let me know if you run into any problems getting the assignment or cloning the repo because Assignment 3 will be issued this way.  For those of you that do this, I'll extend the due date for another week ([let's see if anybody reads this](https://forms.office.com/r/SyUUFzLLgg)).

Hints:

* Start by cloning this repository to your computer
	* make sure you copy the "ssh" (not the "html") link from your repo (green button, upper right).
	```bash
	git clone InsertSshLinkHere
	```
	* recall that in [lecture 0](../lectures/lecture00.md) we set up an ssh security key between your computer and github.  This makes it so that you don't need usernames, passwords, and tokens to interface with github.  

* **_I highly recommend that you create your script in a text document in either Notepad++ or BBedit_**.  

* Make a copy of the `Buzzard2015_pseudo.md` document and a give it a new name as requested in the exercise or of your choosing.  It should end with an `.sh`

  * "Comment" the pseudo code using `#`
  
* Add a shebang!

* Use your terminal to play in this repository and construct/troubleshoot code

* Copy and paste working code into your script in your text editor

* I have noticed that the Win10-Ubuntu terminal does not like when you copy properly formatted code with leading tabs and spaces from your script in the text editor and paste it at the command line

  * You can, however, copy and paste the lines without the leading tabs and spaces
  
  * You can also create the script in the terminal using `nano` and paste in your properly formatted code to then run the script
  
    * _*Win10 only*_, it is critical that you do not modify files in your Ubuntu directory structure with Win10
	  * You can, however, move to your Win10 directory structure from the Win10-Ubunutu terminal and manipulate files as you wish `cd /mnt/c/Users/YOURUSERNAME`

### To `push` your changes to your repository on GitHub, and thus *_submit the assigment_*, do the following

* change directories to the directory for this assignment

* type the following while your `pwd` is inside of the assignment repo:

	```
	git add *
	git commit -m "updating my assignment"
	git push origin master
	```

Note that 
* you can change the `commit` message `"updating my assignment"` to whatever you want (the part in quotations, but keep it brief

* you will have to provide your github username and password for the `push` to `origin master`
