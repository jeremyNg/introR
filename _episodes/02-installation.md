---
title: "Installation of R"
teaching: 5
exercises: 0
questions:
- "How do I install R and R studio?"
- "How do I install other packages in R?"
objectives:
- "Be able to install R and R-studio on a Linux system." 
- "Be familiar with installing packages in R, including BioConductor packages." 
keypoints: 
- "R can be installed via the Linux package managers." 
- "Rstudio is a powerful interface for R programming."
- "Like Linux, R has a system for downloading and installing packages from the R package repositories."
- "CRAN is the main repository for R packages, while BioConductor is the main repository for bioinformatics related packages." 
- "The *library* command allows one to load an installed package in the current R session." 
---

## Installing R
(*This section is for your information only; R and R-studio has already been installed on the computers in the laboratory*). 

Like other packages, R can be installed using a package manager. In Ubuntu, this can be done using the following command: 

~~~ 
sudo apt-get install r-base-core
~~~
{: bash} 

Although R comes with a graphic user interface, this interface contains only the R interpreter (similar to Terminal). Instead, we will use a more powerful interface, *R-studio*. On top of being able to interpret R commands, it also contains a code editor where one can write scripts prior to execution and a plotting area where one can see the graphic output. Installing R-studio is slightly more complex because it is not available on the package repository. Instead, we will need to download the source codes and compile it. This can be done as follows: 

~~~
wget https://download1.rstudio.org/rstudio-0.99.896-amd64.deb
gdebi -n rstudio-0.99.896-amd64.deb
rm rstudio-0.99.896-amd64.deb
~~~ 
{: bash} 

The first line (*wget*) fetches the package from the source (https://download1.rstudio.org/). Thereafter, the package is installed and then the downloaded file is removed (*rm*). 

Once installed, you can start R-studio by clicking on the R-studio icon in the **Applications** list. 

> ## A note on versions
> It is important to note that sometimes, the version of R available on the repository is behind (that is, older than) the current version of R. In this case, one can simply update the list of repositories so that the package manager will download from the R site (which contains the latest version) instead of getting from *apt* only. This can be done by editing the file */etc/apt/sources.list*, a text file that contains the list of all repositories *apt* will search. The following line needs to be inserted into the sources list for an Ubuntu system:

~~~
>deb http://cran.rstudio.com/bin/linux/ubuntu xenial/
~~~
> Once this is done, you will need to update *apt* by using the command, as well as allow *apt* to download from the new source. This is done using the following commands: 
~~~
gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9 
gpg -a --export E084DAB9 | sudo apt-key add 
sudo apt-get update
~~~
{: bash} 
> Thereafter, the previous instructions to install R applies. 

## Installing packages in R 
Likewise, one can install R packages from software repositories. The main repository where R packages are submitted to is **CRAN** (The Comprehensive R Archive Network). However, CRAN is by no means the only repository -- increasingly, people are also hosting packages on *Github*, and there are other more specialized repository as well. For this present purpose, we will focus on installation of packages from 2 repositories -- CRAN, and BioConductor, the latter of which is the main repository for bioinformatics software packages. 

### Installing packages from CRAN 
Installing packages from CRAN is relatively straightforward, and can be achieved with a single command: 

~~~
install.packages("package of interest")
~~~
{: R}

It is important to realize the name of the package is (1) case sensitive, and (2) placed within quotes. The reason for the latter is because if there is no quotes placed around the name, R will assume that you are referring to a variable (next chapter), which might not exist because you did not create it yet or because the value of the variable is an invalid package. 

### Installing BioConductor packages 
Installing BioConductor packages 

> ## Default packages installed with BiocLite
>
> Although the *biocLite* command requires us to specify the packages we wish to install from BioConductor, we can run biocLite without specifying any arguments. In this case, biocLite installs a set of default packages. Can you find out which are the packages that were installed by default? 
>
> *Hint: check out what packages have been installed using the command installed.packages()* 
{: .challenge}

## Loading packages 

~~~
library("package") 
~~~ 

One can check what packages are loaded using the following command: 

~~~
sessionInfo()
~~~ 
{: R}

The sessionInfo command not only tells us what package is loaded, but also what the version numbers of each package is (which is really useful when you run into problems and want to ask for help on the various forums, as some of the problems reported might have been fixed in later versions of the package).
