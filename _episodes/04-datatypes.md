---
title: "Data types in R"
teaching: 5
exercises: 0
questions: 
- "How is data represented in R?"
objectives: 
- "Recognize the different data types in R."
- "Be able to index and subset different classes of data in R." 
---
## Representing data in R
As with programming languages like C, there are different representations of data in R. The main types (classes) of data will be discussed in the below section.
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
 

 > as.integer("TRUE")
[1] NA
Warning message:
NAs introduced by coercion 


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

## Data types in R 

## Vectors

## Lists

## Matrix

## Data frame 