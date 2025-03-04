## Tuple
A tuple in Python is an **ordered**, **immutable** collection that allows storing multiple items in a single variable. Unlike lists, tuples **cannot be modified** after creation, making them useful for storing **fixed data**.

### 1. Creating a Tuple
Tuples are defined using parentheses `()` and can contain any number of elements.

#### Creating a Simple Tuple


```python
my_tuple = (1, 2, 3, 4, 5)
print(my_tuple)  
```

    (1, 2, 3, 4, 5)
    

#### Tuples are similar to lists, but they are immutable (unchangeable).

#### Tuple with Different Data Types


```python
mixed_tuple = (10, "hello", 3.14, True)
print(mixed_tuple)
```

    (10, 'hello', 3.14, True)
    

A tuple can store integers, strings, floats, and booleans together.

#### Creating a Tuple with One Element


```python
single_element_tuple = (5,)  # Comma is necessary!
print(type(single_element_tuple))  
```

    <class 'tuple'>
    


```python
not_a_tuple = (5)  # Without a comma, it's just an integer
print(type(not_a_tuple))  
```

    <class 'int'>
    

### 2. Accessing Elements in a Tuple

#### Indexing (Zero-Based Index)


```python
my_tuple = (10, 20, 30, 40, 50)
print(my_tuple[0])   
print(my_tuple[2])   
print(my_tuple[-1])
```

    10
    30
    50
    

#### Slicing a Tuple


```python
my_tuple = (10, 20, 30, 40, 50)
print(my_tuple[1:4])  
print(my_tuple[:3])   
print(my_tuple[2:])   
print(my_tuple[-3:])
```

    (20, 30, 40)
    (10, 20, 30)
    (30, 40, 50)
    (30, 40, 50)
    

### 3. Tuple Immutability (Cannot be Modified)
Tuples **do not support item assignment** because they are immutable.


```python
my_tuple = (10, 20, 30)
my_tuple[1] = 25
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_9200\1220477182.py in <module>
          1 my_tuple = (10, 20, 30)
    ----> 2 my_tuple[1] = 25
    

    TypeError: 'tuple' object does not support item assignment


#### You can create a new tuple but cannot modify an existing one.

### 4. Tuple Operations

#### Concatenation (+)


```python
tuple1 = (1, 2, 3)
tuple2 = (4, 5, 6)
new_tuple = tuple1 + tuple2
print(new_tuple)  
```

    (1, 2, 3, 4, 5, 6)
    

Tuples can be combined using `+`.

#### Repetition `(*)`


```python
repeat_tuple = (1, 2) * 3
print(repeat_tuple)  
```

    (1, 2, 1, 2, 1, 2)
    

Repeats the tuple `n` times.

### 5. Tuple Methods
Tuples have limited methods because they are immutable.

#### Count the Occurrences of an Element


```python
my_tuple = (1, 2, 3, 2, 4, 2, 5)
print(my_tuple.count(2)) 
```

    3
    

#### Find the Index of an Element


```python
my_tuple = (10, 20, 30, 40)
print(my_tuple.index(30))
```

    2
    

### 6. Looping Through a Tuple
#### Using `for` Loop


```python
my_tuple = (10, 20, 30, 40)
for item in my_tuple:
    print(item)
```

    10
    20
    30
    40
    

#### Using range(len(tuple)) (Accessing via Index)


```python
my_tuple = (10, 20, 30, 40)

for i in range(len(my_tuple)):
    print(f"Index: {i}, Value: {my_tuple[i]}")
```

    Index: 0, Value: 10
    Index: 1, Value: 20
    Index: 2, Value: 30
    Index: 3, Value: 40
    

#### Using `enumerate()` (Best for Index & Value)



```python
my_tuple = (10, 20, 30, 40)

for i, value in enumerate(my_tuple):
    print(f"Index: {i}, Value: {value}")
