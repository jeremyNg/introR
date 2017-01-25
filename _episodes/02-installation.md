---
title: "Installation of R"
teaching: 5
exercises: 0
questions:
- "Installing R and R studio."
- "Basics of R." 
objectives:
- "Be able to install R and R-studio on a Linux system." 
---

## Installing R
(* This section is for your information only; R and R-studio has already been installed on the computers in the laboratory*). 

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

## A note on versions
It is important to note that sometimes, the version of R available on the repository is behind (that is, older than) the current version of R. In this case, one can simply update the list of repositories so that the package manager will download from the R site (which contains the latest version) instead of getting from *apt* only. This can be done by editing the file */etc/apt/sources.list*, a text file that contains the list of all repositories *apt* will search. The following line needs to be inserted into the sources list:
~~~
deb http://cran.rstudio.com/bin/linux/ubuntu xenial/
~~~
{: bash}  

Once this is done, you will need to update *apt* by using the command, as well as allow *apt* to download from the new source. This is done using the following commands: 
~~~
gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9 
gpg -a --export E084DAB9 | sudo apt-key add 
sudo apt-get update
~~~
{: bash} 
Thereafter, the previous instructions to install R applies. 


