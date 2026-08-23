# Installing R Studio

It is important that you keep R Studio up to date on your computer.  If you do not, you will start to run into compatibility issues.  Also note that there are many versions of RStudio.  We are going to use "RStudio Desktop Open Source Edition".  It is free.

_Note: you will not be installing R Studio on Ubuntu. If you have a Windows computer, you'll be working in windows._

<details><summary>Install `R`</summary>
<p>

[You can find R install instructions here](../resources/install_r.md). If you have a windows computer, you will need to separately install `R` in the windows environment even if you already installed it in Ubuntu. 

---
</p>
</details>

<details><summary>Install `R Studio` on Ubuntu</summary>
Regardless of your operating system, if you have not already installed R studio, you need to do that now.  
  
For those with windows computers, you can install R studio in Windows and/or Ubuntu.  If you are "afraid" to change your R and R studio, then install R Studio in Ubuntu.  If you followed the [instructions on setting up Ubuntu](install_wsl_ubuntu.md), it should work.

*If you installed R Studio a while ago, you should do it again to upate to the latest version.*

1. Update Ubuntu Apps
   
Before you can install RStudio, you need to have R installed on your machine. If you don't have R installed yet, you can install it by opening a terminal and typing the following commands:

```bash
sudo apt update
sudo apt upgrade
```

2. Download R Studio

Next, download the RStudio `.deb` package from the [RStudio website](https://posit.co/download/rstudio-desktop/). You can do this with the wget command along with the URL of the RStudio .deb package. Make sure to replace the URL with the latest version available from the RStudio website.

```bash
cd ~/Downloads
wget https://download1.rstudio.org/electron/jammy/amd64/rstudio-2023.09.0-463-amd64.deb
```

3. Install R Studio

Once the download is complete, you can install RStudio with the dpkg command.

```bash
sudo dpkg -i rstudio-2023.09.0-463-amd64.deb
```

4. Resolve Dependencies (if any):

If dpkg reports any missing dependencies, you can install them with the apt command.

```bash
sudo apt-get install -f
```


5. Launch RStudio:
Now that RStudio is installed, you can launch it from the terminal by typing:

```bash
rstudio
```

Make sure you install "RStudio Desktop Open Source Edition".  

---
</p>
</details>

<details><summary>Install `R Studio` on Windows or Mac</summary>
Regardless of your operating system, if you have not already installed R studio, you need to do that now.  
  
For those with windows computers, you can install R studio in Windows and/or Ubuntu.  If you are "afraid" to change your R and R studio, then install R Studio in Ubuntu.  If you followed the instructions on setting up Ubuntu, it should work.



*If you installed R Studio a while ago, you should do it again to upate to the latest version.*

[RStudio Install](https://www.rstudio.com/products/rstudio/download/)

Make sure you install "RStudio Desktop Open Source Edition".  An install package will be downloaded to your computer and then you double click that file to install.

---
</p>
</details>

<details><summary>Clone CSB Repo to Your Windows Home Dir (Win Only)</summary>

Just to make things a little more tricky, if you have windows, it is not easy to access the `CSB` repo that you cloned to your home directory in Ubuntu from RStudio. So, we have to clone the repo again, but this time to the `Downloads` dir inside your windows home dir.

Open your ubuntu terminal and navigate to your windows `Downloads` directory, then clone the CSB repo to there.

```bash
# make sure you are in ubuntu
cd /mnt/c/Users/YourWinUserName/Downloads
git clone git@github.com:tamucc-comp-bio/CSB.git
```

---
</p>
</details>


