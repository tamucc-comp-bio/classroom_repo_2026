# Assignment 2 

---

## Computer Preparation

> [!IMPORTANT]
> Make sure your computer is ready to complete the assignment

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

 Launch a CodeSpaces VM Using the [Lecture 0 CodeSpaces VM Link](https://classroom.github.com/a/5tvV4uls)
 
 Follow the Win/Mac/Linux instructions above

 </p>
</details>

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
