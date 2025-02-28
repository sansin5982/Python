## User Defined Functions

### Writing a function
* **`def`** keyword is used define a function
* All user defined functions have a function name


```python
# Basic syntax
def my_function(parameters):
    block_for_function
    return expression
```

- The `def` keyword, along with the function name is used to define the function.
- The identifier rule must follow the function name.
- A function  can accept parameter/parameters or not (argument) or they can be optional.
- The function block is started with the colon (:), and block statements must be at the same indentation.
- The return statement is used to return the value. A function can have only one return.

#### Function without parameters


```python
def greet():
    print("Hello, Sandeep!")

# def is keyword
# greet is function name


greet() # calling greet() to execute the function
```

    Hello, Sandeep!
    

#### Function with parameters


```python
def add(a, b): # add(a, b) returns the sum of a and b
    return a + b

result = add(5, 3)
print(result) # add(5, 3) returns 8
```

    8
    

#### Function with default parameters


```python
def power(base, exponent=2):
    return base ** exponent

print(power(3)) # no exponent is given hence defualt value is 2
print(power(3, 3)) # exponent is given as 3
```

    9
    27
    

### Difference between `print()` and `return` in Python
Both `print()` and `return` are used to display or provide output, but they serve **different purposes** in Python.

|Feature|print()|return|
|:---|:---|:---|
|**Purpose**|Displays output on the console|Sends a value back to the caller|
|**Where Used?**|Inside any function or script|Inside a function to pass data|
|**Stores Data**|No, just print tot he screen|Yes, allow reuse of the result|
|**Can be assigned to a varaible**|No|Yes|
|**Effect on Execution**|Does not stop execution|Stops execution and exists the function|
|**Use Case**|Debugging diplaying messages|Passing values for further computation|


```python
def add(a, b):
    print(a+b)

result = add(5, 3) # will give 8
print("Result: ", result) # will give none
```

    8
    Result:  None
    

* `print(a + b)` only displays the output `(8)`, but `result` is `None` because nothing is returned.


```python
def add(a, b):
    return a + b

result = add(5, 3)
print("Result: ", result)
```

    Result:  8
    

* `return` **sends the value** (`8`) back to the caller, allowing it to be **stored and reused.**

### Print if a number is even or odd in a given list


```python
listA = [2, 3, 4, 5, 6] # default list 

def even_odd(x): # definng function
    for i in x: # creating loop as it will go through each element
        if i % 2 == 0: # if remainder is 0 it is an even number
            print("Even number")
        else: # if remainder is not 0 it is not an even number
            print("Odd number")
            
even_odd(listA)
```

    Even number
    Odd number
    Even number
    Odd number
    Even number
    

### Create a separate list for even and odd numbers from a given list


```python
listA = [2, 3, 4, 5, 6] # default list 

def even_odd(x): # definng function
    even = []
    odd = []
    for i in x: # creating loop as it will go through each element
        if i % 2 == 0: # if remainder is 0 it is an even number
            even.append(i)  # append even numbers
        else: # if remainder is not 0 it is not an even number
            odd.append(i) # append odd numbers
    return even, odd # return even and odd numbers
            

print(even_odd(listA)) # printing even odd numbers together
even_numbers, odd_numbers = even_odd(listA) # separating even and odd numbers as separate variable

print("Even:", even_numbers) 
print("Odd:", odd_numbers)
```

    ([2, 4, 6], [3, 5])
    Even: [2, 4, 6]
    Odd: [3, 5]
    

### Types of Arguments/parameters
* Positional Arguments
* Keword arguments
* Default Arguments
* Variable-length arguments


### Positional Arguments
* Position of the arguments should be in same sequence
* Changing sequence will change the meaning


```python
def greet(NAME, AGE):
    print(f"Hello, my name is {NAME} and I am {AGE} years old.")
    
greet("Sandeep", 42)
```

    Hello, my name is Sandeep and I am 42 years old.
    

**Changing the sequence**


```python
def greet(NAME, AGE):
    print(f"Hello, my name is {NAME} and I am {AGE} years old.")
    
greet(42, "Sandeep")
```

    Hello, my name is 42 and I am Sandeep years old.
    

