# Week04 How to use ChatGPT and How to use Version Control

> [!IMPORTANT]
> [Assignment 3](../assignments/assignment_3.md) is due at the beginning of this lecture

> [!NOTE]
> The [Lecture Stream 2025](https://tamucc.zoom.us/rec/share/wazoE-XXaH84n0pqtn45EtU8fZ_WAD2qgkCCxJ0fbZCe2dKjh3s9uPu7ipd01PLi.1TpSh9UycOt00AEZ )
Passcode: 727zJ?xU

https://tamucc.zoom.us/rec/share/wazoE-XXaH84n0pqtn45EtU8fZ_WAD2qgkCCxJ0fbZCe2dKjh3s9uPu7ipd01PLi.1TpSh9UycOt00AEZ

___

## Computer Preparation

Before class, complete the [Computer Setup Checklist](../resources/computer_setup_checklist.md).

Confirm that your terminal, Git, and the `~/CSB` repository work before continuing.

---

## In Class Activities

### I. [Quiz 4](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUNU1IUUg4Nzc1SU9KQVNRTVc0TU0xMFI1Sy4u)

[Quiz 4 Non-TAMUCC Students](https://forms.cloud.microsoft/r/yHephrmEfk)

---

### II. [Assignment 3](../assignments/assignment_3.md) Triage

We will review your burning questions about the assignment.

---

### III. ChatGPT

Let's use ChatGPT to solve `assignment-02-xc`.  See my [session log with ChatGPT](https://chat.openai.com/share/b6a5adb2-bd6b-4fd6-ab49-d585b2d0bb12)
<details><summary>ChatGPT Hacks!</summary>
<p>

Here are some &#x1F4A1; tips to help you get the most out of working with ChatGPT to successfully complete computational tasks:

0. **Start Each Problem with a New Conversation**  
   Guide ChatGPT by clearly explaining what you want, rather than expecting it to know everything. If something doesn't work, give feedback and iterate.

1. **Treat ChatGPT as an Assistant, Not an Authority**  
   Guide ChatGPT by clearly explaining what you want, rather than expecting it to know everything. If something doesn't work, give feedback and iterate.

2. **Provide Context Clearly**  
   Describe your environment (e.g., bash, R, Python) and tools you're using. This helps ChatGPT give relevant answers.

3. **Share File Structures and Data Layout**  
   Show the directory structure and contents of key files. ChatGPT can give more targeted help when it understands the layout of your project.

4. **Explicit File, Directory, and Column Naming**  
   Name files, directories, and columns in a way that a human could interpret without guidance. It makes it easier for ChatGPT (and humans!) to follow your work.

5. **Give Incremental Information**  
   When asking for help with scripts or code, start with small parts, share outputs, and iterate. This helps avoid errors and keeps solutions accurate.

6. **Ask for Clarifications and Explanations**  
   Don't hesitate to ask why certain steps are taken, or for explanations of code or concepts. Use this opportunity to learn, not just solve problems.

7. **Test Assumptions**  
   When creating scripts or analyzing data, verify that ChatGPT's suggestions work with your specific data by testing them. Provide examples of your data or run the commands yourself.

8. **Be Explicit About Errors and Results**  
   If a suggestion doesn’t work, provide the exact terminal code and associated error message or describe what went wrong. ChatGPT can provide a better solution if it understands what didn’t work.

9. **Use ChatGPT for Planning**  
   When tackling large tasks, ask ChatGPT to help you plan steps before diving into code. You can also have it review your process.

10. **Request [Unit Tests](https://en.wikipedia.org/wiki/Unit_testing) and [Edge Case Testing](https://en.wikipedia.org/wiki/Edge_case)**  
    Ask ChatGPT to create unit tests or edge case scenarios to ensure the robustness of scripts.

11. **Provide Problem Instructions in Detail**  
    When seeking help on exercises or tasks, provide as much detail as possible. This ensures ChatGPT understands what the end goal is.

12. **Iterate on Responses**  
    Don’t expect the first response to always be perfect—it's common to go through a few iterations before reaching the best solution.

13. **Don't Go Through Too Many Iterations**
    If you go through several cycles of ChatGPT getting it wrong, start a new conversation and change your approach. I've found that ChatGPT can get stuck and changing the prompts can provide different results. 

14. **Include Relevant Logs and Outputs**  
    When debugging or troubleshooting, share logs, errors, or partial outputs with ChatGPT. This makes it easier to pinpoint issues.

15. **Use Examples to Clarify**  
    When asking for help with coding or data manipulation, providing a small, clear example dataset or code snippet can help ChatGPT give more accurate responses.

16. **Ask for Alternative Solutions**  
    There are often multiple ways to solve a problem. Ask ChatGPT for alternative solutions to compare performance, readability, or simplicity.

17. **Use ChatGPT to Help Document Code**  
    After writing code, ask ChatGPT to help generate comments or documentation for your scripts. This can improve the clarity of your code for both yourself and others.

18. **Understand the Limitations of ChatGPT**  
    ChatGPT doesn't have live access to the internet and is trained on data up until a certain point. It may not have the latest updates on libraries or tools. Always verify responses, especially for new or cutting-edge technologies.

19. **Be Specific with Formatting Requests**  
    When requesting code, markdown, or other formatting (e.g., tables, lists), be explicit about how you'd like ChatGPT to present the information.

20. **Break Complex Problems into Smaller Pieces**  
    For more complicated problems or multi-step workflows, break the task down and ask ChatGPT to help with individual parts. This ensures better focus and less chance of overwhelming the model (or yourself).

21. **Ask for Error Handling**  
    When writing scripts or code, request that ChatGPT includes error handling or edge case considerations to make your code more robust.

22. **Use ChatGPT to Learn New Skills**  
    Beyond problem-solving, ChatGPT can also be used as a tutor. Ask it to explain key concepts, walk you through examples, or provide suggestions for further learning on specific topics.

23. **Cross-check with External Resources**  
    While ChatGPT can give helpful guidance, it's important to cross-check its responses with external documentation, especially when working in critical or unfamiliar areas.

</p>
</details>

---

<details><summary>Vibe Coding</summary>
<p>

Vibe Coding, [coined by Andrej Karpathy in Feb 2025 on X](https://x.com/karpathy/status/1886192184808149383), is a specific strategy for integrating LLM into the code creation, but has become the widely adopted term for employing LLM to complete coding tasks, regardless of the strategy.

---

## What Is Vibe Coding?

**Definition:** An improvisational, intent‑first coding style where you state your goal in natural language, generate or sketch code fast (often with an LLM), run it, read errors/output, and iterate in short loops—**then** consolidate into robust artifacts (scripts, tests, docs).

---

**Core loop:**

1. **State the vibe** (goal + constraints) in plain language.
2. **Generate a first pass** (you/LLM) and run it on a small sample.
3. **Tight iteration:** paste errors/outputs back; refine prompts/code.
4. **Snapshot what works**; name functions and files clearly.
5. **Harden:** add flags, checks, docs, and minimal tests.

**Good for:** early exploration, data checks, API pokes, shaping file formats, UI/UX sketches.

**Not for:** final analyses, production pipelines, papers’ main results without tests and documentation.

---

## Responsible Vibe Coding in Science

* **Reproducibility:** always end with a script and a README.
* **Data protection:** never overwrite raw data; keep `data/` read‑only using `chmod`.
* **Traceability:** save commands in a log file; prefer relative paths.
* **Time‑boxing:** decide up front (e.g., 30 minutes) before refactor.
* **Small steps:** run on a tiny subset first.

---

## LLM Copilot Prompts (Templates)

* **Scaffold:** “Write a Bash script with `getopts` that … Use `set -euo pipefail` and helpful error messages.”
	*  `getopts` is a command used in a bash script to read in options such as `-o` when the script is run
 	*  `set -euo pipefail` is a (bash/zsh/ksh) command that makes shell scripts fail fast and catch common bugs
* **Error‑driven:** “Here’s the error + the snippet; fix only what’s necessary and explain the change in one line.”
* **Explain:** “Given this `awk` block, annotate each line with comments.”
* **Refactor:** “Split this long pipeline into named functions with clear variable names.”
* **Docs:** “Draft a concise README with inputs, outputs, and commands to reproduce.”

(Students copy/paste terminal output or error messages back to the model as needed.)

---

## Common Pitfalls & Fixes

* **Overwriting raw data:** enforce outputs to `outputs/` only.
* **No Absolute paths:** relative paths keep repos portable.
* **CSV quoting/comma issues:** use `csvkit` or tsv files for reliable parsing.
* **Unsaved spikes:** capture working commands in scripts immediately.
* **Scope creep:** time‑box spikes; create TODOs for later.

---

## Notes

* Keep directories minimal: `data/`, `bin/`, `outputs/`, `scratch/`.
* Show `tree` to visualize structure.
* For Windows users, use WSL terminal;
* Use `csvkit`, a popular suite of Unix-style CLI tools for converting to and working with CSV file
	* Installation: `sudo apt install csvkit`; `brew install csvkit`
* Demo on a subset first (e.g., `head -n 1001`) to keep iteration fast.
* Emphasize that vibe coding is **a phase**, not a destination.

</p>
</details>

---

<details><summary>Vibe Coding Environments</summary>
<p>

[Gemini CLI](https://github.com/google-gemini/gemini-cli)

![](https://github.com/google-gemini/gemini-cli/blob/main/docs/assets/gemini-screenshot.png)

---

[Codex CLI](https://github.com/openai/codex)

![](https://github.com/openai/codex/blob/main/.github/codex-cli-splash.png)

---

## Structured Vibe Coding

Some best practices in vibe coding are taking shape along with tools like Gemini CLI, Codex CLI, and Claude Code.  I've yet to try these because I'm typcially satisfied with using the "old-fashioned" chat interface, but you might want to give one of these a shot.  Gemini CLI's free version is pretty generous with prompt allowances and features. One important recent development is the birth of the "prompt file".

---

## Prompt File

Prompt files contain basic information about your project to guide the LLM.  They are natively supported by Gemini CLI and others. I think it's good practice to make one even if you're not using a tool like Gemini CLI.

It turns “vibes” into stable constraints the model can’t forget, keeps teams aligned, and makes your LLM runs reproducible (the file is versioned). This is quickly becoming a best practice across vibe-coding write-ups and guides.

**What to put in the file:**

1. Objective (1–3 lines): exact outcome, not a vibe.

2. Inputs/Outputs: file paths, schemas, acceptable ranges.

3. Constraints: tools available (bash, csvkit), runtime limits, no touching data/.

4. Interfaces: CLI flags, expected commands, examples.

5. Mini-evals: a tiny I/O pair to test correctness quickly.

6. Guardrails: failure conditions, logging, reproducibility notes (relative paths, seed, README).

7. Context pointers: where the model should look (folder tree, key files). In Copilot/Gemini, this is exactly what the prompt/system file is for.

Keep it short, structured, and commit it to the repo.

---

## Prompt File Template  (`PROMPT.md`)

```
# Objective
Compute mean, SD, and count of fish `n` by (protected_status × trophic_group) from two tidy CSVs and write `outputs/means_sd_count.csv`.

# Inputs
- data/reef_fish_counts.csv  (site_id, date, habitat, species, trophic_group, n:int)
- data/sites.csv             (site_id, island, depth_m, protected_status)

# Output
- outputs/means_sd_count.csv (protected_status, trophic_group, mean_n, sd_n, count)

# Constraints
- Environment: bash + csvkit; no Python/R.
- Reproducible: use relative paths; never modify files in data/.
- Performance: handle 1e6 rows via streaming where possible.

# Interface
Example:
./bin/summarize_means.sh -c data/reef_fish_counts.csv -s data/sites.csv -o outputs/means_sd_count.csv --filter-trophic=herbivore,omnivore

# Mini-eval
Input (toy): data/toy_counts.csv + data/toy_sites.csv
Expected row: "Protected,herbivore,12.0,4.2,5" present.

# Guardrails
- Exit non-zero if any group has count < 3.
- Validate numeric columns; print row counts to stderr.

# Context pointers
Please read: README.md, bin/summarize_means.sh (if present), `tree` of repo.
```

---

</p>
</details>


---

### IV. Version Control

<details><summary>What is version control?</summary>
<p>

* A tool to record changes to your files and directory structure
  * additions, deletions, changes, etc

---

</p>
</details>

<details><summary>Why use version control?</summary>



* Organize project, especially with multiple people
  * e.g., student, advisor, committee members, collaborators
  * efficient
* Recover old versions of work (undo)
* No need for 10 versions of each of your files

---
</p>
</details>

<details><summary>What is Git?</summary>
<p>

`git` is a version control tool and [`GitHub`](https://github.com) is a website that uses `git`.  `git` is popular, free, open source, and [`GitHub`](https://github.com) is a paid service that is free for educational use.  Fun fact, the [person who made linux os](https://en.wikipedia.org/wiki/Linus_Torvalds) created `git` to version control his and others work on linux.  Thus, `git` is in the "DNA" of linux.

![alt text](Week04_files/gitlogo.jpg)
![alt text](Week04_files/githublogo.jpg)

---
</p>
</details>

<details><summary>Schematic diagram of how Git is used</summary>
<p>

Git is *distributed* and a full copy of the history of changes resides on every instance of the *repository*

![alt text](https://github.com/tamucc-comp-bio/fall_2019/blob/master/lectures/Week04_files/distributedvcs.png)

![alt text](https://miro.medium.com/v2/resize:fit:1386/format:webp/1*pEduJdPky05DeojVGVtPpQ.jpeg)

---
</p>
</details>

<details><summary>Configuring Git</summary>
<p>

Viewing your current `git` settings:

```bash
$ git config --list

user.name=Chris Bird
user.email=cbird808@gmail.com
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
```

Updating your user.name, email, etc...

```bash
$ git config --global user.name "Chris Bird"
$ git config --global user.email cbird808@gmail.com
$ git config --global color.ui true
```

---
</p>
</details>

<details><summary>Getting Help with Git</summary>
<p>

[ChatGPT](https://chatgpt.com/)

[Google Gemini](https://gemini.google.com/)

[duckduckgo search](https://duckduckgo.com/)

```bash
$ git help
$ man git
```

---
</p>
</details>

<details><summary>Initializing a Local Git Repository</summary>



1. Initializing a repository only needs to be done once.  Any directory (dir) can become a `git` repository (repo). `git` cannot version control if you do not make a dir a repo.  Let us make the `~/CSB/git/sandbox/originspecies` directory a `git` repository:

    ```bash
    # TAMUCC COMP BIO ONLY, Run this line
    $ cd ~/CSB/git/sandbox
    
    # WORKSHOPS ONLY, Run this line
    $ cd sandbox
    
    $ mkdir originspecies
    $ cd originspecies
    $ git init

      Initialized empty git repository in /home/cbird/CSB/git/sandbox/originspecies/.git/
    ```

2. Checking the status of a repo:

    ```bash
    $ git status

    On branch master

    Initial commit

    nothing to commit (create/copy files and use "git add" to track)
    ```

---
</p>
</details>

<details><summary>Making and Tracking Changes In a `git` Repo</summary>



1. Create a file called `origin.txt` in your repo as follows:

    ```bash
    $ echo "An Abstract of an Essay on the Origin of Species and Varieties Through Natural Selection" > origin.txt
    ```

2. View file contents:

    ```bash
    $ cat origin.txt

    An Abstract of an Essay on the Origin of Species and Varieties Through Natural Selection
    ```

    So far, `git` has not tracked anything we did.  We need to tell it to record the changes. `git` will only track the files you tell it to track.

3. Set `origin.txt` for `git` tracking then check the repo status:

    ```bash
    $ git add origin.txt
    $ git status

    On branch master

    No commits yet

    Changes to be committed:
      (use "git rm --cached <file>..." to unstage)

            new file:   origin.txt
    ```

    We have yet to actually save a snapshot of our updates.  You should `git commit` your changes at the end of every session, when you have a working script, or when you can succinctly describe the changes you made.

4. Creating a snapshot of the project:

    ```bash
    $ git commit -m "started the book"

    [master (root-commit) a90fea2] started the book
     1 file changed, 1 insertion(+)
     create mode 100644 origin.txt
    ```

    The `-m` option stands for "message".  The message is there to help you know how this version is different than the previous one should you need to recover an older version in the future.  The message should be short but sufficiently descriptive.

5. Show the repo history:

    ```bash
    $ git log

    commit a90fea2df1a59e635fba3c09a0cc0f1dfe78b2d9   #this number is the fingerprint of the commit
    Author: Chris Bird <cbird808@gmail.com>
    Date:   Fri Sep 27 08:24:34 2019 -0500

        started the book
    ```

---
</p>
</details>

<details><summary>Tracking a Change in a Text Document</summary>
<p>


1. Let us change the text in our tracked document

    ```bash
    $ echo "On the Origin of Species, by Means of Natural Selection, or the Preservation of Favoured Races in the Struggle for Life" > origin.txt
    $ git status

    On branch master
    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git checkout -- <file>..." to discard changes in working directory)

            modified:   origin.txt

    no changes added to commit (use "git add" and/or "git commit -a")
    ```

2. Both add and commit need to be executed to update the repo

    ```bash
    $ git add .
    $ git commit -m "Changed the title as suggested by Murray"

    [master 5b762fe] Changed the title as suggested by Murray
     1 file changed, 1 insertion(+), 1 deletion(-)
    ```

3. View the log history again after the commit

```bash
$ git log

commit 5b762fec87bd70db9bdd0d54620b8e4728927a36
Author: Chris Bird <cbird808@gmail.com>
Date:   Fri Sep 27 08:36:22 2019 -0500

Changed the title as suggested by Murray

commit a90fea2df1a59e635fba3c09a0cc0f1dfe78b2d9
Author: Chris Bird <cbird808@gmail.com>
Date:   Fri Sep 27 08:24:34 2019 -0500

started the book
```

    Notice that both commits are logged and each has the "fingerprint" id.

That is the majority of the commands you will use in git: `git add`,  `git commit`

---
</p>
</details>

<details><summary>Git Can Only Track Internal Changes Made to Text Documents</summary>
<p>

It is important to note that `git` is made to track human-readable text files.  A human-readable text file will be readable by your text editor. Files that are binary (`docx`, etc) cannot be tracked by `git` in the same way that text files can.

1. Everybody use your text editor (notepad++ or bbedit) and try to open a MS Word doc

---
</p>
</details>

<details><summary>Showing Changes Since Last Commit</summary>
<p>

  We will use the `sed` command to find the ends of lines (represented by `$` in regex) and replace them with a period (represented by `\.` in regex).  The `-i` argument tells `sed` to change the input file rather than outputting a text stream.

  Then use the `git` argument `diff` to show all changes *since the last commit*.  


```bash
$ sed -i 's/$/\./' origin.txt
$ git diff

# now change it back by removing periods at the ends of lines
$ sed -i 's/\.$//' origin.txt
```

  If you do not see any differences, then you did not change the repo by adding a file or changing the text in `origin.txt`

  Note that the previous version is marked with an `a/` and the newer version is labeled `b`/.  The addition and subtraction of files are marked with `+` and `-`

---
</p>
</details>

<details><summary>Moving and Removing Files in a Repo</summary>
<p>

you need to tell `git` when you remove or move version controlled files

```bash
$ git mv origin.txt origins.txt
$ git rm *.txt

# note that you can skip git add and go straight to commit after this
$ git commit -m "deleted text files"
$ git log
```

  ---
</p>
</details>

<details><summary>Putting it All Together</summary>
<p>

Let us review what we have learned by making a new project in your sandbox and initializing the repo

  ```bash
  $ cd ~/CSB/git/sandbox
  $ rm originspcies
  $ mkdir newproject
  $ cd newproject
  $ git init
  $ git status
  # make changes to repo, then track changes by:
  $ git add --all
  $ git commit -m "my descriptive message"
  ```

---
</p>
</details>

---

### [Mind Expander 2.1](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMVJSRE4zRVpFOElBVTUzMTVVNFZBNkRGVy4u)

---

<details><summary> Troubleshooting `git`</summary>
<p>

Git can get confused if you are not dilligent in your pattern of adding and comitting changes and it will be neccessary to troublshoot conflicts.

1. Amending an Incomplete Commit

  Incomplete commits can occur when files are not removed within git, changes are made but not added, etc..  The solution is to rectify these conflicts.

```bash
# make file
$ touch barnacles.txt

# mistakenly commit changes without adding
$ git commit -m "added barnacles.txt"

On branch master
Untracked files:
		barnacles.txt

nothing added to commit but untracked files present

# fix by adding then committing
$ git add barnacles.txt
$ git commit -m "added barnacles.txt"
```

2. Unstaging Files

  You may have added files to the snapshot staging area by mistake.  To unstage them:
  (do not type this in, it is an example)

```bash
#do not type this into your terminal
$ git reset HEAD filetounstage.txt
```

---
</p>
</details>

<details><summary>Remote Repositories (GitHub)</summary>
<p>

1. Cloning a repository:
  ```bash
  git clone ADD_YOUR_HOMEWORK_REPO_LINK_HERE
  ```

2. Move into your repository, change it, add and commit the changes

3. Push changes from local repository back to central repository on GitHub

    ```bash
    git push
    ```

![alt text](https://github.com/tamucc-comp-bio/fall_2019/blob/master/lectures/Week04_files/git_common_commands.png)

---
</p>
</details>


<details><summary>GitHub Repo Philosophy</summary>
<p>

* You should be conducting your work in your repo, not somewhere else.
  * If you are doing some things for the project on the supercomputer (or a remote server) you should clone your repo there and run the scripts in/from it.

* Do not change the same document in your repo in different locations at the same time
	* for example, don't edit the readme on GitHub and on your laptop without syncing the changes between them

* Every time you pull up to a computer to work on your repo, `pull` the latest version:

	```
	cd path/to/your/repo
	git pull
	```

* As you make progress during a single session, `add` and `commit` your changes.

* Every time you walk away from a computer after working on your repo,`push` your changes


---
</p>
</details>
  
<details><summary>HELP! I CAN'T PUSH MY CHANGES TO GitHub</summary>
<p>

 
Inevitably, you will run into a conflict and your repo will not sync with github, producing errors

&#x1F4A1; TIP! _To solve, "burn it down" and start over. _

* Rename the repo on your computer to ORIGINALNAME_old
* Clone a fresh copy of the repo from GitHub into the parent directory of your old repo
* Copy the newest files and dirs from your old repo into the new repo you just cloned
* add, commit, and push the changes to GitHub


---
</p>
</details>

<details><summary>Directory Organization Philosophy</summary>
<p>

* Every directory should have a descriptive name

* Every directory should contain a descriptive `README.md`
	* this file is automatically displayed when navigating directories on GitHub.
	* yes, part of the intention here is to discourage you from making too many dirs.  Ask yourself, is this new dir I'm thinking of worth writing a `README.md` for?  The answer is usually no.
 	* with the advent of LLM, I like to have ChatGPT take the first pass at making the `README.md`. Can you think of what you might want to show ChatGPT so that it does a good job of making the `README.md`?

* Fewer directories is more (better)

* No "rabbit holes".  
	* A "rabbit hole" is a dir in a dir in a dir in a dir in a...
	* Try to minimize nested directories

* Consult [How to Organize Biological Data](https://github.com/tamucc-comp-bio/how_to/blob/main/howto_organize_data.md)

  ---
  </p>
  </details>

<details><summary>Large files (>100MB) and `.gitignore`</summary>
<p>

If you are working with large files, GitHub will not accept them and it will cause problems with git. You should add large files to the `.gitignore` file.

The `.gitignore` file in the top level of your repo that is a list of files and dirs (wildcards work too) that should not be tracked by `git`. The file is invisible (all files and dirs that start with a `.` are invisible).  To list invisible files, `ls -a`.

This is an example `.gitignore` that includes files created when working with R and RStudio that should not be tracked:

    ```
    # History files
    .Rhistory
    .Rapp.history

    # Session Data files
    .RData
    .RDataTmp

    # User-specific files
    .Ruserdata

    # Example code in package build process
    *-Ex.R

    # Output files from R CMD build
    /*.tar.gz

    # Output files from R CMD check
    /*.Rcheck/

    # RStudio files
    .Rproj.user/

    # produced vignettes
    vignettes/*.html
    vignettes/*.pdf

    # OAuth2 token, see https://github.com/hadley/httr/releases/tag/v0.3
    .httr-oauth

    # knitr and R markdown default cache directories
    *_cache/
    /cache/

    # Temporary files created by R markdown
    *.utf8.md
    *.knit.md

    # R Environment Variables
    .Renviron

    # pkgdown site
    docs/

    # translation temp files
    po/*~

    # RStudio Connect folder
    rsconnect/
    ```

---
</p>
</details>


## EXAM 1 Due Next Week Before Class 

[See Course Schedule](../README.md)
















