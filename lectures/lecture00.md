# Week_00 INTRODUCTION & DATA

## [Lecture_00 Stream 2025](https://tamucc.zoom.us/rec/play/B7cHO6zKPZGA2g2zk5NgpKRFw8AOedLVmBpiYd4pCO43t6v0IjI-aujNAfUYmJa9zlSZzKXNBG_c3NHx.0rIgPsGVSXyz7PW3)

Passcode 2025: sM=xN%0T


## [Lecture_00 Slides](Week00_files/Lecture00_Overview_BigData.pdf)

We will begin the lecture with the ppt presentation.  At the conclusion of the presentation, we will complete the following exercises prior to the end of the class period to get your computers set up for next week.  You should not leave the class until you have completed these exercises because if you have trouble, I can help you now and we will not spend time on this next week.

---

## IN CLASS EXERCISES

Do not begin these until we complete the lecture. You need to complete them in order.

### Log into [GitHub](https://github.com/)
[Create an Account](https://github.com/tamucc-comp-bio/how_to/blob/main/howto_github_acct.md) if you do not have one. `git` is a version control software and `github` is a cloudstorage server that serves as the hub of collaborative projects and it is where the master copy of your data and data analysis scripts lie. Github makes following core data science philosophy easy. The philosophy is, after data is digitized, all manipulations of the data should be documented and executed in code. This facilitates transparency, reproduction of methods, and we are progressing toward a day when you’re scientific research papers will be rejected if you don’t provide the scripts used to process your data. https://www.freecodecamp.org/news/git-and-github-for-beginners/ .

---


### [In Lecture Quiz 0.0](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMlExSEtYN0pTTFVXUzJJUlpYRUNGQzU1Ti4u)

   [Quiz 0.0 for Non-TAMUCC Students](https://forms.cloud.microsoft/r/DUdbALPWZ3)
   
During most lectures we will take a few minutes at least once and ask you to apply the concepts addressed in lecture. You will be expected to have the class's GitHub repository open in a web browser to follow the links to the questions.  You must be logged into [TAMUCC's webmail](https://outlook.tamucc.edu)

---

### Setup [GitHub CodeSpaces](https://github.com/features/codespaces)

Complete the tasks in the [How to Set Up GitHub CodeSpaces](https://github.com/tamucc-comp-bio/how_to/blob/main/howto_github_codespaces.md) guide.

Be sure to turn off your codespace before moving to the next exercise so you don't waste you alloted time allocation.

---


<!-- This is a hidden comment. It will not be visible in the rendered markdown. 

### Make Your Launch HPC Account

Complete the tasks in the [Accessing Launch HPC](https://hprc.tamu.edu/kb/User-Guides/Launch/Access/#no-ssh-login) guide and _BOOKMARK THE GUIDE IN YOUR WEBBROWSER_ because it has the [Launch Portal login link](https://hprc.tamu.edu/kb/User-Guides/Launch/Access/#no-ssh-login).  

Note that your account needs to be approved manually in College Station so it will probably not be operational today.

---

-->

### Setup Your Computer for Computational Biology

Complete the tasks in the [How to Set Up Your Computer for Computational Biology](https://github.com/tamucc-comp-bio/how_to/blob/main/howto_setup_computer.md) guide.

---

### In the Terminal on Your Local Computer Check to confirm you have `git` installed

Open your terminal, type in "git" and then hit <ENTER/RETURN>:

```bash
git
```

and then you see this:

```
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           [--super-prefix=<path>] [--config-env=<name>=<envvar>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone     Clone a repository into a new directory
   init      Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add       Add file contents to the index
   mv        Move or rename a file, a directory, or a symlink
   restore   Restore working tree files
   rm        Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect    Use binary search to find the commit that introduced a bug
   diff      Show changes between commits, commit and working tree, etc
   grep      Print lines matching a pattern
   log       Show commit logs
   show      Show various types of objects
   status    Show the working tree status

grow, mark and tweak your common history
   branch    List, create, or delete branches
   commit    Record changes to the repository
   merge     Join two or more development histories together
   rebase    Reapply commits on top of another base tip
   reset     Reset current HEAD to the specified state
   switch    Switch branches
   tag       Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch     Download objects and refs from another repository
   pull      Fetch from and integrate with another repository or a local branch
   push      Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
See 'git help git' for an overview of the system.
```

you are good to go.  Otherwise, follow [the instructions for both Windows and Linux (Ubuntu Terminal)](https://computingskillsforbiologists.com/setup/)

---


### Clone the "Computing Skills For Biologists" text book's repository to your computer

We will use the open source files that accompany the CSB text book in some lectures and assignments.

1. Open a terminal window
	* For Win laptops, use `Windows Terminal` to open Ubunutu.  
	* For Mac laptops, open your `Terminal`.
	
2. Run the code line by line in the code block below 
```bash
# check that you're in home dir, you should be there when you log in
pwd

# if you are not in your home dir, then move there
cd ~

# if pwd does not return `/home/yourusername` then let Dr. Bird know
pwd

# clone the CSB repository to your home dir
git clone git@github.com:tamucc-comp-bio/CSB.git
```

The repository is named CSB, and it contains all of the example files and directories necessary to conduct the exercises in the text book. Note that this includes solutions to all of the exercises in the book also.


