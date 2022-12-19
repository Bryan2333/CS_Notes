# Lecture 3 Control

## Print and None

### None Value

None Indicates that Nothing is returned

The special value **None** represents nothing in Python

A function that does noe explicitly return a value will return **None**

*Careful:* **None** is not displayed by the interpreter as the value of an expression

```python
>>> def does_not_square(x):
...     x * x
...
>>> does_not_square(5) # Nothing print here
>>> print(does_not_square(5)) # print none to the console
None
```

### Pure/Non-Pure Function

**Pure Functions** just return values

**None-Pure Functions** have side effects

<img src="https://s2.loli.net/2022/11/24/l8DjYisgJTBcr67.jpg" alt="屏幕截图 2022-11-24 144437.jpg" style="zoom:50%;" />

<img src="https://s2.loli.net/2022/11/24/UPcNVEMTlJCrBIo.jpg" alt="屏幕截图 2022-11-24 155536.jpg" style="zoom: 50%;" />

## Multiple Environments

### Life Cycle of a User-Defined Function

<img src="https://s2.loli.net/2022/11/24/TzbwIaSYdsXGZfh.jpg" alt="屏幕截图 2022-11-24 155935.jpg" style="zoom: 45%;" />

### Multiple Environments in one Diagram

<img src="https://s2.loli.net/2022/11/24/Lzjx9iPtMSRFqQ2.jpg" alt="屏幕截图 2022-11-24 160122.jpg" style="zoom:45%;" />

### Names Have no meaning Without Environment

<img src="https://s2.loli.net/2022/11/24/lyEqkbsxHYM2XjB.jpg" alt="屏幕截图 2022-11-24 160233.jpg" style="zoom:45%;" />

## Miscellaneous Python Features

### Division

there are two types of division in Python: **true divsion** and **floor division**

The true division will return the value with fractional part while floor division will not

**Example**

```python
>>> from operator import truediv, floordiv
>>> truediv(2022, 10)
202.2
>>> floordiv(2022, 10)
202
```

### Multiple Return Values

It is possible for a function to return multiple values in Python

And You can use a single assignment statement with multiple names on the left of $=$ to receive the values

**Example**

```python
>>> from operator import truediv, floordiv, mod
>>> def divide_exact(x,y):
...     return floordiv(x,y), mod(x,y)
...
>>> quotient, remainder = divide_exact(2022, 10)
>>> quotient
202
>>> remainder
2
```

### Doctests

**Docstrings** in Python are used not only for the description of a class or a function to provide a better understanding of the code and use but, also used for Testing purposes.

The **Doctest Module** finds patterns in the docstring that looks like interactive shell commands.

**Example**

```python
>>> def divide_exact(x,y):
...     """Return the quotient and remainder of dividing x by y
...     >>> quotient, remainder = divide_exact(2022, 2)
...     >>> quotient
...     202
...     >>> remainder
...     2
...     """
...     return floordiv(x,y), mod(x,y)
...
>>> from doctest import testmod
>>> if __name__ == '__main__':
...     testmod(name = 'divide_exact', verbose = True)
...
Trying:
    quotient, remainder = divide_exact(2022,10)
Expecting nothing
ok
Trying:
    quotient
Expecting:
    202
ok
Trying:
    remainder
Expecting:
    2
ok
1 items had no tests:
    divide_exact
1 items passed all tests:
   3 tests in divide_exact.divide_exact
3 tests in 2 items.
3 passed and 0 failed.
Test passed.
TestResults(failed=0, attempted=3)
>>>
```

### Default Arguments

In Python, we can provide default values for the arguments of a function. 

When calling that function, arguments with default values are optional. 

If they are not provided, then the default value is bound to the formal parameter name instead.

**Example**

```python
>>> def square(x=2):
...     return x*x
...
>>> square()
4
```

## Conditional Statements

### Statements

A statement is executed by the interpreter to perform an action

<img src="https://s2.loli.net/2022/11/24/8aBCONrzRuw4Djp.jpg" alt="屏幕截图 2022-11-24 163813.jpg" style="zoom:50%;" />

-   The first header determines a statement's type
-   The header of a clause "controls" the suite that follows
-   `def` statements are compound statements

### Compound Statements

A suite is a sequence of statements

To “execute” a suite means to execute its sequence of statements, in order

**Execution Rule for a sequence of statements:**

1.   Execute the first statement
2.   Unless directed, otherwise execute the rest

### Condition Statements

<img src="https://s2.loli.net/2022/11/24/d2fhiEycODxSI1F.jpg" alt="屏幕截图 2022-11-24 164117.jpg" style="zoom:45%;" />

**Execution Rule for Conditional Statements:**

Each clause is considered in order.

1.   Evaluate the header's expression.
2.   If it is a true value, execute the suite & skip the remaining clauses

**Syntax Tips:**

-   Always start with `if` clause
-   Zero or more `elif` clause
-   Zero or one `else` clause , always at the end

### Boolean Contexts

False value in Python: `False` , `0` , `''` , `None`

True value in Python: Anything else

### Iteration

**Example**

```python
i, total = 0, 0
while i < 3:
    i = i + 1
    total = i + total
```

**Execution Rule for While Statements**

1.   Evaluate the header expression
2.   If it is true value, execute the suite, then return to step 1
