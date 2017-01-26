---
title: "Data types in R"
teaching: 5
exercises: 0
questions: 
- "How is data represented in R?"
- "How do we extract specific entries in R?"
objectives: 
- "Recognize the different data types in R."
- "Be able to index and subset different classes of data in R." 
keypoints: 
- "Both data frame and matrix are two dimensional objects with rows and columns. "
- "Data frames can have different modes of data for different columns, while all the entries in the matrix must be of the same mode."
- "Class conversion can be done with *as.* *. However, not all conversions can occur and if unsuccessful, will return a warning message." 
- "Subsetting can be done with [] in R, with 1 being the first entry." 
---
## Data classes in R

## Vectors
Vectors are the simplest one dimensional representation of data in R. They can be made of the following types (mode) of data, including a mix of these data types. Likewise, computations involving vectors is one of the fastest in R and hence strongly encouraged (known as *vectorization*).  

### Characters 

### Numeric and integers
The **numeric** class is the most commonly encountered data class in R. Unlike **integer**, decimals can be represented in this class of object. For example: 

~~~
>x<-3.14
>class(x)
[1] "numeric"
~~~

On the other hand, the when one tries to convert between a numeric and an integer (which cannot represent decimals), the decimal is stripped and the number is always **rounded down**. For example:

~~~
> as.integer(3.6)
[1] 3
~~~
 {: R}
 

This behavior is extremely important to bear in mind, as it defies common mathematics (which will have yielded 4 because 3.6 should have been rounded up instead). 

 > ## Converting between classes 
 >
 > Where possible, one can convert between different classes of data using the *as.* * function. For example, in the above snippet, we were able to convert a numeric value (3.14) to an integer using *as.integer*. R will try to convert the class accordingly, but where it cannot do so, will return you **NA** with a warning message. For example:
 
~~~
 > as.integer("TRUE")
[1] NA
Warning message:
NAs introduced by coercion 
~~~
{: R}

> This conversion cannot be done because TRUE cannot be represented as a number. Instead, R will convert it to NA.

> ## Errors and warnings in R
>
> Two types of messages will be encountered in R: error messages and warning messages. Although both  occurs when there is something wrong about the code you are running, they have slightly different behaviors. Errors will terminate the code (that is, the code will not be evaluated at all), while warnings will not. Hence, it is important to always check for the output of scripts that were completed with warnings, as the script might not have done what you had intended for it in the first place. 
{: popout}

### Logical 
**Logical** data can only take on TRUE or FALSE values, and are commonly encountered when we test if a certain condition is fulfilled. For example: 

~~~
> 5>4
[1] TRUE

> class(5>4)
[1] "logical"
~~~
{: R}

Although the test returns a value of TRUE, this TRUE is not in fact a character object but a logical object. 

## Lists

## Matrix
A matrix is a two-dimension object that has rows and columns. One important specification is that all the entries in the matrix must be of the same mode -- that is, either numeric, integer, logical or character. If there are more than one mode present, R will simply convert everything to **character**. 
A matrix can be created with the *matrix* command, which has the general usage as shown:

~~~
Usage:

     matrix(data = NA, nrow = 1, ncol = 1, byrow = FALSE,
            dimnames = NULL)

~~~
{: output}
 
The *nrow* and *ncol* specifies the number of rows and columns respectively, while the *byrow* argument indicates if the matrix will be filled row-wise or column wise. The behavior of the byrow argument can be seen below: 

~~~
> matrix(1:20, nrow=2, ncol=10, byrow=TRUE)
     [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10]
[1,]    1    2    3    4    5    6    7    8    9    10
[2,]   11   12   13   14   15   16   17   18   19    20

> matrix(1:20, nrow=2, ncol=10, byrow=FALSE)
     [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10]
[1,]    1    3    5    7    9   11   13   15   17    19
[2,]    2    4    6    8   10   12   14   16   18    20
~~~
{: R}

## Data frame 
Similar to a matrix, a data frame has both row and columns. However, it is more general than a matrix, and allows for different columns to have different types of data. This makes the data frame one of the most versatile data types in R, and one of the most widely-used data types as well. 
One can create a data frame using the *data.frame* command, which has the usage

~~~
Usage:

     data.frame(..., row.names = NULL, check.rows = FALSE,
                check.names = TRUE, fix.empty.names = TRUE,
                stringsAsFactors = default.stringsAsFactors())

~~~
{: output} 

For example, the following can be used to construct a data frame where we explicitly gave row names and column names to both rows and columns. 

~~~
> data.frame(Gender=c("male","female"),
		       Count=c(10,5), 
		       row.names=c("M","F"))
  Gender Count
M   male    10
F female     5
~~~ 
{: output}

## Subsetting in R 
Subsetting is an important capability of any programming language. That is, how can we extract specific entries from a vector, list, matrix or dataframe? 
