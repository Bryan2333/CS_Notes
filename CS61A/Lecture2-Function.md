# Lecture 1 Functions

## Expression

### Types of expressions

An expression describes a computation and evaluates to a value.

<img src="https://s2.loli.net/2022/11/24/LDbyzfMk6HmYg43.jpg" alt="屏幕截图 2022-11-24 184729.jpg" style="zoom: 50%;" />

### Call Expressions in Python

All expressions can use function call notation

```python
2015

2000 + 15

max(2,4)

min(-2.10000)

from math import add, mul
add(2,3)
mul(2,3)
```

### Anatomy of a Call Expression

```python
   add      (    2      ,       3       )
# Operator    Operand       Operand
```

Operators and Operands are also expressions, So they evaluate to values

**Evalution procedure for call expressions: **

1.   Evalutate the operator and then the operand subexpressions
2.   **Apply**  the **function** that is the value of the operator subexpression to the **arguments** that are the values of the operands subexpressions

### Evaluating Nested Expressions

```python
mul(add(2, mul(4, 6)), add(3, 5))
```

<img src="https://s2.loli.net/2022/11/23/wuhfoiq3kHdzLSI.jpg" alt="屏幕截图 2022-11-23 222736.jpg" style="zoom:67%;" />

## Names, Assignment, and User-Defined Functions

### Types of Expression

There are two type of expressions in Python, **Primitive Expression** and **Call Expression**

**Primitive Expression Examples:**

-   $2^{100}$ 
-   $sin\pi$ 
-   $7\ mod\ 2$ 
-   $\sqrt{349111}$
-   $|-1111|$

**Call Expression Examples:**

-   `add(2,3)`

-   ```python
    def square(x):
        return x*x
    ```

### Name

If a value has been given a name, we say that the name **binds** to the value

```python
>>> radius = 10
>>> radius
10
>>> 2 * radius
20
```

Names can also be imported via `import` statements.

```python
>>> from math import pi
>>> pi
3.141592653589793
```

### Assignment

The $=$ symbol is called the **assignment** operator in Python.

Assignment is our simplest means of **abstraction**, for it allows us to use simple names to refer to the results of compound operations

Names can also be bounded to the function

```python
>>> max
<built-in function max>
```

We can also use assignment statements to give an new name to the existing function

```python
>>> f = max
>>> f(2,5)
5
```

And we can also rebind the name to an new value

```python
>>> f = 10
>>> f
10
```

## Environment Diagrams

### Environment Diagrams

Environment diagrams visualize the interpreter's proLcess.

<img src="https://s2.loli.net/2022/11/23/udS8cwqUOmBbIG5.jpg" alt="屏幕截图 2022-11-23 225827.jpg" style="zoom: 50%;" />

### Assignment Statements

**Execution rule for assignment statements :**

1.   Evaluate all expressions to the right of $=$ from the left to right
2.   Bind all names to the left of $=$ to the resulting values in the current frame

## Defining Functions

### Defining Functions

Assignment is a simple means of abstraction: bind names to values

Function definition is a more powerful means of abstraction: bind names to *expressions*

```Python
def <name>(<formal parameters>):
    return <return expression>
```

-   Function *signature* refers to **the first line of the function definition**, indicating how many arguments a function takes. 

-   **The rest part of function** definition is function *body*, defining the computational performed when the function is applied

**Execution procedure for def statements**

1.   Create a function with signature `<name>(<formal parameters>)`
2.   Set the body of that function to be everything indented after the first line
3.   Bind `<name>` to that function in the current frame


### Calling User-Defined Functions

**Procedure for calling/applying user-defined functions**

1.   Add a local frame, forming an **new** environment
2.   Bind the function's formal parameters to its arguments in that frame
3.   Execute the body of the function in that new environment

<img src="https://s2.loli.net/2022/11/24/rZHxvbQu58e2MVm.jpg" alt="屏幕截图 2022-11-24 184625.jpg" style="zoom:50%;" />

**A function's signature has all the information needed to create a local frame**

### Looking Up Names In Environment

So far, the current enviroment is either : 

-   The global frame alone
-   A local frame, **followed** by the global frame

**An environment is a sequence of frames**

**A name evaluates to the value bound to that name in the earliest frame of the current environment in which that name is found**

**Example :**

to look up some name in the body of **square** function

-   Look for that name in the local frame
-   If not found, look for it in the global frame
