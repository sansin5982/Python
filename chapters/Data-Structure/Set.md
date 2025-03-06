## Set
A set in Python is an **unordered, mutable** collection that **only stores unique elements**. Unlike lists and tuples, sets do **not allow duplicates** and are useful when working with **distinct values**.

### 1. Creating a Set
Sets are defined using curly braces `{}` or the `set()` function.

#### Example 1: Creating a Simple Set


```python
my_set = {1, 2, 3, 4, 5}
print(my_set)  
```

    {1, 2, 3, 4, 5}
    

Sets are unordered, so the output may vary in order.

#### Example 2: Creating a Set with Duplicate Elements


```python
my_set = {1, 2, 2, 3, 4, 4, 5}
print(my_set)  
```

    {1, 2, 3, 4, 5}
    

A set automatically removes duplicate values.

#### Example 3: Creating an Empty Set


```python
empty_set = set()  # Correct way
print(type(empty_set)) 
```

    <class 'set'>
    


```python
wrong_set = {}  # This creates an empty dictionary, NOT a set!
print(type(wrong_set))  
```

    <class 'dict'>
    

Use `set()` to create an empty set, as `{}` creates a dictionary.

### 2. Accessing Elements in a Set
Sets do not support indexing or slicing because they are unordered.


```python
my_set = {10, 20, 30}
print(my_set[0])
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_28632\551607978.py in <module>
          1 my_set = {10, 20, 30}
    ----> 2 print(my_set[0])
    

    TypeError: 'set' object is not subscriptable


Use loops or set operations instead of indexing.

### 3. Modifying a Set
#### Adding Elements
* Using `add()` → Adds a single element.
* Using `update()` → Adds multiple elements.


```python
my_set = {1, 2, 3}
my_set.add(4)  # Adds one element
print(my_set)  
```

    {1, 2, 3, 4}
    


```python
my_set.update([5, 6, 7])  # Adds multiple elements
print(my_set) 
```

    {1, 2, 3, 4, 5, 6, 7}
    

### 4. Removing Elements from a Set
* Using `remove()` → Removes an element (error if not found).
* Using `discard()` → Removes an element (no error if not found).
* Using `pop()` → Removes a random element.
* Using `clear()` → Removes all elements.


```python
my_set = {10, 20, 30, 40, 50}

my_set.remove(30)  
print(my_set)  
```

    {50, 20, 40, 10}
    


```python
my_set.discard(100)  # No error, even though 100 is not present
print(my_set)  
```

    {50, 20, 40, 10}
    


```python
removed_element = my_set.pop()  # Removes a random element
print(removed_element)  # Output: (Random value removed)
print(my_set)  # Remaining elements
```

    50
    {20, 40, 10}
    


```python
my_set.clear()  # Removes all elements
print(my_set)  
```

    set()
    

Use `discard()` when unsure if an element exists to avoid errors.

### 5. Set Operations
**Union (`|` or `union()`)**

Combines elements from two sets (removes duplicates).


```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

union_set = set1 | set2  # Using `|` operator
print(union_set)  
```

    {1, 2, 3, 4, 5}
    


```python
union_set = set1.union(set2)  # Using `union()` method
print(union_set)
```

    {1, 2, 3, 4, 5}
    

**Intersection (`&` or `intersection()`)**

Finds common elements between two sets.


```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

intersection_set = set1 & set2  # Using `&` operator
print(intersection_set)
```

    {3}
    


```python
intersection_set = set1.intersection(set2)  # Using `intersection()`
print(intersection_set)  
```

    {3}
    

**Difference (`-` or `difference()`)**

Finds elements present in the first set but not in the second.


```python
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

difference_set = set1 - set2  # Using `-` operator
print(difference_set)  
```

    {1, 2}
    


```python
difference_set = set1.difference(set2)  # Using `difference()`
print(difference_set)  
```

    {1, 2}
    

**Symmetric Difference (`^` or `symmetric_difference()`)**

Finds elements not present in both sets.


```python
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

sym_diff_set = set1 ^ set2  # Using `^` operator
print(sym_diff_set) 
```

    {1, 2, 5, 6}
    


```python
sym_diff_set = set1.symmetric_difference(set2)  # Using `symmetric_difference()`
print(sym_diff_set) 
```

    {1, 2, 5, 6}
    

### 6. Looping Through a Set
#### Using `for` Loop


```python
my_set = {10, 20, 30, 40}
for item in my_set:
    print(item)
```

    40
    10
    20
    30
    

Order may vary due to unordered nature of sets.

### 7. Checking Membership in a Set


```python
my_set = {1, 2, 3, 4, 5}

