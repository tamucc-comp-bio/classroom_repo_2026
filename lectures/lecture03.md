# Week03 UNIX III - Beyond the CSB Text Book


> [!IMPORTANT]
> [Assignment 2](../assignments/assignment_2.md) is due at the beginning of this lecture

> [!NOTE]
> The [Lecture Stream 2025](https://tamucc.zoom.us/rec/play/aq7l-IbbmYNjOPABMHWggcKG-f_xJifCB_GEPQB-PW5YeJzsCmjrtSrZfhJW7Wca_WR5bdg4L7pun4Dm.ZcxgjLKiglMsTD9_) will be updated following lecture.
> Passcode: ^Frf3nM9

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


# In Class Activities

## [I. Quiz 3](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUNEpSWTVNREU0N1IxUDNLU0tPMVYyUkpSRC4u)

## II. Go Over Assignment 02

* [Mind Expander 01.04](https://forms.office.com/r/uvi6cGMSMJ)
* [File Path Scavenger Hunt!](https://forms.cloud.microsoft/r/Zq7avbJpqu)
* [Non-TAMUCC Students: File Path Scavenger Hunt!](https://forms.cloud.microsoft/r/036fdetK5g)
* [Exercise 1.10.2 Hormone Levels in Baboons](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUQldJQTVHMTlYMFVYTkhZSDBZR1A0Q1E2Ny4u)
* [Exercise 1.10.3 Plant-Pollinator Networks](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMlpVSUQ0U1hTSFZERDE1WUdZWjRYUlhaWi4u)

## III. Review of What We Have Learned
<details><summary>Click to expand</summary>
<p>

1. There are several commands for navigating and manipulating a computer file directory.  I made a [linux cheat sheet](../resources/CheatSheetLinux_2022-09-02.pdf) for students learning to use linux that you can print out on a single double sided sheet of paper and use as a desk reference. 
	  * `cd`    change directories
	  * `pwd`   where am I?
	  * `ls`    show contents of `pwd`
	  * `cp`    copy files and directories from one location to another, could also rename copied file
	  * `mv`    move files and directories from one location to another, rename file or directories
	  * `rm`    delete file or dir, be careful, there is no undo
	  * `mkdir` make new directory, will not overwrite existing dir
	  * `less`  view a file without opening all of it, good for large files
	  * `nano`  word processor, edit text files
	  * `chmod` change file and dir permissions

2. Each command has *options* and accepts *arguments* to modify functionality and which can be viewed in the manual
	  * `man`   show manual for command
	  * `_command_ -h` if man does not work, this could show manual for command
	  * command` --help` another way to display manual
	  * command   another way to display manual
	  * use web browser to search on *bash command man*
	  * example of argument: `ls data` will return the file and contents of directory in pwd that are named *data* if they exist
	  * example of option:  `ls -ltrh` will return all files in `pwd` with details, in reverse chronological order with human-readable file sizes

3. Locations of files and dirs can be specified using absolute or relative *paths* and these *paths* are used by the majority of commands because most commands manipulate files and dirs

	  * `/`     root dir, top dir in directory tree
	  * `~`     home dir
	  * `-`     last directory your were in before the `pwd`
	  * `../`   parent directory, one directory up the tree from `pwd`
	  * `../../` 2 directories up the tree from `pwd`
	  * `./`    present working directory

4. Wildcards can be used to specify several files with one word or path

	* `*` can be any character
	* example: `ls *.txt` will list all files ending in `.txt` 

5. There are several commands we have learned that are important for manipulating biological data.

	* `echo`  prints text or converts text and the contents of variables into a text stream
	* `head`  returns only first few lines of a file, or remove last lines (rows)
	* `tail`  returns only last few lines of a file, or remove first lines (rows)
	  * `cut`   returns specified columns
	  * `cat`   combines files together by line (row)
	  * `uniq`  removes duplicates
	  * `sort`  changes the order of rows by column
	  * `grep`  returns lines (rows) that match a pattern
	  * `tr`    replaces one character with another, usually column delimiters (aka field separators)
	  * `wc`    count words, characters, lines, etc

6. Unix commands are designed to pipe `|` and redirect `>` text streams to construct pipelines that link commands and create new files
	  * `|`     takes standard output (*stdout*) from one command and pipes it to another command as *stdin*
	  * `>`     redirects *stdout* into a file of your naming, will overwrite existing file
	  * `>>`    redirects *stdout* into a file of your naming, will append existing file

7. The escape character `\ ` changes the meaning of the character that follows, including end of lines
	  * at the end of a line, it means do not end line and continue on next line
	  * `\t`   is a tab, but not all commands recognize this
	  * `\n`   is a line feed (*LF*), the unix end of line character (usually invisible)
	  * `\r`   is a carriage return (*CR*), in windows every line concludes with CRLF, and causes compatibility issues with unix/linux/mac 
	  * there are MANY more uses of `\ `

8. We can assign values to variables
	  ```bash
	  VARIABLE=1375
	  ```

9. We have learned how to use unix commands within a line of code to return a value with `$()` 

	  ```bash
	  VARIABLE=$(echo 1375)
	  cat <(ls *)
	  FILES=$(ls *)
	  ```

10. Repetative tasks can be automated using `for` loops

	  ```bash
	  for i in $VARIABLE; do
		echo $i
	  done
	  ```

11. Many lines of commands can be stored in file (script) and executed sequentially

	  ```
	  bash script.sh
	  ```

	  Each "pipe line" is like a sentence in English.  It can stand on its own.  It tells the computer to do something and output the result.  The script will be composed of several pipelines.
	  

12. Values can be passed into a script by listing them as argumnents which are stored sequentially into variables: `$1`, `$2`, `$3`, etc
	```
	# run script with the argument "../data.txt" 
	bash script.sh ../data.txt
	```
	
	The argument `../data.txt` is represented by `$1` inside script
	
	```
	#!/bin/bash
	
	InFilePath=$1
	
	cat $inFilePath
	```

---

</p>
</details>


## IV. Additional Important Unix Commands and Intro to Regular Expressions for Pattern Matching

<details><summary>Click to expand</summary>
<p>

Let us all move to our `~/CSB/unix/sandbox` and copy the Marra and Dalziel data to the `sandbox` if it is not already there.
  ```bash
  $ cd ~/CSB/unix/sandbox
  $ cp ../data/Marra2014_data.fasta .
  $ cp ../../python/data/Dalziel2016_data.csv .
  $ less -S Marra2014_data.fasta
  
  >contig00001  length=527  numreads=2  gene=isogroup00001  status=it_thresh
  ATCCTAGCTACTCTGGAGACTGAGGATTGAAGTTCAAAGTCAGCTCAAGCAAGAGATTTG
  TTTACAATTAACCCACAAAAGGCTGTTACTGAAGGTGTGGCTTAAGTGTCAGAGCAACAG
  CTATGAGTGGAGGAATTTTCTATTACAATATAATTTCATCTCTGGTAAATTGACCAATTA
  ACTGGAACTTTTTCCAACTGAAATAAATGGTAAACTTTTTATCCACCATTCTGCCATCTG
  ACTCACAAAGACCCATGGGAATGGGTGATGAAATCCAACATGCTTCTTTGTAGCAAAAAT
  AAATAAAATCCCCAGAAGGGTGAGGTAAATGGAAAACTCCAAACTCGCCCCTCAGGTGGG
  TGTAATTTACCCAAGTCTGAGAGGAGGCAGAGTTTTTCCCAATGGACTTTGGTTAAGTGA
  GATATGCTGGTCTGTAGAAGGAGGGAGTTCTAGGAAAACAGACACTTAAGTAGGGCCGAA
  CTAAAAATTGTATCAGTCAGATCTTCATGTGAAGTCCTGTGTGCCCA
  
  # use q to exit less
  ```

---

`Marra2014_data.fasta` is an interleaved FASTA file.  Interleaved means that a single squence is spread across multiple lines, it makes data manipulation difficult. There are tools to convert between an interleaved and non-interleaved format, but let's just create our own and name it `deInterleaveFASTA.sh`.

``` bash
# for those with Macs, let me know if this returns an error
touch deInterleaveFASTA.sh
echo '#!/bin/bash' > deInterleaveFASTA.sh && echo 'awk '"'"'/^>/ {if (seq) print seq; print; seq=""} /^[^>]/ {seq=seq $0} END {if (seq) print seq}'"'"' "$1"' >> deInterleaveFASTA.sh
```

Take a look at the script we just created

```bash
cat deInterleaveFASTA.sh
```

You should see the following:

```
#!/bin/bash
awk '/^>/ {if (seq) print seq; print; seq=""} /^[^>]/ {seq=seq $0} END {if (seq) print seq}' "$1"
```

And then let's test our new script for converting interleaved to non-interleaved FASTA files

```bash
# for those with Macs, let me know if this doesn't work...
bash deInterleaveFASTA.sh Marra2014_data.fasta | less -S
```

The sequences should each be on 1 line, rather than several.

```
>contig00001  length=527  numreads=2  gene=isogroup00001  status=it_thresh
ATCCTAGCTACTCTGGAGACTGAGGATTGAAGTTCAAAGTCAGCTCAAGCAAGAGATTTGTTTACAATTAACCCACAAAAGGCTGTTACTGAAGGTGTGGCTTAAGTGTCAGAGCAACAGCTATGAGTGGAGGAATTTTCTATTACAATATAATTTCATCTCTGGTAAATTGACCAATTAACTGGAACTTTTTCCAACTGAAATAAATGGTAAACTTTTTATCCACCATTCTGCCATCTGACTCACAAAGACCCATGGGAATGGGTGATGAAATCCAACATGCTTCTTTGTAGCAAAAATAAATAAAATCCCCAGAAGGGTGAGGTAAATGGAAAACTCCAAACTCGCCCCTCAGGTGGGTGTAATTTACCCAAGTCTGAGAGGAGGCAGAGTTTTTCCCAATGGACTTTGGTTAAGTGAGATATGCTGGTCTGTAGAAGGAGGGAGTTCTAGGAAAACAGACACTTAAGTAGGGCCGAACTAAAAATTGTATCAGTCAGATCTTCATGTGAAGTCCTGTGTGCCCA
```

---

### [`paste`](https://ss64.com/bash/paste.html) is used for binding files and text objects together by adding *columns* (recall that `cat` binds by row) or converting a file with one column into a file with several columns
  
  Paste is very convenient for converting non-tidy data into tidy data.  An example is `Marra2014_data.fasta`.  There is only 1 column and each row contains different types of information about different observational units.  Because there are the two lines per observational unit, the file can be converted to a tidy format which is easier to modify.  
  
Note that we will use the `deInterleaveFASTA.sh` script so that sequences aren't spread across multiple lines.
  
  ```bash
  # we can use the paste command to take a single column of data and make it multi column
  $ bash deInterleaveFASTA.sh Marra2014_data.fasta | paste - - | less -S

  >contig00001  length=527  numreads=2  gene=isogroup00001  status=it_thresh      ATCCTAGCTACTCTGGAGACTGAGGATTGAAGTTCAAAGTCAGCTCAAGCAAGAGATTTGTTTACAATTAACCCACAAAAGGCTGTTACTGAAGGTGTGGCTTAAGTGTCAGAGCAACAGCTATGAGTGGAGGAATTTTCTATTACAATATAATTTCATCTCTGGTAAATTGACCAATTAACTGGAACTTTTTCCAACTGAAATAAATGGTAAACTTTTTATCCACCATTCTGCCATCTGACTCACAAAGACCCATGGGAATGGGTGATGAAATCCAACATGCTTCTTTGTAGCAAAAATAAATAAAATCCCCAGAAGGGTGAGGTAAATGGAAAACTCCAAACTCGCCCCTCAGGTGGGTGTAATTTACCCAAGTCTGAGAGGAGGCAGAGTTTTTCCCAATGGACTTTGGTTAAGTGAGATATGCTGGTCTGTAGAAGGAGGGAGTTCTAGGAAAACAGACACTTAAGTAGGGCCGAACTAAAAATTGTATCAGTCAGATCTTCATGTGAAGTCCTGTGTGCCCA
  >contig00002  length=551  numreads=8  gene=isogroup00001  status=it_thresh      GAACCATCCTGCGCGGGAAAGATCTAGAAGCTGGCACGTCAAACTGCTGCCGAGTAACGACTGTGAAAATACAGAGCAGAACGTACAGGTGGTAATGCACTGGAAAGGAAGAAACTGATCGTCTCCTGTGACCTCCAGATTCCACTGGCATAAGTACTGTCATCTGTGTGCCACACAGAAAGGCGCTCCGTGGTAAAGTACGATCATCACCAATCTACCTATAAGAGAAACAGACTGGCTCCACAGTGCAAGTATAAGGGAGACTTGGAGAAGGCACTTGAAGGCACTGTTTTAATTAATTCCATCATTTCTTTGGTATTTCTCAGGCTTTGGGATCCTCTGTAAACCTGGCATCCACTGGTGGAAGCTTTATGGGTGTGGGGGAGGCACTGGCATCATCAGAGTGCGACGGTCCTCAGCAGGTTCCCCGGGGTGCCCGGCCCCACCACGTATGTGCACTCCGACTTCTCTGCAAACTTCCCGCAGCAGGACCAGTGGGGACGGCCCGGATGGCCCTTGTGTCCGTGACCGCAGCCCAGGTACCCACCTGg
  ```
  
  ```bash
  # we can also use paste to join files by column, instead of by row (cat)
  # while you would not want to combine these two files, you can:
  $ paste Dalziel2016_data.csv Marra2014_data.fasta | less -S
  ```
  
  ```bash
  biweek,year,loc,cases,pop       >contig00001  length=527  numreads=2  gene=isogroup00001  status=it_thresh
  1,1906,BALTIMORE,NA,526822.1365 ATCCTAGCTACTCTGGAGACTGAGGATTGAAGTTCAAAGTCAGCTCAAGCAAGAGATTTG
  2,1906,BALTIMORE,NA,526995.246  TTTACAATTAACCCACAAAAGGCTGTTACTGAAGGTGTGGCTTAAGTGTCAGAGCAACAG
  3,1906,BALTIMORE,NA,527170.1981 CTATGAGTGGAGGAATTTTCTATTACAATATAATTTCATCTCTGGTAAATTGACCAATTA
  4,1906,BALTIMORE,NA,527347.0136 ACTGGAACTTTTTCCAACTGAAATAAATGGTAAACTTTTTATCCACCATTCTGCCATCTG
  5,1906,BALTIMORE,NA,527525.7134 ACTCACAAAGACCCATGGGAATGGGTGATGAAATCCAACATGCTTCTTTGTAGCAAAAAT
  6,1906,BALTIMORE,NA,527706.3183 AAATAAAATCCCCAGAAGGGTGAGGTAAATGGAAAACTCCAAACTCGCCCCTCAGGTGGG
  7,1906,BALTIMORE,NA,527888.849  TGTAATTTACCCAAGTCTGAGAGGAGGCAGAGTTTTTCCCAATGGACTTTGGTTAAGTGA
  8,1906,BALTIMORE,NA,528073.3264 GATATGCTGGTCTGTAGAAGGAGGGAGTTCTAGGAAAACAGACACTTAAGTAGGGCCGAA
  9,1906,BALTIMORE,NA,528259.7712 CTAAAAATTGTATCAGTCAGATCTTCATGTGAAGTCCTGTGTGCCCA
  ```
  
  The output looks odd because the files `Dalziel2016_data.csv` and `Marra2014_data.fasta` do not have the same format or observational units.  This was just a demonstration that paste treats each file as a column and binds them together as separate columns, row by row.
  
  &#x1F4A1; TIP! _It is very common to use subshells to pass text streams to `paste` (and `cat`).  When doing this, we use the following syntax `<()`_
  
  ```
  paste <(echo Testing) <(echo 1) <(echo 2) <(echo 3)
  
  cat <(echo Testing) <(echo 1) <(echo 2) <(echo 3)
  ```
  


---

## [`sed`](https://ss64.com/bash/sed.html) can be used to find a pattern and replace it with text or a specified pattern

`sed` is a very versatile tool and we will only scratch the surface of what it can do, but 99.9% of the time, you will use it to find and replace text.

### `sed 's/FindThisRegExPattern/ReplaceWithThis/g'`

* the `s` triggers the *search* functionality of `sed`, its essentially an option

* The `/` divides the statement into its component arguments

* The `g` is optional and means *global*.  If present, all pattern matches will be replaced.  If there is no `g`, then only the first match on each line is replaced. See below to observe what happens without the `g`

  ```bash
  # find the first T on each line and replace with @
  $ sed 's/T/@/' Marra2014_data.fasta | head
  >contig00001  length=527  numreads=2  gene=isogroup00001  status=it_thresh
  A@CCTAGCTACTCTGGAGACTGAGGATTGAAGTTCAAAGTCAGCTCAAGCAAGAGATTTG
  @TTACAATTAACCCACAAAAGGCTGTTACTGAAGGTGTGGCTTAAGTGTCAGAGCAACAG
  C@ATGAGTGGAGGAATTTTCTATTACAATATAATTTCATCTCTGGTAAATTGACCAATTA
  AC@GGAACTTTTTCCAACTGAAATAAATGGTAAACTTTTTATCCACCATTCTGCCATCTG
  AC@CACAAAGACCCATGGGAATGGGTGATGAAATCCAACATGCTTCTTTGTAGCAAAAAT
  AAA@AAAATCCCCAGAAGGGTGAGGTAAATGGAAAACTCCAAACTCGCCCCTCAGGTGGG
  @GTAATTTACCCAAGTCTGAGAGGAGGCAGAGTTTTTCCCAATGGACTTTGGTTAAGTGA
  GA@ATGCTGGTCTGTAGAAGGAGGGAGTTCTAGGAAAACAGACACTTAAGTAGGGCCGAA
  C@AAAAATTGTATCAGTCAGATCTTCATGTGAAGTCCTGTGTGCCCA
  
  # find the all T and replace with @
  $ sed 's/T/@/g' Marra2014_data.fasta | head
  >contig00001  length=527  numreads=2  gene=isogroup00001  status=it_thresh
  A@CC@AGC@AC@C@GGAGAC@GAGGA@@GAAG@@CAAAG@CAGC@CAAGCAAGAGA@@@G
  @@@ACAA@@AACCCACAAAAGGC@G@@AC@GAAGG@G@GGC@@AAG@G@CAGAGCAACAG
  C@A@GAG@GGAGGAA@@@@C@A@@ACAA@A@AA@@@CA@C@C@GG@AAA@@GACCAA@@A
  AC@GGAAC@@@@@CCAAC@GAAA@AAA@GG@AAAC@@@@@A@CCACCA@@C@GCCA@C@G
  AC@CACAAAGACCCA@GGGAA@GGG@GA@GAAA@CCAACA@GC@@C@@@G@AGCAAAAA@
  AAA@AAAA@CCCCAGAAGGG@GAGG@AAA@GGAAAAC@CCAAAC@CGCCCC@CAGG@GGG
  @G@AA@@@ACCCAAG@C@GAGAGGAGGCAGAG@@@@@CCCAA@GGAC@@@GG@@AAG@GA
  GA@A@GC@GG@C@G@AGAAGGAGGGAG@@C@AGGAAAACAGACAC@@AAG@AGGGCCGAA
  C@AAAAA@@G@A@CAG@CAGA@C@@CA@G@GAAG@CC@G@G@GCCCA
  ```

---

## Regular Expressions (regex) are sequences of characters that define search patterns.  

There are different regex languages (POSIX, PERL, etc) that have slight differences in the meanings of different characters.  Regex is critical for `grep`, `sed`, and other commands associated with pattern matching and we will learn more regex later in the course.

### `^`     Beginning of line

### `$`     End of line

### `[]`    Any of of the characters inside the square brackets are a match for a single character

### `.`     Any character

### `*`     Any number of repeats of the previous character, including zero  (meaning the absence of the previous character)

### `\ `     Escape character 
  
  ```bash
  # return contig names for either isogroup00001 or isogroup00002 in Marra data
  $ grep 'isogroup0000[12]' Marra2014_data.fasta 
  >contig00001  length=527  numreads=2  gene=isogroup00001  status=it_thresh
  >contig00002  length=551  numreads=8  gene=isogroup00001  status=it_thresh
  >contig00003  length=541  numreads=2  gene=isogroup00001  status=it_thresh
  >contig00004  length=291  numreads=3  gene=isogroup00001  status=it_thresh
  >contig00005  length=580  numreads=12  gene=isogroup00001  status=it_thresh
  >contig00006  length=3288  numreads=35  gene=isogroup00001  status=it_thresh
  >contig00008  length=1119  numreads=10  gene=isogroup00001  status=it_thresh
  >contig00010  length=202  numreads=4  gene=isogroup00001  status=it_thresh
  >contig00011  length=5563  numreads=61  gene=isogroup00001  status=it_thresh
  ```

  ```bash
  # return lines that begin with A
  $ grep '^A' Marra2014_data.fasta 
  ATCCTAGCTACTCTGGAGACTGAGGATTGAAGTTCAAAGTCAGCTCAAGCAAGAGATTTG
  ACTGGAACTTTTTCCAACTGAAATAAATGGTAAACTTTTTATCCACCATTCTGCCATCTG
  ACTCACAAAGACCCATGGGAATGGGTGATGAAATCCAACATGCTTCTTTGTAGCAAAAAT
  AAATAAAATCCCCAGAAGGGTGAGGTAAATGGAAAACTCCAAACTCGCCCCTCAGGTGGG
  AGGCGCTCCGTGGTAAAGTACGATCATCACCAATCTACCTATAAGAGAAACAGACTGGCT
  AGGTTCCCCGGGGTGCCCGGCCCCACCACGTATGTGCACTCCGACTTCTCTGCAAACTTC
  ```

---


## Basic addition and subtraction

We need to tell `bash` that we are asking for arithmetic by wrapping the equation with `$(())`.  No spaces should be used.

  ```bash
  # addition
  X=$((1+1))
  echo $X
  
  # subtraction
  Y=$((10-5))
  echo $Y
  
  echo $((1+11-2))
  
  ```

---

## Decision logic with if-then-else statements

We can program a computer to make decisions.  

* If something is true, then do "this", otherwise do "that".  

* If X is true, then do Y; else if Z is true, then do W; else if A is true, then do B

If-then statements have a standard multiline architecture with a distinct beginning (`if`) and end (`fi`) and internal spacing matters. There are no optional internal spaces, they are required where you see them

In a script, it is a good practice to indent the code between `if`, `else`, and `fi`

```bash
if [ 1 == 2 ]; then                # if 1 equals 2 then
  echo 1 does equal 2               # print "1 does equal 2" to screen
else                               # if 1 does not equal 2 then
  echo 1 does not equal 2          # print "1 does not equal 2" to screen
fi                                 # end of if statement
```
  
In the if-then statement, the square brackets denote the condition to test.  Note that two equals signs are neccessary.  Also note below that we quotified the variables `$A` and `$B`.  I recommend that you consult a web resource when constructing if then statements in bash because the syntax can be tricky and I am not showing everything that is possible here.
  
```bash
A="orangutang"
B=100
if [ "$A" != "$B" ]; then
  echo $A does not equal $B
else
  echo $A does equal $B 
fi  
```

---


## A function allows you to define a new customized command composed of several existing commands

A function is a command that you can define and use in the terminal environment or a script. You should make a function when you find yourself repeatedly using the same code over and over. 

Let us build upon the if-then-else logic in the last section to create a function that decides whether the two arguments passed to it are equal.

* The name of the function is `DOES_A_EQUAL_B`

* The `()` are there because other languages have the same structure, but they do not do anything

* you *_cannot_* define default input variable values in the parentheses `()`, like you would in `R`

* The code passed to the function is wrapped in curly brackets `{}`

* everything else is just `bash` code

Note that a function treats "arguments" just like a script.  The first argument becomes `$1`, the second `$2`, etc. It is good practice to convert the variables containing arguments into variables with more meaningful names in the first lines of the function. 

Also note the indenting to make code readable and signify hierarchy

```bash
DOES_A_EQUAL_B(){
A=$1
B=$2
if [ "$A" != "$B" ]; then
  echo $A does not equal $B
else
  echo $A does equal $B 
fi 
}
  ```

After you enter the function, nothing will happen, but it has been stored into memory and can now be used.

```bash
DOES_A_EQUAL_B 1 2
  ```

---

</p>
</details>


## V. Real World Application of Skills Learned: Fisheries-Induced Evolution

My lab has been studying the evolution of limpets in Hawaii.  They are a local delicacy and are under intense harvesting pressure.  We are interested in the selective pressures applied by overharvesting and how it affects the evolution of phenotypes.  

We found that shell surface area is associateD with human harvesting and want to use 3d scans of the limpet shells to more precisely test of effects of harvesting on phenotype. Here are some views of a 3d scan:

![alt text](Week03_files/3Dscan_limpetShell.PNG) ![alt text](Week03_files/3Dscan_limpetShell_left.PNG) ![alt text](Week03_files/3Dscan_limpetShell_right.PNG) ![alt text](Week03_files/3Dscan_limpetShell_top.PNG) ![alt text](Week03_files/3Dscan_limpetShell_bottom.PNG)

#### [Related Publication from my Research Group](https://onlinelibrary.wiley.com/doi/abs/10.1111/jbi.13845?af=R)

The images above are rendered 3d scans, but the data file is in [STL](https://en.wikipedia.org/wiki/STL_%28file_format%29) format.  An `*.stl` file is obtuse and not the easiest for a human to read.  Consequently, a tool to extract information from `*.stl` files, [admesh](https://admesh.readthedocs.io/en/latest/#), was created as a master's thesis.  I found this program on GitHub and used it to extract the surface areas of the shells.  It was the best program I could find to automate this task.  Unfortunately, I did also have to manipulate the `*.stl` files and clip off the bottom surface covering the shell aperature using a bash tool that I made.  

Unfortunately, the output of `admesh` is not tidy.  Fortunately for you, I made a tool to tame the `admesh` output, `admesh2tsv.bash`. I'll show you how this works and then you'll edit it for homework.

#### Clone the [`admesh2tsv` repo](https://github.com/comp-bio-master/admesh2tsv) to your `comp_bio` dir

```bash
mkdir ~/comp_bio  
# you should get an error here saying that you've already created this dir
cd ~/comp_bio
git clone git@github.com:comp-bio-master/admesh2tsv.git

# move into the new Repo and explore
cd admesh2tsv
ls -lh
cat README.md
less -S admesh.out
less -S admesh2tsv.bash
```

In the lecture, I will orient you to this repo which is similar, but not the same as your homework repo.

### IMPORTANT: delete the `admesh2tsv` repo we cloned in class before doing the homework. For the home work, you will clone your homework repo, which is very similar to `LimpetShellEvolution`, to your computer and complete you work there.

```
cd ~/comp_bio
rm -rf admesh2tsv
```

---








