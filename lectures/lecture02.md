# Week02 UNIX II

> [!IMPORTANT]
> [Assignment 1](../assignments/assignment_1.md) is due at the beginning of this lecture

> [!NOTE]
> The [Lecture Stream 2025](https://tamucc.zoom.us/rec/play/pfgVVA9Bsk-di4MUxhHCxwL9kKJFOqZNeqw9ZgNV59MMlaxYxJaARqcDpYSbh0rZRK5iv1RJB8dUe29l.0g9hG3R7k_b1Hqyz) will be updated following lecture.
> Passcode: !N6*?2HL

> [!NOTE]
> I converted the [**Lecture_02 Slides**](Week02_files/Lecture02_WelcomeToTheMatrix.pdf)  to a more screen-splitting friendly format here in GitHub.

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

## Text Book Versus Online Materials

<details><summary>click to expand</summary>
<p>

While the CSB text book is not required, this info provides context for those that choose to use it.

The material below closely follows the book but there is some additional information that is not provided in the book (and vice versa). If you choose to follow the lecture slides, the `code blocks` are represented by green text on a black background, mimicking the terminal.

* Page 35 **Use _BodyMass.csv_ (slides) rather than _BodyM.csv_ (book)**

* Page 46, the script on the bottom half of the page is poor form. Making a bunch of tmp files is a bad idea.  Do this instead:

```
#!/bin/bash

# to run do this:
# ./ExtractBodyM.sh [infile] [outfile]

# isolate columns 2-6 of csv (first argument) using cut
# translate the ; to “ “ using tr
# remove the header row using tail
# sort by sixth column, descending order
# save to file (second argument)

# isolate columns 2-6 of csv (first argument) using cut
cut -d ";" -f 2-6 $1 | \
 # translate the ; to “ “ using tr
	tr ";" " " | \
 # remove the header row using tail
	tail -n+2 | \
 # sort by sixth column, descending order
 # save to file (second argument)
	sort -nrk6 > $2
```

</p>
</details>


---

## [Week 02 Quiz](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMjIySEJCNFlSMVJRSUo0SU5HSFNKMVRHWC4u)

After you log into the class and get your computer set up, please complete the quiz. If you are logged into the university webmail, you will not be prompted for a password.

---


## Review [`assignment_01`](../assignments/assignment_1.md) Due Today 

<details><summary>Advanced `bash` Commands</summary>
<p>

Work through the following tutorial. Note the instructions to clone the CSB repo in the Computer Preparation instructions above


---

### Move the the `CSB/unix/sandbox` directory

```bash
# let’s start by moving to our sandbox in the unix dir of the CSB repo
# you must have cloned the CSB repo to your home dir for this path to work
$ cd ~/CSB/unix/sandbox
$ pwd
```

After running `cd ~/CSB/unix/sandbox`, your present working directory (`pwd`) is `sandbox`.  If the `cd ~/CSB/unix/sandbox` failed, then you should consult the [Computer Preparation Section](#computer-preparation) above

```
CSB/unix
├── data
│   ├── Saavedra2013
│   └── miRNA
├── installation
├── **sandbox**  #YOU SHOULD BE HERE!
└── solutions
```

---

### Redirection of output ([stdout](https://en.wikipedia.org/wiki/Standard_streams#Standard_output_(stdout))) to file `[command] > filename`, Append [stdout](https://en.wikipedia.org/wiki/Standard_streams#Standard_output_(stdout)) to file `[command] >> filename`, Redirect contents of file to [stdin](https://en.wikipedia.org/wiki/Standard_streams#Standard_input_(stdin)) `[command] < filename` 

```
# print text to screen, then print to file, then print file to screen
$ echo "My first line" 
My first line

$ echo "My first line" > test.txt
$ cat test.txt
My first line

# append file with additional text, then print file to screen
$ echo "My second line" >> test.txt
$ cat test.txt
My first line
My second line
```

&#x1F4A1; TIP! _use `Tab` key to autocomplete names, prevent spelling mistakes_

---


### Problem Solving Scenario

A machine provides you with thousands of data files. There’s so many, it is freezing your Win/Mac GUI file browser. How can you determine the number of files?

We will use the dir `unix/data/Saavedra2013` as an example of a directory with many files

```
CSB/unix
├── data
│   ├── Saavedra2013
│   └── miRNA
├── installation
├── **sandbox**  #YOU ARE HERE!
└── solutions
```

&#x1F4A1; TIP! _To specify `unix/data/Saavedra2013` from `unix/sandbox` you can use the relative path `../data/Saavedra2013`_

```bash
# save file names to file in pwd
$ ls ../data/Saavedra2013 > filelist.txt

# look at the file
$ cat filelist.txt

# count lines in the file
$ wc -l filelist.txt

# remove the file
$ rm filelist.txt
```

---

### Piping Text Streams From One Command to the Next with `|`

![Common Operating Systems](../lectures/Week01_files/pipeline.png)

![Common Operating Systems](../lectures/Week01_files/pipeline2.png)

A pipe `|` passes the [stdout](https://en.wikipedia.org/wiki/Standard_streams#Standard_output_(stdout)) from one command to the [stdin](https://en.wikipedia.org/wiki/Standard_streams#Standard_input_(stdin)) of another

&#x2753; QUESTION _How many files are there in `CSB/unix/data/Saavedra2013`?_

```
CSB/unix
├── data
│   ├── Saavedra2013
│   └── miRNA
├── installation
├── **sandbox**  #YOU ARE HERE!
└── solutions
```

```bash
# list file names
$ ls ../data/Saavedra2013

# list file names and pipe into wc to return the number of files
$ ls ../data/Saavedra2013 | wc –l
59

```

---

### [TSV](https://en.wikipedia.org/wiki/Tab-separated_values) & [CSV](https://en.wikipedia.org/wiki/Comma-separated_values) Data Files

In the tidy table below, columns are _*delimited*_ by tabs.  The first column has no column header but is the sample ID.  Ozone, Solar.R, Wind, Temp, Month, and Day are all pieces of data (dimensions) describing each of the 10 samples.

![Common Operating Systems](../lectures/Week01_files/tsv.png)

* Tab Separated Values (TSV)

  * Tabs denote columns

* Comma Separated Values (CSV)

  * Commas denote columns
  
* [Tidy data](https://en.wikipedia.org/wiki/Tidy_data)

  * Each [row](https://en.wikipedia.org/wiki/Row_(database)) is one [unit of observation](https://en.wikipedia.org/wiki/Unit_of_observation)
  
  * Each [column](https://en.wikipedia.org/wiki/Column_(database)) is one dimension or aspect of the units of observation
  
* File extensions are not always accurate, so it is important to view a file to be sure of the delimiter.


Tidy Table:
| Column 1 Header | Column 2 Header | Column 3 Header |
| --------------- | --------------- | --------------- |
| Row 1 Column 1 | Row 1 Column 2 | Row 1 Column 3 |
| Row 2 Column 1 | Row 2 Column 2 | Row 2 Column 3 |
| Row 3 Column 1 | Row 3 Column 2 | Row 3 Column 3 |
| Row 4 Column 1 | Row 4 Column 2 | Row 4 Column 3 |

TSV
```
Column 1 Header	Column 2 Header	Column 3 Header
Row 1 Column 1	Row 1 Column 2	Row 1 Column 3
Row 2 Column 1	Row 2 Column 2	Row 2 Column 3
Row 3 Column 1	Row 3 Column 2	Row 3 Column 3
Row 4 Column 1	Row 4 Column 2	Row 4 Column 3
```

&#x26A0; CAUTION! _Do not type in these code blocks.  They are here to show you TSV and CSV formatting_

TSV File with tabs denoted by `\t`.  Note your text files will not contain `\t`.  I did this show where tabs were, versus spaces. This is also the first use of a regular expression in this course.  The `\` is the escape character, which changes the meaning of the character that follows.  `\t` is the regular expression for a tab. Regular expressions are recognized by almost all commands across all computer languages that use a pattern (`\t`) to find matching text (tab character).

```
Column 1 Header\tColumn 2 Header\tColumn 3 Header
Row 1 Column 1\tRow 1 Column 2\tRow 1 Column 3
Row 2 Column 1\tRow 2 Column 2\tRow 2 Column 3
Row 3 Column 1\tRow 3 Column 2\tRow 3 Column 3
Row 4 Column 1\tRow 4 Column 2\tRow 4 Column 3
```

CSV
```
Column 1 Header, Column 2 Header, Column 3 Header
Row 1 Column 1, Row 1 Column 2, Row 1 Column 3
Row 2 Column 1, Row 2 Column 2, Row 2 Column 3
Row 3 Column 1, Row 3 Column 2, Row 3 Column 3
Row 4 Column 1, Row 4 Column 2, Row 4 Column 3
```

---


### Convert Among Formats Using `tr "<old delimiter>" "<new delimiter>"`

```bash
# view contents of csv
$ less -S ../data/Pacifici2013_data.csv 

# replace semicolons with commas using tr [find] [replace]
$ cat ../data/Pacifici2013_data.csv | tr “;” “,” | less –S

# view as tsv
# \t is the nearly universal symbol for tab
$ cat ../data/Pacifici2013_data.csv | tr ";" "\t" | less -S

```

&#x1F4A1; _`tr` is an abbreviation for translate_

---


### Using `cut` to retrieve/isolate/select columns and `head` to retrieve rows

```bash
# change directory
$ cd ~/CSB/unix/data

# display first line of file (i.e., header of CSV file)
$ head -n 1 Pacifici2013_data.csv

# display first column of file
$ cut -d ";" –f 1 Pacifici2013_data.csv

# display second through fourth columns
$ cut -d ";" -f 2-4 Pacifici2013_data.csv

# display first “cell” of data
$ head -n 1 Pacifici2013_data.csv | cut -d ";" -f 1

```

&#x1F4A1; _`cut` assumes tab delimited files.  If a different delimiter is used in the file, the `-d` option is used to specify the delimiter.  It is very easy to mistake spaces for tabs, and that will make `cut` do odd things with your data if you do not set `-d " "`_

---


### Connecting `cut` `head` `tail` `sort` `uniq`

```bash
# select 2nd column, display first 5 elements
$ cut -d ";" -f 2 Pacifici2013_data.csv | head -n 5

# select 2nd and 8th columns, display first 3 elements
$ cut -d ";" -f 2,8 Pacifici2013_data.csv | head -n 3

# select 2nd column without header, show 5 first elements
$ cut -d ";" -f 2 Pacifici2013_data.csv | tail -n +2 | head -n 5

# identify the orders in csv
# select 2nd column without header, unique sorted elements
$ cut -d ";" -f 2 Pacifici2013_data.csv | tail -n +2 | sort | uniq

# count how many records per order in csv
$ cut -d ";" -f 2 Pacifici2013_data.csv | tail -n +2 | sort | uniq -c

# output the order with the most records, including the number of records in csv
$ cut -d";" -f2 ../data/Pacifici2013_data.csv |  tail -n +2 | sort | uniq -c | tr -s " " "\t" | cut -f2-3 | sort -n | tail -n1

```

&#x1F4A1; _`uniq` is a command that that removes consecutive duplicate lines (rows). For this reason, the input to `uniq` is almost always sorted beforehand.  Use `man uniq` to see the description of the `-c` option.  I use `uniq -c` all the time._

&#x1F4A1; _`sort -t";"` specifies the delimiter character, also known as a field separator.  Try `man sort` and search `/field` to see the manual entry for this._

&#x1F4A1; _`tr -s` can be used to easily convert files or text streams that have multiple spaces in between columns (such as the output of `uniq -c` into a tab separated format.  The `-s` means squish consecutive charcters to one character_

---

### Advanced Pipelining

When constructing long pipelines like the last one in the code block above, you should build it step by step, testing the output as you go.  This strategy reduces the possibility of making a mistake.

I like to use `less -S` or `head` to capture and view the output when it takes up many lines.  The `q` key closes the `less` viewer.

```
# here is an example of how to build the really long pipe above, from scratch
$ cut -d";" -f2 ../data/Pacifici2013_data.csv | less -S
$ cut -d";" -f2 ../data/Pacifici2013_data.csv | tail -n +2 | head
$ cut -d";" -f2 ../data/Pacifici2013_data.csv | tail -n +2 | sort | head
$ cut -d";" -f2 ../data/Pacifici2013_data.csv | tail -n +2 | sort | uniq -c | less -S
$ cut -d";" -f2 ../data/Pacifici2013_data.csv | tail -n +2 | sort | uniq -c | tr -s " " "\t" | head
$ cut -d";" -f2 ../data/Pacifici2013_data.csv | tail -n +2 | sort | uniq -c | tr -s " " "\t" | cut -f2-3 | head
$ cut -d";" -f2 ../data/Pacifici2013_data.csv | tail -n +2 | sort | uniq -c | tr -s " " "\t" | cut -f2-3 | sort -n | less -S
$ cut -d";" -f2 ../data/Pacifici2013_data.csv | tail -n +2 | sort | uniq -c | tr -s " " "\t" | cut -f2-3 | sort -n | tail -n1
```

</p>
</details>



[Software Carpentry, The Unix Shell: Pipes & Filters](https://swcarpentry.github.io/shell-novice/04-pipefilter.html) 

[Software Carpentry, The Unix Shell: Finding Things](https://swcarpentry.github.io/shell-novice/07-find.html)

<details><summary>Mind Expander & Exercise Review</summary>
<p>

[Mind Expander 01.01](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUM1FFUUZLT01LR0ZGODU2WVNSV1c0NEpWMi4u)

[Mind Expander 01.02](https://forms.office.com/r/M9XnBAtiUw)
 
[Mind Expander 01.03](https://forms.office.com/r/sSBR8Sjm9x)

[Exercise 1.10.1 Next Generation Sequencing Data](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMTVENFg0UjhFTzc3Wkc0NExRTjdLSjdGNi4u)

</p>
</details>

<details><summary>Reading</summary>
<p>

[Good enough practices (Wilson etal 2017)](../literature/Wilson_etal_2017_good_enough_practices_in_scientific_computing.pdf)

<details><summary>What is the main point of the Wilson etal 2017 manuscript?</summary>
<p>

![](Week02_files/assignment1_1.png)

**Core takeaway:** Wilson et al. (2017) argues that many scientists lack formal computing training, and offers practical, accessible guidelines—covering data management, simple coding, version control, documentation, and project organization—to reduce errors, improve efficiency, and make research reproducible.

**Key points:**

* Scientists commonly use computers without proper training, leading to inefficiencies and data loss.
* The paper provides beginner-friendly tools and minimum best practices anyone can adopt.
* Emphasis on organizing projects for human and machine readability.
* Focus on reproducibility, reliability, and collaboration through clear code, data standards, and documentation.
* Goal is optimization of everyday research workflows, not advanced techniques.

---

 </p>
</details>

<details><summary>What do you like about the Wilson etal 2017 manuscript?</summary>
<p>

![](Week02_files/assignment1_2.png)

**Overall sentiment**

* Practical, to-the-point, and beginner-friendly without being overwhelming.

**Top themes**

* **Accessibility:** Acknowledges most scientists aren’t formally trained; “easier is better” and welcoming to newcomers.
* **Actionability:** Concrete, achievable steps for data management, file/directory setup, versioning, and documentation.
* **Reproducibility & collaboration:** Helps your future self and teammates find, understand, and reuse work.
* **Clarity & organization:** Clear breakdowns of concepts and “what to do,” making it simple to follow.

**Standout features**

* Structured format (boxes/sections) and a summary table that functions like a cheat sheet.
* Realistic examples that show what good practice looks like in practice.
* Logical organization of reading sections that guides the reader smoothly.

---

 </p>
</details>

<details><summary>Do you disagree with Wilson etal 2017 on any of their points?</summary>
<p>

![](Week02_files/assignment1_3.png)

**Overall verdict**

* **No disagreements.** Respondents broadly agree with Wilson et al. (2017) and found the guidance accurate and useful.

**Why they agree**

* The points match real-world pain: many have made or fixed the exact mistakes the paper addresses.
* The low barrier, “good-enough” practices are practical and helpful—especially for beginners.

**Nuanced caveat raised by a few**

* While the advice is great for getting started, **“good enough” may fall short** for advanced users or high-stakes/complex projects, where stricter practices may be needed.

---

 </p>
</details>

<details><summary>What was confusing or do you have any questions about Wilson etal 2017?</summary>
<p>

![](Week02_files/assignment1_4.png)

## What felt confusing / open questions

* **Collaboration tools:** “Is Word/Google Docs good for manuscripts?” “For theses/papers, Google Docs or plain text in version control?”
* **Jargon & workflow:** Directories and “tracking changes” were hard to follow.
* **Data size:** How advice scales to very small vs. very large datasets.
* **Rigor thresholds:** “When do we move from ‘good enough’ to fully tidy/strict practices?”
* **Provenance:** Want a concrete example of how to record data-processing steps.
* Some respondents had **no questions**.

## Answers

* **Word/Google Docs vs. plain text + Git**

  * *Good:* Docs/Word are great for early drafting, comments, and broad coauthoring.
  * *Better for maniacal control, reproducibility:* Plain text (Markdown/LaTeX) in Git. Hybrid works well: draft in Google Docs → freeze a submission version in Markdown/LaTeX under Git (or use Overleaf with Git).  I use word.  Some prefer LaTeX.
  * *Rule of thumb:* I generally think word is "good enough" for manuscripts!. md is all that github understands, so it's best for documenting
* **Directories & “track changes” (cheat sheet)**

  * **Directories:** `project/` → `data_raw/`, `data_clean/`, `scripts/`, `results/`, `docs/`, `README.md`.
  * **Tracking changes:** Prefer Git over Word “Track Changes.” Use branches/PRs for review; keep commit messages meaningful.
* **Dataset size**

  * **Small (MBs):** Keep data in the repo.
  * **Medium/Large (GB+):** Don’t store raw in Git. Store externally (OSF/Zenodo/S3/Dataverse); keep *checksums + metadata* and *download scripts* in the repo. Consider DVC or git-annex.
* **When to go beyond “good enough” to tidy/strict**

  * This is up to you.  I still think I'm in the good-enough phase!
* **How to record processing steps (minimal template)**

  * Keep one of these in `docs/` or project root:

    * **Processing log (Markdown):**

      ```
      # Data Processing Log
      ## 2025-09-12
      - Input: data_raw/fish_survey.csv (sha256: abc123…)
      - Script: scripts/01_clean.R (v1.2, commit 3f7c2d)
      - Params: min_count=5, drop_na=true
      - Output: data_clean/fish_survey_clean.csv (rows: 12,345)
      - Notes: Removed 23 rows with missing site_id.
      ```
    * **Scripted report:** Use an R Markdown / Jupyter notebook that reads raw → writes clean, with parameters and session info.
    * **Makefile / workflow:** Encode steps as targets (e.g., `make data_clean/fish_survey_clean.csv`), which documents order and dependencies automatically.

---

 </p>
</details>

</p>
</details>

---


## Additional Important `bash` Commands (rest of CSB Section 1.6)

<details><summary>Additional Important Commands</summary>
<p>

### Substituting Characters Using 	`tr`
### Predefined Characters `[:upper:]`

`tr` can be used to replace one or more characters

```bash
# change all a to b
$ echo "aaaabbb" | tr "a" "b"
bbbbbbb

# change 1, 2, 3, 4, and 5 to zero
$ echo "123456789" | tr 1-5 0
000006789

# change a, c, t, g to upper case
$ echo "ACtGGcAaTT" | tr actg ACTG
ACTGGCAATT 

# change lower case letters to upper case
$ echo "ACtGGcAaTT" | tr [:lower:] [:upper:]
ACTGGCAATT

# change a, b, or c to 1, 2 ,or 3 repectively
$ echo "aabbccddee" | tr a-c 1-3
112233ddee

# delete all occurrences of a
$ echo "aaaaabbbb" | tr -d a
bbbb

# remove consecutive duplicate occurrences of a
$ echo "aaaaabbbb" | tr -s a
abbbb

```

&#x1F4A1; TIP! _`tr` does not accept a file as an argument, always use pipe `|` or redirect a file into `tr` (`tr " " "," < file.txt`)_

---

### Use `;` to separate multiple independent commands on 1 line

`;` is equivalent to a period in an english sentence.

```bash
# move to sandbox and list files
cd ~/CSB/unix/sandbox; ls
```

---


### Making a New File From An Existing File

Make a new file `BodyMass.csv` in sandbox dir based on columns 2-6 in `Pacifici2013_data.csv`, remove header, sort lines according to body mass (large to small), change ; to spaces

```bash
# 1. View header row to refresh your memory
$ head -n 1 ../data/Pacifici2013_data.csv 
$ head -n 1 ../data/Pacifici2013_data.csv | tr ";" "\n"

# 2. Start building pipe, use head to view
$ cut -d ";" -f2-6 ../data/Pacifici2013_data.csv | head

# 3. Add to pipe by changing ; to tabs, use head to view
$ cut -d ";" -f2-6 ../data/Pacifici2013_data.csv | tr ";" "\t" | head

# 4. Add to pipe by removing first line, figure out sort options, use head to view
$ cut -d ";" -f2-6 ../data/Pacifici2013_data.csv | tr ";" " " | tail -n+2 | sort -nrk6 | head

# 5. Instead of piping to head, redirect output to file named BodyMass.csv
$ cut -d ";" -f2-6 ../data/Pacifici2013_data.csv | tr ";" " " | tail -n+2 | sort -nrk6 > BodyMass.csv
```

&#x1F4A1; _in step 1, we use `tr` to replace semicolons `;` with "[line feeds](https://en.wikipedia.org/wiki/Newline)" `\n` to view one column header per line._

&#x1F4A1; _`\` is the "[escape character](https://en.wikipedia.org/wiki/Escape_character)".  The character following the `\` has an alternate meaning._

&#x1F4A1; _`t` is the letter "t", `\t` is a [metacharacter](https://en.wikipedia.org/wiki/Metacharacter) that symbolizes a tab_

&#x1F4A1; _`n` is the letter "n", `\n` is a metacharacter that symbolizes the end of a line (aka line feed)_

---

### [Glob Patterns](https://en.wikipedia.org/wiki/Glob_(programming)) with [Wildcard Characters](https://en.wikipedia.org/wiki/Wildcard_character)

[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are used to specify groups of directories and files based on common naming.

[Wildcards](https://en.wikipedia.org/wiki/Wildcard_character) are special characters that represent multiple characters simultaneously

`*` Matches zero or more characters, except "leading dot"

`?` Matches any single character, except "leading dot"

`[]` match any one of the characters in the brackets


```bash
# goto miRNA dir inside data dir
$ cd ~/CSB/unix/data/miRNA

# list all files that end with fasta 
$ ls *fasta

# count the numbers of lines in all the fasta files
$ wc -l *fasta

# print the first two lines of each file whose name starts with pp
$ head -n 2 pp*

# determine the type of every file that has an extension with exactly three letters
$ file *.???

# list all files begining with either g, h, or m and ending with fasta
ls [ghm]*fasta

```

&#x1F4A1; TIP! _in unix and linux, hidden files are marked by a "leading dot" `.`.  Try `ls -a` to see all files, including those that are hidden.  Wildcards will not return hidden files without being preceded by a `.`_

---

### Selecting lines with matching pattern using `grep [options] [pattern] <filename>` 

* Every line that matches the pattern is returned

  * there are options that allow more specific output, such as a word rather than a line

* Many options to increase functionality. I use `grep` all the time.

* [Regular Expressions](https://en.wikipedia.org/wiki/Regular_expression), aka regex, are used for pattern matching in text files

  * A language of characters, metacharacters, wildcards
  
  * 2 primary syntaxes or standards: [POSIX](https://en.wikipedia.org/wiki/POSIX) (default in `grep`), [Perl](https://en.wikipedia.org/wiki/Perl) (use `-P` option in `grep`)
  
    * when searching for help on regex, it is important to know which standard the pattern is using because POSIX is not the same a Perl


```bash
# goto unix chapter sandbox
$ cd ~/CSB/unix/sandbox

# how many wombats (fam Vombatidae)?
$ grep "Vombatidae" BodyMass.csv
$ grep -c "Vombatidae" BodyMass.csv

# which cattle are in file?
$ grep "Bos" BodyMass.csv

# Only match whole words
$ grep -w "Bos" BodyMass.csv

# Only match whole words and only return the words that match, rather than the lines
$ grep -wo "Bos" BodyMass.csv

# Make search case insensitive
$ grep –i "Bos" BodyMass.csv

# which mammals have body weight most similar to the gorilla?
# option –B lines before match, option –A lines after match
$ grep -B 2 -A 2 "Gorilla gorilla" BodyMass.csv

# show line number of gorilla
$ grep -n "Gorilla gorilla" BodyMass.csv

# -v means match anything except pattern
$ grep Gorilla BodyMass.csv | grep -v gorilla

# return all lines with Gorilla or Pan, note use of escape char \
$ grep -w "Gorilla\|Pan" BodyMass.csv

# return all lines with Gorilla for all files in data dir and its subdirs. -r recursive, searches subdirs
$ grep -r "Gorilla" ../data

```

&#x1F4A1; TIP! _the `grep -c` option is very handy for counting and can negate the need for `wc -l`_

---

### Searching for files with `find [dir] [options] [pattern]` 


```bash
# current directory is the unix sandbox
$ find ../data

# how many files are in data?
$ find ../data | wc -l

# find file named n30.txt in data
$ find ../data -name "n30.txt"

# use wildcards to find all files in data that contain about
$ find ../data -iname "*about*"

# count all files that end in .txt in data, then do same but do not include subdirs
$ find ../data -name "*.txt" | wc –l
$ find ../data -maxdepth 1 -name "*.txt" | wc –l

# count files in data that do not include about
$ find ../data -not -name "*about*" | wc -l

# find directories with data in path or name
$ find ../data -type d
```

---

### Change Permissions with `chmod [options] ### <filename>`

* Three types of permissions

  * Read, Write, Execute
  
  * Program will not run if `x` is not set

* Three types of users

  * User, Group, Global

* View with `ls -l`

![](Week01_files/ls-ltrh_3.PNG)

* Setting permissions using “octal” numeric system

  * read = 4
  
  * write = 2
  
  * execute =1
  
  * Simply add numbers together for different combos of permissions

    * if the user has all permissions, 4 + 2 + 1 = 7
  
    * if the group has read permissions, 4
  
    * if the global has no permissions, 0

      * the full set of permissions are then: 740

```bash
# create a file in the unix sandbox
$ touch permissions.txt
$ ls –l

# change permissions so that user can r,w,x; group can r,x; and global can r
$ chmod 754 permissions.txt
$ ls –l

# give everybody full permissions 
$ chmod 777 permissions.txt
$ ls –l

# give yourself full permissions, but only let others read your files 
$ chmod 744 permissions.txt
$ ls –l
```

---

### Super User Do to Execute Command as Administrator: `sudo <command> <options> <arguments>`

* Use `sudo` when computer tells you no.

* You will need sudo for installing software

```bash
$ apt update
Reading package lists... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)

$ sudo apt update

```

&#x26A0; CAUTION! _Make sure you are certain that you want to execute the command before using `sudo`, especially in combination with `rm`, `cp`, `mv`._


---

### Change Owners With `chown`

The user who creates a file or directory owns that file or directory, but sometimes you will want to transfer ownership (usually to yourself).

```bash
# create a directory with a subdirectory
$ mkdir -p test_dir/test_subdir
$ ls -l 
$ ls -l test_dir

# list valid users
$ cut –d: -f1 /etc/passwd

# change owner of dir, -R includes subdirs
$ chown -R ValidUserName test_dir/
$ sudo chown -R ValidUserName test_dir/
$ ls –l
$ ls –l test_dir

# change owner back to you
$ sudo chown -R $USER test_dir/
```

---


</p>
</details>

[Mind Expander 01.04](https://forms.office.com/r/uvi6cGMSMJ): Take 10 minutes to complete

---


## Concise Review of Material Covered Up Through Now

<details><summary>Commands have options and accept arguments to modify functionality </summary>
<p>

#### [command] [options] [arguments]

* `ls -ltrh CSB`

#### a command is a simple app 

* `ls`

#### an option is a command setting, like a check box

* `-a` single letter options are immediately preceded by `-`,  `- a` will not work

  * shortcut for many single letter options: `ls -l -t -r -h` is the same as `ls -ltrh`

* `--all` there are typically word versions of each option and they are preceded by `--`

  * there are no shortcuts for word options, i.e. `ls -ltrh --all` or ` ls --all -ltrh` or `ls -ltrha`

#### an argument is a value or string that is provided to the command

* ex. a path, dir name, or file name
  
  * `ls data` will return the file and contents of directory named *data* if it exists in present dir

</p>
</details>

---

<details><summary>Commands for navigating and manipulating dirs & files </summary>
<p>

#### `cd`    change directories
#### `pwd`   where am I?
#### `ls`    show contents of `pwd`
#### `cp`    copy files and directories from one location to another, could also rename copied file
#### `mv`    move files and directories from one location to another, rename file or directories
#### `rm`    delete file or dir, be careful, there is no undo
#### `mkdir` make new directory, will not overwrite existing dir
#### `less`  view a file without opening all of it, good for large files
#### `nano`  word processor, edit text files
#### `chmod` change file and dir permissions

</p>
</details>

---

<details><summary>Use `man`, `-h`, `--help`, or web search to get help </summary>
<p>

#### `man` [command]    show manual for command
  
#### [command]` -h`     if man does not work, this could show manual for command
  
#### [command]` --help` another way to display manual in some cases
  
#### [command]          another way to display manual in some cases
  
#### use web browser to search on *bash command* 
  

</p>
</details>

---

<details><summary>The address of a file or dir is a *path*: `/home/username`</summary>
<p>

#### Absolute paths specify the same address regardless of the present working dir

  * `/`     root dir, top dir in directory tree
  
  * `~`     home dir

#### Relative paths specify different addresses depending upon the present working dir

  * `-`     last directory your were in before the `pwd`
  
  * `../`   parent directory, one directory up the tree from `pwd`
  
  * `../../` 2 directories up the tree from `pwd`
  
  * `./`    present working directory

</p>
</details>

---

<details><summary>Many bash commands are important for manipulating biological data</summary>
<p>

#### `echo`  prints text or convertes text into a text stream

#### `head`  returns only first few lines of a file, or remove last lines (rows)

#### `tail`  returns only last few lines of a file, or remove first lines (rows)

#### `cut`   returns specified columns

#### `cat`   combines files together by line (row)

#### `uniq`  removes duplicates

#### `sort`  changes the order of rows by column

#### `grep`  returns lines (rows) that match a pattern

#### `tr`    replaces one character with another, usually column delimiters

#### `wc`    count words, characters, lines, etc

</p>
</details>

---

<details><summary>Unix commands are designed to pipe `|` and redirect `>` text streams to construct pipelines that link commands and create new files</summary>
<p>

#### [command] [options] [arguments] | [command] [options] [arguments] > [output file]

#### `|`     takes standard output (*stdout*) from one command and pipes it to another command as *stdin*

#### `>`     redirects *stdout* into a file of your naming, will overwrite existing file

#### `>>`    redirects *stdout* into a file of your naming, will append existing file

</p>
</details>

---

<details><summary>Glob patterns employ wildcards and common naming to specify several files with one word or path</summary>
<p>

#### `*` can be any character

* `ls *.txt` will list all files ending in `.txt` 

#### `[AB]` means either character `A` or character `B` 

* `ls [bm]oat.txt` will list files named either `boat.txt` or `moat.txt`

</p>
</details>

---

<details><summary>The escape character `\ ` changes the meaning of the character that follows, including end of lines</summary>
<p>

#### at the end of a line, `\ ` means do not end line and continue on next line

#### `\t`   is a tab, but not all commands recognize this

#### `\n`   is a line feed (*LF*), the unix end of line character (usually invisible)

#### `\r`   is a carriage return (*CR*), in windows every line concludes with CRLF, and causes compatibility issues with unix/linux/mac 

#### there are MANY more uses of `\ `, such as specifying a file with a space in the name: `my\ files`

</p>
</details>

---

## [File Path Scavenger Hunt!](https://forms.cloud.microsoft/r/Zq7avbJpqu)

* [Non-TAMUCC Students: File Path Scavenger Hunt!](https://forms.cloud.microsoft/r/036fdetK5g)

Take 10 minutes to complete the scavenger hunt.

---

## Computer Programming with `bash` (CSB 1.7-1.9)

<details><summary>Scripting</summary>
<p>

See the lecture 2 slides and chapter 1 for this material

### NOTE: While the examples I use here show you how to edit a script in `nano` the best way to construct/edit a script is to 
 to:

* use a GUI text editor (NotePad++ or bbEdit) to edit the code, 
* troubleshoot lines by copying and pasting into the terminal,
* then add tested code to your script in Ubuntu by copying from your GUI text editor to `nano`

### What are [scripts](https://en.wikipedia.org/wiki/Scripting_language)?

A script is a file with a list of commands which are executed sequentially from the first line to the last.

In lecture 0, we installed [xming](https://sourceforge.net/projects/xming/) on windows computers.  You need to have [xming](https://sourceforge.net/projects/xming/) turned on for the next commands to work in Ubuntu on windows computers.  

```bash
# create and open ExtractBodyM.sh in CLI text editor
$ nano ExtractBodyM.sh

# ctrl + x to save and exit, then "y" to use the existing name, then "enter key"

# If you have Ubuntu, make sure that you have xming turned on
# open ExtractBodyM.sh in GUI text editor.  If this does not work, then use the nano command above
$ gedit ExtractBodyM.sh

# If you have Mac
# open ExtractBodyM.sh in GUI text editor.  If this does not work, then use the nano command above
$ open –a bbedit ExtractBodyM.sh
# or
$ open ExtractBodyM.sh
```

Either type in or copy and paste the pipeline we made previously to make `BodyMass.csv` into `ExtractBodyM.sh`:

```bash
cut -d ";" -f 2-6 ../data/Pacifici2013_data.csv | tr ";" " " | tail -n+2 | sort -nrk6 > BodyMass.csv
```

The script should look like this:

![](Week02_files/nano_screen_1.png)

Close the script `ctrl + x` then run it as follows:

```bash
# run ExtractBodyM.sh script
$ bash ExtractBodyM.sh

# view directory
$ ls –ltrh

# Open script again
$ nano ExtractBodyM.sh
```

---

### Documenting your script appropriately

* It is important to write comments in English to describe what the script is doing

  * You’ll forget what the code does
  
  * Makes it easier for others to figure out what is happening in the script
  
  * Easier to identify errors

Add the following comments to the script before the code using nano

```bash
# isolate columns 2-6 of csv using cut
# translate the ; to “ “ using tr
# remove the header row using tail
# sort by sixth column, descending order
# save to file
```

Your screen in `nano` should look like this:

![](Week02_files/nano_screen_2.png)

To save changes made in nano without closing: `ctrl + o`, then `enter`.  Do not change the name of the script

---

### Organizing the script

It can be a good idea to try to limit a script to 1 command per line to improve its readability.

Now, let us organize the script so that each pipe in the pipeline occurs on one line by adding the escape character `\ ` after each pipe `|` and hitting enter. The `\ ` tells `bash` to ignore the end of the line.  When complete, your screen should look like this:

![](Week02_files/nano_screen_3.png)

Now that each command is on one line, we can reorganize the comments to occur immediately before the correct line, as follows:

![](Week02_files/nano_screen_4.png)

&#x1F4A1; TIP! _`ctrl + k` will delete a line in `nano`_


---

### Indenting consistently

Indentation is a key to writing readable code.  Because we are continuing the same pipe, it is a good idea to indent the subsequent lines in the pipe, as follows:

![](Week02_files/nano_screen_5.png)

---

### Accepting arguments from the command line

It is easy to write a script that accepts arguments when run from the command line.  Recall that an argument is a word or number that is passed to a command.  The first argument after a script or command is saved into a variable called `$1` automatically. A second argument is saved to `$2`, so on and so forth.  

Let us make our script accept a path to the input file and a path to the output file rather than [hard coding](https://en.wikipedia.org/wiki/Hard_coding) the input and output files. We do this by replacing the input `../data/Pacifici2013_data.csv` and output file paths `BodyMass.csv` with `$1` and `$2`, respectively. Do not forget to add to the documentation, and describe how the script should be run:

![](Week02_files/nano_screen_6.png)

Do not forget to save your work with `ctrl + o`.

&#x1F4A1; TIP! _all variables are preceded by a `$`.  Avoid creating variables named 1, 2, etc because they could interfere with arguments read in from the command line._

---

### Running the script

Close `nano` with `ctrl + x`, then let us run the script.

```bash
# run ExtractBodyM.sh script
$ bash ExtractBodyM.sh ../data/Pacifici2013_data.csv BodyM.csv
```

---

### Making script "executable"

You can always run a bash script using `bash scriptname`, but you can also make the script executable so that you do not need to call `bash` to run the script.  The permissions need to be changed with `chmod`. Here we will give all users read, write, and execute priviledges. 

```bash
# change permissions so script is executable
$ chmod 777 ExtractBodyM.sh

# open script to add shebang!
$ nano ExtractBodyM.sh
```

Then, we need to add a [shebang!](https://en.wikipedia.org/wiki/Shebang_(Unix)) `#!`to the script. A shebang! tells the computer which program to run the script with, is always preceded by a `#!` and should be on the first line of the script.

![](Week02_files/nano_screen_7.png)

Close `nano` and now you run the script as follows:

```bash
./ExtractBodyM.sh ../data/Pacifici2013_data.csv BodyM.csv
```

---

</p>
</details>


<details><summary>For Loops</summary>
<p>

### `for [variableName] in [list]; do [something]; done` 

* For loops automate repetitive tasks

  * 1 task, 100 files
  
  * Same task, many different arguments


```bash
$ cd ~/CSB/unix/data/miRNA
$ ls

# display first two lines of two fastas ( do not type in the > )
$ for file in ggo_miR.fasta hsa_miR.fasta
> do head -n 2 $file
> done
```

Let us break down the multiline `for` loop above.  

  * Line 1: `file` is the variable name.  
  
    * We could have named it anything but the CSB book uses `file`.  
	
    * I prefer to use `i`.  
  
  * Line 1: `ggo_miR.fasta hsa_miR.fasta` is the list
  
    * A list of file names
  
    * A list can also be the name of a file with a list inside of it
	
	* Or, a list can be a sequence of numbers, e.g. `seq 1 10`

  * Line 2: `head -n2 $file` is the command
  
    * return the first two lines of the file specified in `$file`
	
	* on the first cycle of the loop, `$file` is `ggo_miR.fasta`
	
  * Line 3: `done` tells the code to loop back to line 1 and make `file=hsa_miR.fasta`
  
    * The loop continues cycling until the whole list is complete.
	
	* this loop cycles twice because there are two file names in the list
	

Let us make a longer list of files using a wildcard

```bash
# display first two lines of all fastas
$ for i in *.fasta
> do head -n 2 $i
> done

```

&#x1F4A1; TIP! _When setting a variable equal to a value, don’t use a `$`. When calling the value held in the variable, use a `$`_

---

### Another `for` loop example

In the following for loop, we use a for loop to extract three types of microRNA from all of the `fasta` files and save them into 1 file per type of miRNA.

```bash
# display first two lines of two fastas
$ for miR in miR-208a miR-564 miR-3170
> do grep $miR -A1 *.fasta > $miR.fasta
> done
```

![](Week02_files/forloop.png)

---

</p>
</details>

<details><summary>User Defined Variables</summary>
<p>

We can assign values to variables and recall them later. Variables can have any name, but it is safe to stick with letters, rather than numbers or punctuation.  It can be common to use `.` and or `_` in variable names.

When saving or creating a variable, you never precede it with a `$`.  

When recalling a variable, it is always preceded by a `$` in `bash`

```
VARIABLE=1375
X=10
height=6.3
echo $VARIABLE $X $height
```

---

</p>
</details>

<details><summary>Using Subshells (aka Child Processes) </summary>
<p>

It is often useful to use a unix command to return an argument for another unix command or to generate a value to be saved into a variable.  But how?

In CLI `bash` we are operating a [shell](https://en.wikipedia.org/wiki/Shell_(computing)).  We can specify a [subshell](https://en.wikipedia.org/wiki/Child_process), which is a shell within the shell, by wrapping a unix command or pipeline inside of `$()` 

```bash
VARIABLE=1375
echo $VARIABLE
echo 1375
VARIABLE=$(echo 1375)
echo $VARIABLE

cd ~/CSB/unix/data/Saavedra2013/

ls *txt
FILES=$(ls *txt)
echo $FILES
echo $(ls *txt)

cat *txt
cat $(ls *txt)

cd ../../sandbox

```

These examples are a bit contrived, but you will quickly find that subshells are indispensable when automating

---

</p>
</details>


<details><summary>Tips & Tricks</summary>
<p>

### The `$PATH`

* A variable that holds all paths to directories where executable commands and scripts are located

* When you type `ls`, `bash` looks at `$PATH` to find the `ls` command file

* If you compile and install software manually (not with `apt`), you need to move it to a `$PATH` dir such as `/usr/local/bin`


```bash
# show path variable
$ echo $PATH

# identify the path to the ls command
$ which ls
/bin/ls
```

---

### Line Terminators - Use a Real Text Editor to View

* There are invisible characters at the end of every line in a text document

  * Carriage Return (CR or `\r`)
  
  * Line Feed (LF  or `\n`)
  
* Unix, Linux, Mac systems end lines with `LF`

* Win systems end lines with `CR LF`

* Make sure your remove CR from files made in Windows that will be used in Linux

* This is one of many reasons why we use a Notepad++ or BBedit

Showing line terminators in `Notepad ++`

![](Week02_files/line_terminators.png)

Finding CR and replacing with nothing in `Notepad ++`

![](Week02_files/line_terminators2.png)

---

### Misc Useful Commands

Note that some of these commands need to be installed on MacOS using `brew`

![](Week02_files/misc_useful_commands.png)

![](Week02_files/misc_useful_commands2.png)

</p>
</details>

---







