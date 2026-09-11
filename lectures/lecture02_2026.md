# Week02 UNIX II: From Commands to Pipelines to Scripts

> [!IMPORTANT]
> [Assignment 1](https://classroom50.org/tamucc-comp-bio-assignments/comp-bio-skills-2026/assignments/assignment-1/accept) is due at the beginning of this lecture. Submit its online forms and push your work from your `assignment-1` repository.

> [!NOTE]
> The [2025 lecture recording](https://tamucc.zoom.us/rec/play/pfgVVA9Bsk-di4MUxhHCxwL9kKJFOqZNeqw9ZgNV59MMlaxYxJaARqcDpYSbh0rZRK5iv1RJB8dUe29l.0g9hG3R7k_b1Hqyz) is available as a reference. Passcode: !N6*?2HL
> Its paths and some commands differ from this year's instructions.

The [Lecture 02 slides](Week02_files/Lecture02_WelcomeToTheMatrix.pdf) and CSB Chapter 1 provide additional background. Follow the commands on this page for the current repository layout.

In Lecture 1, you practiced navigating directories and manipulating files. In Assignment 1, you connected commands to process biological data. Today we will turn those commands into documented scripts that we can run again and apply to many files.

By the end of this lecture, you should be able to:

* build and check a pipeline one command at a time;
* save a pipeline as a Bash script;
* supply input and output paths as arguments;
* use variables and a `for` loop to repeat a task; and
* commit and push your scripts, results, and notes to GitHub.

---

## Computer Preparation

Complete the [Computer Setup Checklist](../resources/computer_setup_checklist.md). Use Ubuntu on Windows or Terminal on macOS. If your Mac opens a `zsh` shell, enter `bash` before working through the examples.

Keep this page open beside your terminal. Command blocks omit the terminal's `$` and `>` prompts so you can copy the commands directly. A line beginning with `#` is a comment; Bash ignores it.

---

## [Week 02 Quiz](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMjIySEJCNFlSMVJRSUo0SU5HSFNKMVRHWC4u)

Complete the quiz while everyone gets ready.

---

## Set Up Your Lecture 2 Repository

Accept **Lecture 2** using the Classroom 50 link provided by your instructor. Classroom 50 creates your personal GitHub repository, just as it did for Lecture 1 and Assignment 1.

<!-- Instructor: replace the preceding sentence with the verified Lecture 2 acceptance link after creating the activity. Starter files and setup notes are in ../resources/classroom50/lecture-2-setup.md. -->

1. Open **your Lecture 2 repository** on GitHub.
2. Click the green **Code** button, select **SSH**, and copy the address.
3. Go to your home directory:

   ```bash
   cd ~
   ```

4. Replace `YOUR-COPIED-SSH-ADDRESS` below with your address and clone into a directory named `lecture-2`:

   ```text
   git clone YOUR-COPIED-SSH-ADDRESS lecture-2
   ```

5. Enter your clone and inspect it:

   ```bash
   cd ~/lecture-2
   pwd
   ls
   git status
   ```

If you already cloned Lecture 2, enter that directory instead of cloning it again. Your personal repositories are separate projects; use the Lecture 2 clone for today's work.

| Location in `~/lecture-2` | Purpose |
| --- | --- |
| `README.md` | Getting started and link to this lecture |
| `CSB/unix/data/` | Supplied biological data and source descriptions |
| `CSB/unix/sandbox/` | Your practice files, scripts, results, and notes |

Enter the sandbox:

```bash
cd ~/lecture-2/CSB/unix/sandbox
pwd
ls ../data
```

Your path should end with `/lecture-2/CSB/unix/sandbox`. From here, `../data` means go up to `unix`, then into `data`.

> [!IMPORTANT]
> Keep the supplied files in `data` unchanged. Save your work in `sandbox`. All examples below use this Lecture 2 repository, including the Assignment 1 review.

---

## Review Assignment 1

<details><summary>Pipes, filters, and finding things</summary>

Start here whenever you need to reset your working directory:

```bash
cd ~/lecture-2/CSB/unix/sandbox
```

### Redirection and pipes

Predict what each command will do before running it:

```bash
echo "My first line" > test.txt
echo "My second line" >> test.txt
cat test.txt
wc -l < test.txt
```

| Operator | Meaning |
| --- | --- |
| `>` | Write output to a file, replacing its contents if it exists |
| `>>` | Append output to a file |
| `<` | Read a file as a command's input |
| `\|` | Pass one command's output into the next command |

Never redirect output back into the input file: Bash opens and empties the output file before the command reads it.

![Commands connected by a pipe](Week01_files/pipeline.png)

How many plant–pollinator network files are supplied?

```bash
find ../data/Saavedra2013 -type f -name '*.txt' | wc -l
```

Expected result: **59**. `find` selects files; `wc -l` counts the resulting lines. These supplied filenames do not contain newline characters.

### Inspect a table before processing it

```bash
head -n 3 ../data/Pacifici2013_data.csv
head -n 1 ../data/Pacifici2013_data.csv | tr ';' '\n'
```

Despite its `.csv` extension, this file separates columns with semicolons. Spaces inside a species name are part of the name, not column separators.

* `cut -d ';'` specifies the input delimiter.
* `-f 2` selects the second field (column), **Order**.
* `tail -n +2` starts at line 2, omitting the header.
* `uniq` groups adjacent identical lines; sort first to bring matching values together.

Build the pipeline one step at a time:

```bash
cut -d ';' -f 2 ../data/Pacifici2013_data.csv | head
cut -d ';' -f 2 ../data/Pacifici2013_data.csv | tail -n +2 | head
cut -d ';' -f 2 ../data/Pacifici2013_data.csv | tail -n +2 | sort | uniq -c
cut -d ';' -f 2 ../data/Pacifici2013_data.csv | tail -n +2 | sort | uniq -c | sort -nr | head -n 1
```

Which order has the most records? Explain what the final `sort -nr` adds. These are counts of records in this dataset, not estimates of animal abundance.

### `grep` versus `find`

```bash
# Search inside a file.
grep -n 'Gorilla' ../data/Pacifici2013_data.csv

# Find a file by its name.
find ../data -type f -name 'n30.txt'
```

Put the filename pattern in quotes so `find` receives it unchanged.

</details>

<details><summary>Mind Expander and exercise review</summary>

Bring up the questions that were most challenging in Assignment 1:

* [Mind Expander 01.03](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUOThBNjZNVzlGQUtJUzhYREZVSE5UVVJMNS4u)
* [Exercise 1.10.1: Next Generation Sequencing Data](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMTVENFg0UjhFTzc3Wkc0NExRTjdLSjdGNi4u)

Open your Assignment 1 answers for this discussion. Any additional Marra data commands for that exercise belong in your Assignment 1 repository.

Additional reference: [Software Carpentry: Pipes and Filters](https://swcarpentry.github.io/shell-novice/04-pipefilter.html) and [Finding Things](https://swcarpentry.github.io/shell-novice/07-find.html).

</details>

<details><summary>Discuss the reading: Wilson et al. (2017)</summary>

The response summaries below are retained from the previous version of this lecture. Discuss this year's responses in class.

[Good enough practices (Wilson etal 2017)](../literature/Wilson_etal_2017_good_enough_practices_in_scientific_computing.pdf)

<details><summary>What is the main point of the Wilson etal 2017 manuscript?</summary>

**Core takeaway:** Wilson et al. (2017) argues that many scientists lack formal computing training, and offers practical, accessible guidelines—covering data management, simple coding, version control, documentation, and project organization—to reduce errors, improve efficiency, and make research reproducible.

**Key points:**

* Scientists commonly use computers without proper training, leading to inefficiencies and data loss.
* The paper provides beginner-friendly tools and minimum best practices anyone can adopt.
* Emphasis on organizing projects for human and machine readability.
* Focus on reproducibility, reliability, and collaboration through clear code, data standards, and documentation.
* Goal is optimization of everyday research workflows, not advanced techniques.

---

 </details>

<details><summary>What do you like about the Wilson etal 2017 manuscript?</summary>

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

 </details>

<details><summary>Do you disagree with Wilson etal 2017 on any of their points?</summary>

**Overall verdict**

* **No disagreements.** Respondents broadly agree with Wilson et al. (2017) and found the guidance accurate and useful.

**Why they agree**

* The points match real-world pain: many have made or fixed the exact mistakes the paper addresses.
* The low barrier, “good-enough” practices are practical and helpful—especially for beginners.

**Nuanced caveat raised by a few**

* While the advice is great for getting started, **“good enough” may fall short** for advanced users or high-stakes/complex projects, where stricter practices may be needed.

---

 </details>

<details><summary>What was confusing or do you have any questions about Wilson etal 2017?</summary>

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
  * *Rule of thumb:* I generally think word is "good enough" for manuscripts!. Markdown works well for README files and other documentation displayed on GitHub
* **Directories & “track changes” (cheat sheet)**

  * **Directories:** `project/` → `data_raw/`, `data_clean/`, `scripts/`, `results/`, `docs/`, `README.md`.
  * **Tracking changes:** Prefer Git over Word “Track Changes.” For now, use the familiar status → add → commit → push workflow and meaningful commit messages.
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
      ## 2026-09-11
      - Input: data_raw/fish_survey.csv (sha256: abc123…)
      - Script: scripts/01_clean.R (v1.2, commit 3f7c2d)
      - Params: min_count=5, drop_na=true
      - Output: data_clean/fish_survey_clean.csv (rows: 12,345)
      - Notes: Removed 23 rows with missing site_id.
      ```
    * **Scripted report:** Use an R Markdown / Jupyter notebook that reads raw → writes clean, with parameters and session info.
    * **Makefile / workflow:** Encode steps as targets (e.g., `make data_clean/fish_survey_clean.csv`), which documents order and dependencies automatically.

---

 </details>

</details>

---


## Additional Important `bash` Commands (CSB 1.6)

<details><summary>Translate characters with tr</summary>

`tr` translates characters in a text stream. It reads from a pipe or from input redirected with `<`.

```bash
echo "aaaabbb" | tr 'a' 'b'
echo "123456789" | tr '1-5' '0'
echo "ACtGGcAaTT" | tr '[:lower:]' '[:upper:]'
echo "aabbccddee" | tr 'a-c' '1-3'
echo "aaaaabbbb" | tr -d 'a'
echo "aaaaabbbb" | tr -s 'a'
```

In order, these commands return `bbbbbbb`, `000006789`, `ACTGGCAATT`, `112233ddee`, `bbbb`, and `abbbb`.

* `-d` deletes the specified characters.
* `-s` squeezes repeated instances of the specified characters into one.
* Quote character classes such as `'[:lower:]'` so the shell passes them to `tr`.

For example, view the Pacifici data with tabs between columns:

```bash
cd ~/lecture-2/CSB/unix/sandbox
tr ';' '\t' < ../data/Pacifici2013_data.csv | less -S
```

Press `q` to exit `less`. Here, `tr` interprets `\t` as a tab. Escape sequences are command-dependent; not every command interprets `\t` the same way.

`tr` changes individual characters, not whole words. These examples work for this simple delimited dataset; `tr` and `cut` do not understand quoted CSV fields containing delimiters or embedded newlines.

</details>

<details><summary>Build a body-mass table</summary>

### Biological question: Which mammals have the largest adult body masses?

Create a table containing the taxonomic information and body masses, sorted from largest to smallest.

```bash
cd ~/lecture-2/CSB/unix/sandbox
head -n 1 ../data/Pacifici2013_data.csv | tr ';' '\n'
```

Select original columns 2–6. Count the columns **after** selection:

| New column | Original column | Variable |
| --- | --- | --- |
| 1 | 2 | Order |
| 2 | 3 | Family |
| 3 | 4 | Genus |
| 4 | 5 | Scientific_name |
| 5 | 6 | AdultBodyMass_g |

Build and inspect the pipeline in stages:

```bash
# Select five columns.
cut -d ';' -f 2-6 ../data/Pacifici2013_data.csv | head

# Remove the header from the text stream.
cut -d ';' -f 2-6 ../data/Pacifici2013_data.csv | tail -n +2 | head

# Sort by the fifth selected column, keeping semicolons as delimiters.
cut -d ';' -f 2-6 ../data/Pacifici2013_data.csv | tail -n +2 | sort -t ';' -k5,5nr | head

# Convert semicolons to tabs for a TSV output file.
cut -d ';' -f 2-6 ../data/Pacifici2013_data.csv | tail -n +2 | sort -t ';' -k5,5nr | tr ';' '\t' > BodyMass.tsv

head -n 5 BodyMass.tsv
wc -l BodyMass.tsv
```

`sort -t ';' -k5,5nr` uses semicolons to identify fields, sorts only field 5, treats it as a number (`n`), and reverses the order (`r`). Spaces within species names remain intact.

The output has **5,426 rows and five tab-separated columns**, without a header. The first row should be *Balaenoptera musculus*, with an adult body mass of **154,321,304.5 g**. Keep the units in mind!

We name it `BodyMass.tsv` because it contains tabs. Some older slides and the book use `BodyMass.csv` or `BodyM.csv`; use `BodyMass.tsv` in this lecture.

> [!TIP]
> The source description is `../data/Pacifici2013_about.txt`. A sorted table answers a question about the supplied values; it does not establish that every value is complete or error-free.

</details>

<details><summary>Search the body-mass table with grep</summary>

```bash
cd ~/lecture-2/CSB/unix/sandbox

# Find wombat records, then count matching rows.
grep 'Vombatidae' BodyMass.tsv
grep -c 'Vombatidae' BodyMass.tsv

# Compare a substring search with a whole-word search.
grep 'Bos' BodyMass.tsv
grep -w 'Bos' BodyMass.tsv

# Ignore capitalization.
grep -i 'gorilla' BodyMass.tsv

# Show the neighboring rows in the body-mass-sorted table.
grep -B 2 -A 2 'Gorilla gorilla' BodyMass.tsv

# Show line numbers.
grep -n 'Gorilla gorilla' BodyMass.tsv

# Match either genus as a whole word using an extended regular expression.
grep -Ew 'Gorilla|Pan' BodyMass.tsv
```

`grep` returns matching **lines**. `grep -c` counts matching lines, not every occurrence of the pattern. The neighbors around a gorilla record have nearby ranks in this sorted table; this is not a calculation of absolute differences in mass.

In `grep -Ew 'Gorilla|Pan'`, the quoted `|` means **or** in the search pattern. A `|` outside quotes connects shell commands into a pipeline.

</details>

<details><summary>Use filename patterns and find</summary>

We will use the supplied microRNA FASTA files later in a loop. View the matching filenames:

```bash
cd ~/lecture-2/CSB/unix/sandbox
ls ../data/miRNA/*.fasta
ls ../data/miRNA/pp*.fasta
ls ../data/miRNA/[ghm]*.fasta
wc -l ../data/miRNA/*.fasta
```

| Pattern | Meaning |
| --- | --- |
| `*` | Zero or more characters |
| `?` | Exactly one character |
| `[ghm]` | One character: g, h, or m |

These are shell filename patterns, also called **globs**. They are different from the regular expressions used by `grep`.

Search below the data directory:

```bash
find ../data -type f
find ../data -type f -name 'n30.txt'
find ../data -type f -name '*about*'
find ../data -type f -name '*.txt' | wc -l
find ../data -type d
```

`-type f` restricts results to files; `-type d` restricts results to directories. Without a type restriction, `find` can return both.

</details>

<details><summary>Permissions: read, write, and execute</summary>

```bash
cd ~/lecture-2/CSB/unix/sandbox
touch permissions.txt
ls -l permissions.txt
chmod u-w permissions.txt
ls -l permissions.txt
chmod u+w permissions.txt
```

The permission letters are `r` (read), `w` (write), and `x` (execute). They apply separately to the owner, group, and everyone else. `u-w` removes your write permission; `u+w` restores it. Later we will use `u+x` to make a script executable by its owner.

![Reading file permissions](Week01_files/ls-ltrh_3.PNG)

<details><summary>Reference: numeric permissions and administrator commands</summary>

Numeric permissions add read = 4, write = 2, and execute = 1 for each of the three categories. For example, `chmod 754 script.sh` gives the owner read/write/execute, the group read/execute, and everyone else read access.

`sudo` runs a command with elevated privileges, often for system administration such as installing software. `chown` changes ownership. Neither is needed for today's exercises. If a command fails, check the path and error message before deciding that administrator privileges are needed.

</details>

</details>

[Mind Expander 01.04](https://forms.office.com/r/uvi6cGMSMJ): Take 10 minutes to complete.

## [File Path Scavenger Hunt!](https://forms.cloud.microsoft/r/Zq7avbJpqu)

[Non-TAMUCC students: File Path Scavenger Hunt](https://forms.cloud.microsoft/r/036fdetK5g)

Take 10 minutes to complete the scavenger hunt. Any `CSB` paths shown in older questions refer to the same directory relationships inside today's `~/lecture-2/CSB` directory.

---

## Computer Programming with `bash` (CSB 1.7–1.9)

<details><summary>Save a working pipeline as a script</summary>

A **script** is a text file containing commands. Running the script carries out those commands in order. This preserves the processing steps, so you and other researchers can repeat them.

### Create the script

```bash
cd ~/lecture-2/CSB/unix/sandbox
nano ExtractBodyM.sh
```

Type or paste the following **into the editor**:

```bash
#!/usr/bin/env bash
# Extract taxonomy and adult body mass from the Pacifici dataset.
# Output: five tab-separated columns, no header, mass in grams.
# Run from CSB/unix/sandbox: bash ExtractBodyM.sh

# Select original columns 2-6; remove the header; sort selected column 5
# numerically from largest to smallest; convert delimiters to tabs.
cut -d ';' -f 2-6 ../data/Pacifici2013_data.csv |
    tail -n +2 |
    sort -t ';' -k5,5nr |
    tr ';' '\t' > BodyMass.tsv
```

Save with **Ctrl+O**, then **Enter**. Exit with **Ctrl+X**. These are Control-key shortcuts on macOS too.

Run your script in the terminal:

```bash
bash ExtractBodyM.sh
head -n 5 BodyMass.tsv
```

Running it again replaces `BodyMass.tsv` with a freshly generated result.

### Make the code readable

* Explain the purpose, inputs, outputs, and how to run the script in comments.
* Indent continuation lines consistently.
* Keep the steps in the same order as the pipeline you tested.

A line ending in `|` tells Bash that the pipeline continues on the next line. No backslash is needed after that pipe. Elsewhere, a final `\` can continue a command onto the next line; it must be the last character, with no trailing spaces.

The first line, `#!/usr/bin/env bash`, is the **shebang**. It tells the system to use Bash when you execute the file directly.

You can also edit the file with Notepad++ or BBEdit if you are comfortable opening the file in your clone. Save as plain text with Unix (LF) line endings. `nano` provides a consistent starting point on both operating systems.

</details>

<details><summary>Accept input and output paths as arguments</summary>

The first version always reads and writes the same paths. Arguments let us supply those paths when we run it.

Open the script again:

```bash
nano ExtractBodyM.sh
```

Replace its contents with:

```bash
#!/usr/bin/env bash
# Extract taxonomy and adult body mass from a Pacifici-format table.
# Input: semicolon-delimited table with a header and the original columns.
# Output: Order, Family, Genus, Scientific_name, AdultBodyMass_g;
#         tab-separated, without a header, sorted by decreasing mass.
# Usage: bash ExtractBodyM.sh INPUT_FILE OUTPUT_FILE
# Use different paths for input and output. The output is overwritten.

cut -d ';' -f 2-6 "$1" |
    tail -n +2 |
    sort -t ';' -k5,5nr |
    tr ';' '\t' > "$2"
```

Save and exit, then run:

```bash
bash ExtractBodyM.sh ../data/Pacifici2013_data.csv BodyMass.tsv
```

| Part | Meaning |
| --- | --- |
| `bash` | Program that interprets the script |
| `ExtractBodyM.sh` | Script to run |
| `../data/Pacifici2013_data.csv` | First argument, available inside the script as `$1` |
| `BodyMass.tsv` | Second argument, available inside the script as `$2` |

The double quotes in `"$1"` and `"$2"` keep each supplied path together, including any spaces. This introductory script assumes two valid paths and a table with the expected columns. It does not check them for you yet.

### Check your understanding

```bash
bash ExtractBodyM.sh ../data/Pacifici2013_data.csv BodyMass_check.tsv
cmp BodyMass.tsv BodyMass_check.tsv
```

`cmp` compares the files. No output means their contents match. An error message about a missing file means the comparison could not run.

The script path and its input/output paths are relative to the terminal's **current working directory**, not automatically relative to where the script is stored.

### Make the script executable

```bash
chmod u+x ExtractBodyM.sh
./ExtractBodyM.sh ../data/Pacifici2013_data.csv BodyMass.tsv
```

`./` tells the shell to run the script in the current directory. You can still run it with `bash ExtractBodyM.sh ...` without adding execute permission.

</details>

<details><summary>Use variables and command substitution</summary>

A variable holds a value that you can use later:

```bash
species="Gorilla gorilla"
echo "$species"
grep "$species" BodyMass.tsv
```

There are no spaces around `=` when assigning a value. Use `$` when retrieving the value, not when assigning it.

For your own variable names, use letters, digits, and underscores; start with a letter or underscore. Dots are not allowed. Use descriptive names such as `species` and `sequence_count`.

### Save a command's output in a variable

The syntax `$(command)` is called **command substitution**: run the command and substitute its output.

```bash
sequence_count=$(grep -c '^>' ../data/miRNA/hsa_miR.fasta)
echo "$sequence_count"
```

In the quoted `grep` pattern, `^` means the beginning of a line, so `'^>'` matches FASTA headers. Each header starts a sequence record. The `>` inside quotes is part of the search pattern, not output redirection.

Why is counting headers more reliable than dividing a FASTA file's line count by two? Sequence lines can wrap across multiple lines.

</details>

<details><summary>Repeat a task with a for loop</summary>

### Start with two files

```bash
cd ~/lecture-2/CSB/unix/sandbox

for file in ../data/miRNA/ggo_miR.fasta ../data/miRNA/hsa_miR.fasta
do
    echo "$file"
    head -n 2 "$file"
done
```

| Part | Meaning |
| --- | --- |
| `for file in ...` | Assign each listed path to `file`, one at a time |
| `do` | Begin the commands to repeat |
| `"$file"` | Use the path for the current iteration |
| `done` | Finish this iteration and move to the next path |

When entering a loop interactively, Bash may show a `>` continuation prompt. Do not type that prompt. Use **Ctrl+C** if you need to cancel an incomplete command.

### Expand to all supplied FASTA files

```bash
for file in ../data/miRNA/*.fasta
do
    echo "$file"
    grep -c '^>' "$file"
done
```

The glob supplies the list of filenames; the loop repeats the same commands for each file. A filename containing a written list does not automatically expand into that list.

### Save a tidy summary table

Create a second script:

```bash
nano CountSequences.sh
```

Put the following code in the editor:

```bash
#!/usr/bin/env bash
# Count sequence records in the supplied microRNA FASTA files.
# Run from CSB/unix/sandbox: bash CountSequences.sh
# Output: sequence_counts.tsv, one row per input file, with a header.

printf 'file\tsequence_count\n' > sequence_counts.tsv

for file in ../data/miRNA/*.fasta
do
    sequence_count=$(grep -c '^>' "$file")
    printf '%s\t%s\n' "$file" "$sequence_count" >> sequence_counts.tsv
done
```

Save and exit, then run:

```bash
bash CountSequences.sh
cat sequence_counts.tsv
```

`printf` uses a format string: `%s` inserts a value, `\t` inserts a tab, and `\n` starts a new line. The first `printf` replaces any previous output and writes the header. The loop appends one row per file.

There should be **six data rows plus one header row**. Run the script again and confirm that it still has seven lines:

```bash
bash CountSequences.sh
wc -l sequence_counts.tsv
```

Why would using `>>` for the header be a problem when running this script again?

Keep generated files in the sandbox so that input globs such as `../data/miRNA/*.fasta` continue to select only the supplied data.

</details>

<details><summary>Extension: extract selected microRNA records</summary>

The original lecture used `grep -A 1` to extract a header and the following sequence line. This works only for FASTA files with one sequence line per record, as in these supplied files.

```bash
cd ~/lecture-2/CSB/unix/sandbox

for mirna in miR-208a miR-564 miR-3170
do
    grep -h -A 1 -w "$mirna" ../data/miRNA/*.fasta | grep -v '^--$' > "$mirna.fasta"
done
```

`-h` suppresses filename prefixes when searching multiple files. The second `grep` removes separator lines introduced between context groups. Both steps are needed to keep the output in FASTA format. Output files remain separate from the input directory.

This searches for the supplied name as a word within each header; it is not a general FASTA parser or an exact biological identifier lookup. Inspect the headers and sequences. For wrapped sequences or more complex extraction, use a sequence-aware tool rather than relying on `-A 1`.

</details>

---

## Save Your Lecture Work to GitHub

Keep short notes about commands you found useful, errors you resolved, and questions you still have:

```bash
cd ~/lecture-2/CSB/unix/sandbox
nano lecture02_notes.md
```

Before finishing, check for these files in your sandbox:

| File | Contents |
| --- | --- |
| `ExtractBodyM.sh` | Documented script accepting input/output paths |
| `BodyMass.tsv` | Sorted body-mass table |
| `CountSequences.sh` | Loop that counts FASTA records |
| `sequence_counts.tsv` | One row per FASTA input file |
| `lecture02_notes.md` | Your notes and answers to the in-class questions |

Use the same Git workflow as Lecture 1 and Assignment 1:

```bash
cd ~/lecture-2
git status
git add --all
git status
git commit -m "Complete Lecture 2 pipelines and scripts"
git push
```

Refresh **your Lecture 2 repository** on GitHub and open the sandbox to verify the files arrived. A commit saves your changes locally; a push sends those commits to GitHub. Complete any linked quiz or exercise forms separately.

---

## Quick Reference

<details><summary>Commands, paths, and troubleshooting</summary>

| Command or syntax | Purpose |
| --- | --- |
| `pwd`, `ls`, `cd` | Check location, inspect files, change directories |
| `.`, `..`, `~` | Current directory, parent directory, home directory |
| `head`, `tail` | Inspect the beginning/end of a file or select lines |
| `cut`, `tr` | Select fields; translate characters |
| `sort`, `uniq -c` | Sort lines; count adjacent identical lines |
| `grep`, `find` | Search text; find files/directories |
| `bash script.sh` | Run a Bash script |
| `chmod u+x script.sh` | Add execute permission for the owner |
| `name=value`, `"$name"` | Assign and retrieve a variable |
| `$(command)` | Capture a command's output |
| `man command` | Read the command manual; press `q` to exit |

If you see **No such file or directory**, run `pwd` and `ls`, then check the path and capitalization. Return to `~/lecture-2/CSB/unix/sandbox` for processing examples.

If you see **Permission denied** when running a script directly, inspect `ls -l` and use `chmod u+x` for your script, or run it with `bash`.

If you see **nothing to commit**, inspect the files and confirm that you are in the correct repository. Your changes may already be committed; check GitHub after pushing.

### PATH and line endings

`PATH` lists the directories the shell searches for commands:

```bash
echo "$PATH"
command -v bash
```

You do not need to change `PATH` for this lecture; use `bash script.sh` or `./script.sh`.

Unix text files normally end lines with LF. Windows editors can use CRLF. Save Bash scripts with Unix (LF) line endings; stray CR characters can produce errors such as `bash\r: No such file or directory`.

</details>
