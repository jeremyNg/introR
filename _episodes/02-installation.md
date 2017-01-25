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
- "The installed.packages command allows us to view what packages have been installed on our system, while the sessionInfo commands allows us to view what packages have been loaded in the current session of R."
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
Installing BioConductor packages requires that you first download the BioConductor installer, which provides an interface to install other BioConductor packages. This is done using the following command:

~~~
source(http://bioconductor.org/biocLite.R)
~~~
{: R}

Once the Bioconductor installer package is installed, you will need to load the library. Loading of packages in R is done using the following: 

~~~
library("library to be loaded)
~~~
{: R}

In the above case, we will do the following: 

~~~
library(BiocInstaller)
~~~
{: R}
This will load the BiocInstaller package, which then allows us to access the functions contained within the package. Thereafter, we will use the biocLite command to install the packages we want to install, as shown below: 

~~~
biocLite("packages to be installed")
~~~

The above command will install packages that are found in the BioConductor repository. Occassionally, you will also be prompted to update your older packages -- this is usually recommended as packages are constantly being updated to fix newly discovered bugs or improve performance. 

> ## Default packages installed with BiocLite
>
> Although the *biocLite* command requires us to specify the packages we wish to install from BioConductor, we can run biocLite without specifying any arguments. In this case, biocLite installs a set of default packages. Can you find out which are the packages that were installed by default? 
>
> *Hint: check out what packages have been installed using the command installed.packages()* 
{: .challenge}

## Loading packages 
As alluded to earlier, packages are loaded using the *library* command, as follows: 

~~~
library("package") 
~~~ 
{: R}
Importantly, packages are loaded only in the current session of R. That is, if another instance of R is started or the current session of R is restarted, these packages will no longer be loaded and will need to be re-loaded again. 

One can check what packages are loaded using the following command: 

~~~
sessionInfo()
~~~ 
{: R}

An example of a *sessionInfo* output looks like this: 

~~~
R version 3.3.2 (2016-10-31)
Platform: x86_64-apple-darwin13.4.0 (64-bit)
Running under: OS X El Capitan 10.11.6

locale:
[1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
[1] ggplot2_2.2.0

loaded via a namespace (and not attached):
 [1] colorspace_1.3-2 scales_0.4.1     assertthat_0.1   lazyeval_0.2.0  
 [5] plyr_1.8.4       tools_3.3.2      gtable_0.2.0     tibble_1.2      
 [9] Rcpp_0.12.8      grid_3.3.2       munsell_0.4.3  
~~~
{: output}

> ## Attached packages vs packages loaded via namespace
>
> From the output above, you can see that I have loaded the ggplot2 package, which is a package used extensively for data visualization. This information is found in the *other attached packages* section. However, you will also notice that there are a whole bunch of packages that are listed in the *loaded via a namespace (and not attached)* section. These are packages that are suggested by ggplot2. Unlike the functions in ggplot2 however, the functions in these packages cannot be directly accessed by me because the packages are not explicitly loaded. 

The sessionInfo command not only tells us what package is loaded, but also what the version numbers of each package is. The latter information is really useful when you run into problems and want to ask for help on the various forums, as some of the problems reported might have been fixed in later versions of the package.
