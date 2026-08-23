# Computer Setup Checklist

Complete the setup appropriate for the current section of the course before starting an assignment or lecture. Detailed installation instructions are maintained in the [Computational Biology `how_to` repository](https://github.com/tamucc-comp-bio/how_to).

## Unix and Git

- [ ] Complete the [computer setup guide](https://github.com/tamucc-comp-bio/how_to/blob/main/howto_setup_computer.md), including the GitHub and SSH-key steps.
- [ ] Open a terminal. On Windows, use Ubuntu in Windows Terminal.
- [ ] Ubuntu users (not Mac) should update their ubuntu packages

  ```bash
  sudo apt update
  sudo apt upgrade
  ```
  
- [ ] Confirm that Git is available:

  ```bash
  git --version
  ```

  If you don't have git, then:

  ```bash
  #mac users, install git with this command
  brew install git

  #ubuntu users, install git with this command
  sudo apt install git
  ```
  
- [ ] Configure your github account locally

  ```bash
  git config --global user.name "First Last"
  git config --global user.email "EMAIL_ASSOCIATED_WITH_GITHUB"
  ```

- [ ] Confirm that the CSB repository is in your home directory:

  ```bash
  ls ~/CSB
  ```

  If it is missing, clone it once:

  ```bash
  cd ~
  git clone git@github.com:tamucc-comp-bio/CSB.git
  ```

## R

Before the R section, complete the R and RStudio steps in the [computer setup guide](https://github.com/tamucc-comp-bio/how_to/blob/main/howto_setup_computer.md). Confirm that `R --version` works in your terminal and that RStudio opens.

## Python

Before the Python section, complete the Conda step in the [computer setup guide](https://github.com/tamucc-comp-bio/how_to/blob/main/howto_setup_computer.md). Confirm that `conda --version` works in your terminal.

## ChromeOS, iOS, and Android

Use a browser-based environment instead of installing the desktop tools:

- [GitHub Codespaces setup](https://github.com/tamucc-comp-bio/how_to/blob/main/howto_github_codespaces.md)
- [Launch HPC access instructions](https://hprc.tamu.edu/kb/User-Guides/Launch/Access/)

