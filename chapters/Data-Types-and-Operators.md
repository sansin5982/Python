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
