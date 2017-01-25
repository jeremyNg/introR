---
title: "Assignments and data types in R"
teaching: 5
exercises: 0
questions:
- "What are variables and why use them?" 
- "How do we assign values to variables?"
- "What are the different data types?" 
objectives:
- "Understand what are variables and how are values assigned to variables."
- "Know the different data types in R." 
---
## Variables: What and why
The concept of variables is found in all programming languages. For example, the following example shows a variable that is assigned the value of 5: 

~~~
x=5
print(x) 
~~~
{: R} 

~~~
[1] 5
~~~
{: output}

Thereafter, we can constantly use *x* instead of 5 throughout our script. 

> Variables are used to store information to be referenced and  manipulated in a computer program. They also provide a way of labeling data with a descriptive name, so our programs can be understood more clearly by the reader and ourselves. It is helpful to think of variables as containers that hold information. Their sole purpose is to label and store data in memory. This data can then be used throughout your program. (Taken from https://launchschool.com/books/ruby/read/variables)

Variables are used because they can be manipulated easily throughout our program. For example: 

~~~
## finding the average of N people
N=10
total=100
average=total/N 
~~~
{: R}

## Assigning values ot variables 