print(3 in my_set)  
print(6 in my_set)  
```

    True
    False
    

### 8. Copying a Set


```python
set1 = {1, 2, 3}
set2 = set1.copy()  # Creates a copy
print(set2) 
```

    {1, 2, 3}
    

### 9. Set Functions

#### `len()`
Returns number of elements


```python
set1 = {1, 2, 3, 5, 4}
len(set1)
```




    5



#### `max()`
Returns the largest element


```python
max(set1)
```




    5



#### `min()`
Returns the smallest element


```python
min(set1)
```




    1



#### `sum()`
Returns sum of elements


```python
sum(set1)
```




    15



#### `set.add(x)`
Adds an element


```python
set1.add(10)
print(set1)
```

    {1, 2, 3, 4, 5, 10}
    

#### `set.remove(x)`
Removes an element (Error if missing)


```python
set1.remove(5)
print(set1)
```

    {1, 2, 3, 4, 10}
    

#### `set.discard(x)`
Removes element (No error if missing)


```python
set1.discard(10)
print(set1)
```

    {1, 2, 3, 4}
    

#### `set.pop()`
Removes a random element


```python
set1.pop()
```




    1




```python
print(set1)
```

    {2, 3, 4}
    

#### `set.clear()`
Removes all elements


```python
set1.clear()
```


```python
print(set1)
```

    set()
    

#### Write a function that takes a list and returns the number of unique elements using a set.


```python
my_list = [1, 2, 3, 3, 2, 4, 5, 6, 5]

def count_unique(num):
    return len(set(num))

count_unique(my_list)
```




    6



#### Write a function that returns True if two sets have common elements.


```python
set1 = {1, 2, 3}
set2 = {4, 5, 6}

def common_elements(num1, num2):
    return not set1.isdisjoint(set2)

common_elements(set1, set2)
```




    False



`isdisjoint()` to check if two sets have no common elements.

#### Write a function that returns elements in the first set but not in the second.


```python
set1 = {1, 2, 3, 4}
set2 = {4, 5, 6, 7}

def set_difference(num1, num2):
    return num1 - num2

set_difference(set1, set2)
```




    {1, 2, 3}




```python
def set_difference(num1, num2):
    return num1.difference(num2)

set_difference(set1, set2)
```




    {1, 2, 3}



Use `-` or `.difference()` to get unique elements from the first set.

#### Write a function that returns a set of common elements.


```python
def common_elements(num1, num2):
    return num1 & num2

common_elements(set1, set2)
```




    {4}




```python
def common_elements(num1, num2):
    return num1.intersection(num2)

common_elements(set1, set2)
```




    {4}



Use `&` or `.intersection()` to find common elements.

#### Write a function that merges two sets into one.


```python
def merge_set(num1, num2):
    return num1 | num2

merge_set(set1, set2)
```




    {1, 2, 3, 4, 5, 6, 7}




```python
def merge_set(num1, num2):
    return num1.union(num2)

merge_set(set1, set2)
```




    {1, 2, 3, 4, 5, 6, 7}



 Use `|` or `.union()` to combine sets.

#### Write a function that finds elements that are not common between two sets.


```python
def unique_elements(num1, num2):
    return num1 ^ num2

unique_elements(set1, set2)
```




    {1, 2, 3, 5, 6, 7}




```python
def unique_elements(num1, num2):
    return num1.symmetric_difference(num2)

unique_elements(set1, set2)
```




    {1, 2, 3, 5, 6, 7}



Use `^` or `.symmetric_difference()` to find non-common elements.

#### Write a function that removes duplicates from a list.


```python
list1 = [5, 3, 7, 9, 5, 6, 9]

def remove_dup(num):
    return list(set(num))

remove_dup(list1)
```




    [3, 5, 6, 7, 9]



#### Write a function that checks if set1 is a subset of set2.


```python
set1 = {1, 8}
set2 = {1, 2, 3, 4, 5, 6, 7}

def is_subset(num1, num2):
    return num1.issubset(num2)

is_subset(set1, set2)
```




    False



Use `issubset()` to check if all elements of set1 exist in set2.

#### Write a function that removes an element from a set without causing an error if the element is missing.


```python
def safe_remove(num, element):
    num.discard(element)
    
set1 = {1, 2, 3, 4}

print(safe_remove(set1, 2))
print(safe_remove(set1, 10))
print(set1)
```

    None
    None
    {1, 3, 4}
    

#### Summary

|Problem|Concept|
|:---|:---|
|Count unique elements|`set()` removes duplicates|
|Check common elements|`.isdisjoint()`|
|Find difference|`-` or `.difference()`|
|Find intersection|`&` or .`intersection()`|
|Merge sets|`.union()`|
|Find non-common elements|`^` or `.symmetric_difference()`|
|Remove duplicates from list|`set()` --> `list()`|
|Check subset|`.issubset()`|
|Count element frequency|`{item: lst.count(item)}`|
|Remove an element safely|`.discard()`|

[⬅ Back to Data Strcutures](../Data-Structure.md)
