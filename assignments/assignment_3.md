# Assignment 3

## Computer Preparation

Before class, complete the [Computer Setup Checklist](../resources/computer_setup_checklist.md).

Confirm that your terminal, Git, and the `~/CSB` repository work before continuing.

---

## GitHub Preparation

* You should be a member of our class's github classroom. You can tell if you're a member by clicking the "Click on this Link to Initiate this Assignment" below. If you're not a member, then please let me know via email (include your github id) and I'll reinvite you to the classroom. 

* Make sure you are logged into github.

---

## Description of Assignment 

You will be working in bash to manipulate the 3d scans of limpet shells we discussed in class.  

### [Click on this Link to Initiate this Assignment](https://classroom.github.com/a/CWLE574N)

* Begin by cloning your repo to your computer
	* make sure you copy the "ssh" link from your repo (green button, upper right).
   
	```bash
 	# make sure that your pwd is where you think it is so that you can find this location in the future
	git clone InsertSshLinkHere
	```
 
	* recall that on the first day of class we set up an ssh security key between your computer and GitHub. If you didn't do that, you can find the instructions [here](../resources/howto_sshkeys.md) to make an ssh key and then put the public ssh key in your github settings so that you can seamlessly push changes to your homework repo
 
* As you work on the assignment, I recommend testing functions and troubleshooting as necessary after each change you make to the script

* You may work in groups but each student must submit their own work.

---

### Tracking & Recording Progress with `git` and `GitHub`

As you make progress on the assignment, you will be creating and modifying files in your repo.  To have these changes be tracked, you can use git and github.  Every time you accomplish a task, you should log the changes with git and push the changes to github.  This will save and track your progress, allowing you to go back to one of these "save points" should something go very wrong as you progress further into the assignment.  (This will be on the exam, so start practicing this now).

* in your terminal, change directories to the repo for this assignment
* type the following:

```
git add --all
git commit -m "updating my assignment"
git push
```

Note that 
* you can change the `commit` message to whatever you want (the part in quotations, but keep it brief)
* you will have to provide your github username and password for the `push` to `origin master` if you did not set up the ssh key in lecture_0

<details><summary>Detailed Info on Git and GitHub</summary>
<p>

#### What is Git?

Git is a distributed version control system that helps you keep track of changes made to your code, collaborate with others, and is widely used in both academia and the industry.

#### Why Use Git?

1. *Versioning:* Keep track of changes and revert to older versions of code when necessary.
2. *Collaboration:* Work with teammates on the same projects without overlapping each other's changes.
3. *Reproducibility:* Document versions of code that produce specific results.

#### Core Commands: git add, git commit, git push

1. `git add`: Stage your changes for commit
  * What it does: Tells Git that you want to include the changes made in specific files for the next commit.
  * Why: You may not want to commit all the changes you've made at once. git add allows you to select the changes to include.
  * Example:

	```bash
	# only stage changes for a single file
	# note, your present working dir must be inside of a repo for this to work
	git add myfile.txt
	```

	```bash
	# or stage all changes in the current directory
	git add .
	```

	```bash
	# or stage all changes in the whole repo
	git add --all
	```

2. `git commit`: Save your changes to the local repository

  * What it does: Takes the files as they are in the staging area (git add) and stores that snapshot as a unique version in your local repository.
  * Why: It provides a record of changes and an associated message describing those changes, making it easier to understand the development history.
  * Example:

	```bash
	# take a snapshot of all added (staged) changes to the repo
	git commit -m "Implement feature X"
	```

3. `git push`: Update the remote repository on GitHub

  * What it does: Sends the committed changes in your local repository to a remote repository like GitHub.
  * Why: Makes your changes accessible to team members or collaborators. Also, it serves as a backup of your local repository.
  * Example:

	```bash
	# take a snapshot of all added (staged) changes to the repo
	git push
	```

#### A Typical Workflow:

1. Modify your code.
2. Stage the changes: `git add --all`
3. Commit the changes: `git commit -m "Description of changes"`
4. Push the changes to the remote repository: `git push`

By doing this, you're keeping your code versioned, making it easier to collaborate with others, and allowing you or anyone else to understand how the codebase evolved over time.

</p>
</details>

### Submitting Assignment

To submit your assignment, add, commit, and push your changes to github one last time.

