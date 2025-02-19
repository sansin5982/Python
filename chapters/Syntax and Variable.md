# Python Syntax and Variables

## Python Syntax
Python syntax is simple and follows indentation rules to define blocks of code rather than using braces {} like other programming languages.

#### Example



```python
if True:
    print("This is indented correctly")
```

    This is indented correctly
    

Indentation is critical in Python; incorrect indentation will result in an error.

### Comments in Python

Comments help document the code and improve readability. Python supports single-line and multi-line comments.

* **Single-line comment**: Begins with `#`

* **Multi-line comment**: Uses triple quotes `'''` or `"""`

#### Example


```python
# This is a single-line comment
"""
This is a multi-line comment
spanning multiple lines
"""
```




    '\nThis is a multi-line comment\nspanning multiple lines\n'



## Variables in Python

Variables store data values. In Python, variable names can contain letters, numbers, and underscores but cannot start with a number.

#### Variable Declaration:


```python
x = 10  # Integer
name = "Python"  # String
pi = 3.14  # Float
```

Python variables are dynamically typed, meaning you don’t need to declare their type explicitly.

### Variable Naming Rules:

* Must start with a **letter** or an **underscore (_)**

* Cannot start with a number

* Can contain letters, numbers, and underscores

* Case-sensitive (`var` and `Var` are different)

### Multiple Assignments


```python
a, b, c = 5, 10, 15
```

### Summary:

* Python syntax relies on indentation.

* Comments improve code readability.

* Variables store data and are dynamically typed.

* Variable names must follow specific rules.

[⬅ Back to Home](../index.md)
