# Lecture 5 Environment

## Environments for Higher-Order Functions

### Environments Enable Higher-Order Functions

**Functions are first-class**: Functions are values in our programming language.

**Higher-order function**: A function that takes a function as an argument value or A function that returns a function as a return value

### Names As Function Arguments

<img src="https://s2.loli.net/2022/12/13/QvRr9Z2THtOSdUF.jpg" alt="Snipaste_2022-12-13_19-48-43.jpg" style="zoom:67%;" />

## Environments for Nested Definitions

<img src="https://s2.loli.net/2022/12/13/8TJ2cZrhqsd5waj.jpg" alt="屏幕截图 2022-12-13 195158.jpg" style="zoom: 57%;" />

-   Every user-defined function has a parent frame (often global)
-   The parent of a function is the frame in which it was defined
-   Every local frame has a parent frame (often global)
-   The parent of a frame is the parent of the function called

### How to Draw an Environment Diagram

**When a function is defined:** 

Create a function value: `func <name>(<formal parameters>) [parent=<label>]`

Its parent is the current frame.

<img src="https://s2.loli.net/2022/12/13/GeVWS7U3fQJa4gw.jpg" alt="Snipaste_2022-12-13_19-56-50.jpg" style="zoom:67%;" />

Bind `<name>` to the function value in the current frame.

**When a function is called:**

1.   Add a local frame, titled with the `<name>` of the function being called.
2.   **Copy the parent of the function to the local frame: `[parent]=<label>`**
3.   Bind the `<formal parameters>` to the arguments in the local frame.
4.   Execute the body of the function in the environment that starts with the local frame

## Local Names

### Local Names' Visibility

Local Names are not visible to other(non-nested) functions

-   An environment is a sequence of frames.
-   The environment created by calling a top-level function (no def within def) consists of on local frame, followed by the global frame.

## Lambda Expressions

### Lambda Expressions

<img src="https://s2.loli.net/2022/12/13/kt8HrOSxsCaKABv.jpg" alt="Snipaste_2022-12-13_20-04-50.jpg" style="zoom:67%;" />

Lambda expressions are not common in Python, but important in generall

Lambda expressions in Python cannot contain statements at all

### Lambda Expressions and Def Statements

-   Both create a function with the same domain, range, and behavior. 
-   Both bind that function to the name square. 
-   Only the def statement gives the function an intrinsic name, which shows up in environment diagrams but doesn't affect execution (unless the function is printed).

## Currying

### Function Currying

Function Currying  is that transform a **multi-argument** function into a **single-argument**, higher-order function

```python
>>> from operator import add
>>> def make_adder(n):
...     return lambda k: k + n
...
>>> make_adder(2)(3)
5
>>> add(2, 3)
5
```

