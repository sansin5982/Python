# Data Types and Operators

## Data Types in Python
Python has various built-in data types that help store and manipulate different kinds of data.

#### Common Data Types:

|Data Type|Example|Description|
|:---|:---|:---|
|Integer|`x= 10`|Whole Number|
|Float|`y = 3.14`|Numbers with Decimal|
|String|`name = Python`|Sequence of characters|
|Boolean|`is_valid = True`|Represents True or False|
|List|`lst = [1, 2, 3]`|Ordered, mutable sequence|
|Tuple|`tup = (4, 5, 6)`|Ordered, immutable sequence|
|Dictionary|`{"key":"value"}`|Key-value pair collection|
|Set|`s = {1, 2, 3}`|Unordered, unique collection|

A list, tuple, set and dictionary in Python is a data type because it is a built-in type that holds an ordered collection of items. Python's official documentation classifies lists as a sequence data type, similar to strings and tuples.

However, lists can also be considered a data structure in a broader computer science sense, as they are used to store and manipulate collections of data. But in Python, lists are explicitly categorized as a data type.


```python
# integers
a = 3
type(a) # type is used to check the data types
```




    int




```python
# Floating-Point numbers
# They are in decimals
# Range: -10^308 to 10^308; 16 digits of precision
pi = 3.14 # 
type(pi)
```




    float




```python
# Scientific notation
c = 6e4 # 6 * 10 * 4
type(c)
```




    float




```python
# strings
name = "Sandeep"
type(name)
```




    str




```python
# Bloolean
a = True
type(a)
```




    bool



#### All procedural programming -> Case sensitive(Python, C, C++, Java)
#### All non-procedural languages -> Case insensitive (Sql, html)

## Type conversion
* Changing data types


```python
# convert float into integer value
a = 5.2
b = int(5) # it will convert into integer
print(type(b))
print(b)
```

    <class 'int'>
    5
    


```python
# convert integer into float value
a = 5
b = float(a)
print(b)
print(type(b))
```

    5.0
    <class 'float'>
    


```python
# converting string into number
name = "Sandeep"
a = int(name)
type(a) # it will throw error as it is invalid
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_9572\3511620100.py in <module>
          1 # converting string into number
          2 name = "Sandeep"
    ----> 3 a = int(name)
          4 type(a) # it will throw error as it is invalid
    

    ValueError: invalid literal for int() with base 10: 'Sandeep'



```python
# convert numbers into string
a = 5
string1 = str(a)
print(string1)
print(type(string1))
```

    5
    <class 'str'>
    


```python
# convert numbers into boolean value
# 0 is considered as False, and 1 or other numbers as True
a = 5
boolean1 = bool(a)
print(boolean1)
print(type(boolean1))
```

    True
    <class 'bool'>
    

## Operators
Operators are used to perform operations on variables and values.

### Types of operators


### 1. Arithmetic Operators: 
Perform mathematical operations.


```python
a = 10
b = 3
print(a + b)  # Addition
print(a - b)  # Subtraction
print(a * b)  # Multiplication
print(a / b)  # Division
print(a % b)  # Modulus
print(a ** b) # Exponentiation
```

    13
    7
    30
    3.3333333333333335
    1
    1000
    

### 2. Comparison Operators: 
Compare values and return Boolean results.


```python
print(a == b)  # Equal to
print(a != b)  # Not equal to
print(a > b)   # Greater than
print(a < b)   # Less than
print(a >= b)  # Greater than or equal to
print(a <= b)  # Less than or equal to
```

    False
    True
    True
    False
    True
    False
    

### 3. Logical Operators: 
Used to combine conditional statements.


```python
print(a > 5 and b < 5)  # AND
print(a > 5 or b > 5)   # OR
print(not (a > 5))      # NOT
```

    True
    True
    False
    

### 4. Bitwise Operators: 
Perform operations on binary values.


```python
print(a & b)  # AND
print(a | b)  # OR
print(a ^ b)  # XOR
print(~a)     # NOT
print(a << 1) # Left shift
print(a >> 1) # Right shift
```

    2
    11
    9
    -11
    20
    5
    

### 5. Assignment Operators: 
Assign values to variables.


```python
x = 10
x += 5  # Equivalent to x = x + 5
x -= 3  # Equivalent to x = x - 3
x *= 2  # Equivalent to x = x * 2
x /= 4  # Equivalent to x = x / 4
x %= 3  # Equivalent to x = x % 3
x **= 2 # Equivalent to x = x ** 2
```

### 6. Identity Operators: 
Check whether two variables reference the same object.


```python
a = [1, 2, 3]
b = a
c = [1, 2, 3]
print(a is b)  # True, because b references the same object as a
print(a is not c)  # True, because c is a different object
```

    True
    True
    

### 7. Membership Operators:
Check whether a value exists in a sequence.


```python
lst = [1, 2, 3, 4]
print(2 in lst)  # True
print(5 not in lst)  # True
```

    True
    True
    

#### Summary:

* Python has multiple built-in data types, including integers, floats, strings, booleans, lists, tuples, dictionaries, and sets.

* Lists and tuples are ordered sequences, while dictionaries and sets are collections.

* Python provides various operators such as arithmetic, comparison, logical, bitwise, assignment, identity, and membership operators.

* Operators help perform calculations, comparisons, and logical operations efficiently.

[⬅ Back to Home](../index.md)
