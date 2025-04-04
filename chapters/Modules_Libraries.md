# Modules vs Libraries
As Python developers, we often use pre-written code to avoid reinventing the wheel. Python provides this through **modules** and **libraries**. These two concepts help you reuse code, organize it better, and make your programs efficient and readable.

Although people often use these terms interchangeably, **modules and libraries are not the same**. Let's understand the difference clearly with definitions, diagrams, examples, and comparisons.

## Modules

**A module is a single Python file `(.py)`** containing **functions**, **classes**, and **variables** that we can import and use in other programs.

### Key Features of a Module
* One `.py` file.
* Contains reusable code: functions, classes, variables.
* Helps organize and reuse code.


#### Example with math module


```python
import math

print(math.sqrt(25))   
print(math.pi)         
```

    5.0
    3.141592653589793
    

### Importing a module




```python
#### General syntax
import <module_name>
```


```python
# Import the OS module
import os
```


```python
# Check the type
type(os)
```




    module



## Python module

* There are around 200 built-in modules
* Popular modules include:
    * `os` - for interpreting and interacting with your operating system
    * `collections` - advanced data structure types and functions
    * `string` - performing string operations
    * `logging` - to log information when testing or running software
    * `subprocess` - to run terminal command.

- list all files in a directory
ls

* Full list of python modules:
https://docs.python.org/3/pymodindex.html

### Finding a module's functions
* Look at the documentation
- call help()
- Warning - will return a very large output!

* Useful if need to refer to the directory repeatedly

### Importing a single function from a module
* Importing a whole module can require a lot of memory
* Can impact a specific function from a module


```python
# importing a single function from a module
from os import chdir 
```

## Libraries
A **library** is a **collection of modules** bundled together. Libraries usually offer broader functionalities and can be installed via tools like `pip`.

### Key Features of a Library:
* A package (directory) of multiple modules.
* Offers tools for complex tasks (data science, machine learning, web development, etc.).
* May contain sub-packages and dependencies.

* Module = Python file
* Anyone can create a python file!
* A collection of modules = **Library**
* Libraries are publicly available and free
* First need to be downloaded from PyPl
* Then can be imported and used like modules

### Installing a package
`python3 -m pip install <package_name>`

* `python3` - Used to execute Python code from the terminal
* `pip` - Preferred Installed Program


`python3 -m pip install pandas`

### Importing a package

`import pandas`

- using alias

`import pandas as pd`


```python
import pandas as pd

df = pd.DataFrame({'Name': ['Alice', 'Bob'], 'Age': [25, 30]})
print(df)
```

        Name  Age
    0  Alice   25
    1    Bob   30
    

### Module vs library
* Library --> NumPy
    * Module 1 --> numpy.core
    * Module 2 --> numpy.linlag
    * Module 3 --> numpy.random


```python

```