### Key word arguments
* Use key words to define parameters
* Changing positions will also not affect anything


```python
def greet(NAME, AGE):
    print(f"Hello, my name is {NAME} and I am {AGE} years old.")

greet(NAME = "Sandeep", AGE = 42)
```

    Hello, my name is Sandeep and I am 42 years old.
    

* Changing the sequence will not affect anything.


```python
def greet(NAME, AGE):
    print(f"Hello, my name is {NAME} and I am {AGE} years old.")

greet(AGE = 42, NAME = "Sandeep")
```

    Hello, my name is Sandeep and I am 42 years old.
    

### Default Argument



```python
NUM = [2, 3, 4, 5, 6]

for i in NUM:
    print(i)
```

    2
    3
    4
    5
    6
    

### `help()`
* `help` function is used to see the arguments used in built-in functions


```python
help(print)
```

    Help on built-in function print in module builtins:
    
    print(...)
        print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
        
        Prints the values to a stream, or to sys.stdout by default.
        Optional keyword arguments:
        file:  a file-like object (stream); defaults to the current sys.stdout.
        sep:   string inserted between values, default a space.
        end:   string appended after the last value, default a newline.
        flush: whether to forcibly flush the stream.
    
    

* here print has many arguments, value, sep = ' ', end = '\n', etc. 
* value is must to print something
* Rest are default arguments, already predefined such as sep suggests space, end suggests new line.
* We can change these default arguments.


```python
for i in NUM:
    print(i, end = "-")
```

    2-3-4-5-6-

* Here i changed the end from new line to have `-` in between.

#### Using default argument calculate area of square and rectangle.


```python
def area(length, breadth=None): # breadth is already defined
    if breadth is None:
        return f"The area of square is: {length * length}"
    else:
        return f"The are of rectangle: {length * breadth}"

# Example  
print(area(5)) # calculate square
print(area(5, 4)) # calculate rectangle
```

    The area of square is: 25
    The are of rectangle: 20
    


```python
def greet(NAME, AGE=22): # Age is predfined
    print(f"Hello! my name is {NAME} and I am {AGE} years old.")

greet("Sandeep", 42) # I changed the Age
```

    Hello! my name is Sandeep and I am 42 years old.
    

### Variable length arguments
* `*args`
* `**kwargs`


```python
def operation(a, b):
  return a * b

operation(5, 6, 7)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_10764\852539860.py in <module>
          2   return a * b
          3 
    ----> 4 operation(5, 6, 7)
    

    TypeError: operation() takes 2 positional arguments but 3 were given


* Here we have given two arguments, a and b, but calling three (5, 6, 7).
* Hence, shows TypeError.
* Hence, in these scenarios we use `variable-length arguments`.

### *args


```python
# add few numbers but total n is not sure
def operations(*args):
    return sum(args)

print(operations(25, 50, 75)) # three parameters
print(operations(25, 50, 75, 25, 75)) # 5 parameters
print(operations(25, 50, 75, 100, 125, 175)) # 6 parametes
```

    150
    250
    550
    

* Here we have different parameters everytime

### **kwargs
* Called keyword arguments. Hence, we need a `key:value` pair.

#### dictionary
* `dict.values()`: Only gives values
* `dict.keys()`: Only gives keys
* `dict.items`: gives both keys and values
   


```python
def info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}:{value}")

info(Name = "Sandeep", Age = 42, City = "Lucknow")
info(Name = "Virat", Age = 22, City = "New Delhi")
info(Name = "Surehs", Age = 22)
info(Name = "Ramesh", Age = 22, City = "New Delhi", Education = "PhD")
```

    Name:Sandeep
    Age:42
    City:Lucknow
    Name:Virat
    Age:22
    City:New Delhi
    Name:Surehs
    Age:22
    Name:Ramesh
    Age:22
    City:New Delhi
    Education:PhD
    

#### Calculating average of different numbers



```python
def average(**kwargs):
    average_value = sum(kwargs.values())/len(kwargs.values())
    return average_value

print(average(num1 = 10, num2 = 15))
print(round(average(num1 = 15, num2 = 15, num3 = 25)), 2) # rounding for 2 decimal values
```

    12.5
    18 2
    

[⬅ Back to Function](../Functions.md)
