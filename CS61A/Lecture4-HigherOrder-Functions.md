# Lecture 4 Higher-Order Functions

## Designing Functions

### Characteristics of Functions

A function's domain is the set of all the inputs it might take as arguments

A function's range is the set of output values it might return

A pure function's behaviour is the relationship it creates between input and output

### A Guide to Design Functions

-   Give each function a exact job
-   Do not Repeat Yourselft. Implement a process once, but execute many times
-   Define functions generally

## Higher-Order Functions

### Generalizing Over Computational Processes

The common structure among functions may be a **computational process, rather than a number** .

## Function as Return Values

### Locally Defined Functions

Functions defined within other function bodies are bound to names in a local frame.

![Snipaste_2022-12-13_12-45-59.jpg](https://s2.loli.net/2022/12/13/hYDlLavnIpkJOeB.jpg)

### Call Expressions as Operator Expressions

![Snipaste_2022-12-13_12-47-03.jpg](https://s2.loli.net/2022/12/13/k5R9cYLslXWaqCz.jpg)

### The purpose of Higher-Order Function

**Functions are first-class:** Functions can be manipulated as values in our programming language.

**Higher-order function:** A function that takes a function as an argument value or returns a function as a return value

The feature of Higher-order functions:

-   Express general methods of computation
-   Remove repetition from programs
-   Separate concerns among functions

