---
title: "Variables and assignments in R"
teaching: 5
exercises: 0
questions:
- "What are variables and why use them?" 
- "How do we assign values to variables?" 
objectives:
- "Understand what are variables and how are values assigned to variables."
- "Differentiate global and local variables, and understand how to assign a variable within a function as a global variable." 
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

There are two huge advantages in using variables: 
1.  Not having to 'hard-code' any value in our scripts. This is especially important when a single variable is referenced more than once in the script -- in that case, we only need to change the initial value assigned to the variable instead of changing the value everywhere in the script.
2. Legibility. With good variable names, the script becomes more legible as it is apparent to other readers what is being done/evaluated at each step of the script. 

> ##Variable names in R
>
> There are a few rules that needs to be observed when naming variables, namely:
>1. Variable names may not start with a number.
>2. Variable names cannot contain mathematical symbols such as "+", "-","*", "/".
>3. Variable names are case-sensitive.
>4. Variable names that start with "." are hidden in the global environment (more on environments later)

## Assigning values to variables
Assignment can be done using either '=' or '<-'. For example: 

~~~
x=5
x<-5
~~~
{: R}

In both cases, the variable *x* will be assigned the value of 5. Stylistically, we use '<-' in R for assignment so as to avoid confusion with '==', which is used to test for the equality of 2 objects. 

Variables do not necessarily have to be values. In fact, they can be anything. For example, the following variable *average* is a function that calculates the average for a vector of numbers (more on that in the next section). 

~~~
numbers <-c(10,20,30,40,50,60,70,80)
average<-function(x){
	return(sum(x)/length(x))
}
result<-average(numbers)
result
~~~
{: R}

Executing the above script will yield the following: 

~~~
[1] 45
~~~
{: R}

In the above snippet, we did the following: 
1. Created a variable *numbers*, which was a vector of numbers
2. Created a variable *average*, which is a function that calculates the average of a vector of numbers
3. Assigned the result of passing *numbers* through our function *average* to a new variable *result*


## Types of variables: Local vs. global variables 

## Variables in R are mutable