```

    Index: 0, Value: 10
    Index: 1, Value: 20
    Index: 2, Value: 30
    Index: 3, Value: 40
    

### 7. Converting Between Tuples and Lists
Convert a Tuple to a List


```python
my_tuple = (10, 20, 30)
my_list = list(my_tuple)
print(my_list)
type(my_list)
```

    [10, 20, 30]
    




    list



Convert a List to a Tuple


```python
my_list = [1, 2, 3]
my_tuple = tuple(my_list)
print(my_tuple) 
type(my_tuple)
```

    (1, 2, 3)
    




    tuple



#### Useful when you need to modify a tuple (convert to list, modify, then convert back).

### 8. Nested Tuples
A tuple can contain other tuples inside it.


```python
nested_tuple = ((1, 2), (3, 4), (5, 6))
print(nested_tuple[1])  
print(nested_tuple[1][0])
```

    (3, 4)
    3
    

### 9. Tuple Packing and Unpacking
#### Tuple Packing (Creating a Tuple)


```python
packed_tuple = 10, 20, 30  # No parentheses needed
print(packed_tuple)
```

    (10, 20, 30)
    

#### Tuple Unpacking


```python
a, b, c = packed_tuple
print(a, b, c)
```

    10 20 30
    

Tuple unpacking assigns values to multiple variables at once.

### 10. Tuple Functions

#### len()
Returns length of the tuple


```python
my_tuple = (5, 9, 8, 6)
len(my_tuple)
```




    4



#### max()
Returns the maximum value


```python
max(my_tuple)
```




    9



#### min()
Returns the minimum value 


```python
min(my_tuple)
```




    5



#### sum()
Returns the sum of elements


```python
sum(my_tuple)
```




    28



#### Write a function that counts how many times an element appears in a tuple.


```python
def count_elements(num, x):
    return num.count(x)

my_tuple = (2, 5, 2, 9, 4, 2)

count_elements(my_tuple, 2)
```




    3



#### Write a function that returns the maximum and minimum values in a tuple.


```python
def max_min(num):
    return max(num), min(num)

max_min(my_tuple)
```




    (9, 2)



#### Write a function that converts a tuple to a list, modifies a value, and returns a new tuple.


```python
def modify_tuple(num, index, value):
    num = list(num)
    num[index] = value
    return tuple(num)


modify_tuple(my_tuple, 0, 5)
```




    (5, 5, 2, 9, 4, 2)



#### Write a function that returns the index of the first occurrence of an element.


```python
def find_index(num, element):
    return num.index(element)

find_index(my_tuple, 5)
```




    1



#### Write a function to reverse a tuple without using a loop.


```python
def reverse_tuple(num):
    return num[::-1]

my_tuple = (2, 5, 2, 9, 4, 2)
reverse_tuple(my_tuple)
```




    (2, 4, 9, 2, 5, 2)



#### Write a function that merges two tuples and returns a new tuple.


```python
def merge_tuple(num1, num2):
    return num1+num2

num1 = (25, 75, 25)
num2 = (35, 65, 35)

merge_tuple(num1, num2)
```




    (25, 75, 25, 35, 65, 35)



#### Write a function that checks if an element exists in a tuple.


```python
def element_exists(num, element):
    return element in num
    
my_tuple = (2, 4, 6, 8)
element_exists(my_tuple, 6)
```




    True



#### Write a function that converts a list of tuples into a dictionary.


```python
list_tuples = [(1, 'one'), (2, 'two'), (3, 'three')]

def tuple_dict(num):
    return dict(list_tuples)

tuple_dict(list_tuples)
```




    {1: 'one', 2: 'two', 3: 'three'}



#### Write a function that finds common elements between two tuples.


```python
my_tuple1 = (1, 2, 3, 4, 5)
my_tuple2 = (3, 4, 5, 6, 7)

def common_element(num1, num2):
    return tuple(set(num1) & set(num2))

common_element(my_tuple1, my_tuple2)
```




    (3, 4, 5)



[⬅ Back to Data Strcutures](../Data-Structure.md)
