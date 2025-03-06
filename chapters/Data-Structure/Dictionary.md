## Dictionary
A dictionary in Python is an **unordered, mutable** collection that stores **key-value pairs**. Each key in a dictionary must be **unique** and **immutable** (e.g., strings, numbers, tuples), while values can be of any data type.

### 1. Creating a Dictionary
Dictionaries are defined using **curly braces** `{}` or the `dict()` function.

#### Example 1: Creating a Simple Dictionary


```python
my_dict = {"name": "Alice", "age": 25, "city": "New York"}
print(my_dict)
```

    {'name': 'Alice', 'age': 25, 'city': 'New York'}
    

Dictionaries store key-value pairs in an unordered manner.

#### Example 2: Creating an Empty Dictionary


```python
empty_dict = {}  # Correct way
print(type(empty_dict))  
```

    <class 'dict'>
    


```python
another_dict = dict()  # Another way to create an empty dictionary
print(type(another_dict))
```

    <class 'dict'>
    

#### Example 3: Dictionary with Mixed Data Types


```python
mixed_dict = {"name": "Alice", "age": 25, "is_student": False, "grades": [85, 90, 78]}
print(mixed_dict)
```

    {'name': 'Alice', 'age': 25, 'is_student': False, 'grades': [85, 90, 78]}
    

Values can be of different types (string, integer, list, boolean, etc.).

### 2. Accessing Dictionary Elements
Accessing Values Using Keys


```python
my_dict = {"name": "Alice", "age": 25, "city": "New York"}
print(my_dict["name"])  
print(my_dict["age"])
```

    Alice
    25
    

Use dict[key] to access values.

#### Using get() to Avoid Errors


```python
print(my_dict.get("city"))    
print(my_dict.get("country"))
```

    New York
    None
    

`get()` returns `None` if the key does not exist, avoiding errors.

### 3. Modifying a Dictionary
Adding or Updating Key-Value Pairs


```python
my_dict = {"name": "Alice", "age": 25}
my_dict["city"] = "New York" # adding new key value pair
my_dict["age"] = 26  # changing age value
print(my_dict)
```

    {'name': 'Alice', 'age': 26, 'city': 'New York'}
    

#### If the key exists, it updates the value; otherwise, it adds a new key-value pair.

### 4. Removing Elements from a Dictionary
#### Using `del` to Delete a Specific Key


```python
my_dict = {"name": "Alice", "age": 25, "city": "New York"}
del my_dict["age"]
print(my_dict)
```

    {'name': 'Alice', 'city': 'New York'}
    

`del` removes a key-value pair.

#### Using `pop()` to Remove and Return a Value


```python
removed_value = my_dict.pop("city")
print(removed_value)  
print(my_dict)
```

    New York
    {'name': 'Alice'}
    

`pop()` removes the key and returns its value.

#### Using `popitem()` to Remove the Last Inserted Key-Value Pair


```python
my_dict = {"name": "Alice", "age": 25}
my_dict.popitem()
print(my_dict)  
```

    {'name': 'Alice'}
    

Useful for removing the most recently added item.

#### Using `clear()` to Remove All Items


```python
my_dict.clear()
print(my_dict)  
```

    {}
    

### 5. Dictionary Operations
#### Merging Two Dictionaries
* Using `update()` (Modifies the original dictionary)
* Using `{**dict1, **dict2}` (Creates a new dictionary)


```python
dict1 = {"a": 1, "b": 2}
dict2 = {"b": 3, "c": 4}

dict1.update(dict2)  # Merging dict2 into dict1
print(dict1)
```

    {'a': 1, 'b': 3, 'c': 4}
    


```python
# Alternative: Create a new merged dictionary
merged_dict = {**dict1, **dict2}
print(merged_dict)
```

    {'a': 1, 'b': 3, 'c': 4}
    

If a key exists in both dictionaries, the second dictionary's value is used.

### 5. Looping Through a Dictionary
#### Looping Through Keys


```python
my_dict = {"name": "Alice", "age": 25, "city": "New York"}
for key in my_dict.keys():
    print(key)
```

    name
    age
    city
    

#### Looping Through Values


```python
for value in my_dict.values():
    print(value)
```

    Alice
    25
    New York
    

#### Looping Through Key-Value Pairs


```python
for key, value in my_dict.items():
    print(f"{key}: {value}")
```

    name: Alice
    age: 25
    city: New York
    

Use `.items()` to iterate over both keys and values.

### 6. Checking Membership in a Dictionary


```python
my_dict = {"name": "Alice", "age": 25}

print("name" in my_dict)  
print("country" in my_dict)
```

    True
    False
    

Only checks for keys, not values.

### 7. Copying a Dictionary


```python
dict1 = {"a": 1, "b": 2}
dict2 = dict1.copy()  # Creates a new dictionary
print(dict2)  
```

    {'a': 1, 'b': 2}
    

Avoid dict2 = dict1 as it only creates a reference, not a new copy.

#### Write a function that counts how many times each element appears in a list and returns a dictionary.


```python
def count_freq(num):
    freq_dict = {}
    for item in num:
        freq_dict[item] = freq_dict.get(item, 0) + 1
    return freq_dict

my_list = [1, 2, 2, 3, 3, 3, 4]    
count_freq(my_list)  
```




    {1: 1, 2: 2, 3: 3, 4: 1}



#### Write a function that returns the key with the highest value.


```python
dict1 = {"a": 10, "b": 25, "c": 15}

def highest_key(num):
    return max(num, key=num.get)

highest_key(dict1)
```




    'b'



#### Write a function that merges two dictionaries. If a key exists in both, the value from the second dictionary should be used.


```python
dict1 = {"a": 1, "b": 2}
dict2 = {"c": 3, "d": 4}

def merge_dicts(num1, num2):
    return {**num1, **num2}

merge_dicts(dict1, dict2)
```




    {'a': 1, 'b': 2, 'c': 3, 'd': 4}



Use dictionary unpacking {**dict1, **dict2} to merge.

#### Write a function that removes a key from a dictionary without causing an error if the key doesn’t exist.


```python
def remove_key(num, key):
    return num.pop(key, None)

my_dict = {"a": 1, "b": 2, "c": 3}

remove_key(my_dict, "b")
print(my_dict)
```

    {'a': 1, 'c': 3}
    

Use .pop(key, None) to avoid errors when the key doesn’t exist

#### Write a function that swaps keys and values in a dictionary.


```python
def invert_dict(num):
    return {value: key for key, value in num.items()}

my_dict1 = {"a": 1, "b": 2, "c": 3}

invert_dict(my_dict1)
```




    {1: 'a', 2: 'b', 3: 'c'}



#### Write a function that creates a dictionary from two lists (one as keys, the other as values).


```python
list1 = ["name", "age", "city"]
list2 = ["Alice", 25, "New York"]

def list_to_dict(num1, num2):
    return dict(zip(num1, num2))

list_to_dict(list1, list2)
```




    {'name': 'Alice', 'age': 25, 'city': 'New York'}



#### Write a function that filters a dictionary, keeping only items where values are greater than 10.


```python
dict1 = {"a": 5, "b": 15, "c": 25}

def filter_dict(num):
    return {k: v for k, v in num.items() if v > 10}

filter_dict(dict1)
```




    {'b': 15, 'c': 25}



#### Write a function that returns a set of keys common to two dictionaries.


```python
def common_keys(num1, num2):
    return set(num1.keys()) & set(num2.keys())

dict1 = {"a": 1, "b": 2, "c": 3}
dict2 = {"b": 10, "c": 20, "d": 30}

common_keys(dict1, dict2)
```




    {'b', 'c'}



#### Write a function that converts a dictionary into a list of (key, value) tuples.


```python
def dict_to_tuples(num):
    return list(num.items())

dict1 = {"a": 1, "b": 2, "c": 3}

dict_to_tuples(dict1)
```




    [('a', 1), ('b', 2), ('c', 3)]



#### Write a function that returns a dictionary sorted by values.


```python
dict1 = {"a": 3, "b": 1, "c": 2}

def sort_dict_value(num):
    return dict(sorted(num.items(), key=lambda item: item[1]))

sort_dict_value(dict1)
```




    {'b': 1, 'c': 2, 'a': 3}



#### Summary

|Proble|Concept|
|:---|:---|
|Count frequency of elements|`.get()` method|
|Find key with max value|`max(dictionary, key=dictionary.get)`|
|Merge dictionaries|`{**dict1, **dict2}`|
|Remove key safely|`.pop(key, None)`|
|Invert keys and values|Dictionary comprehension|
|Create dictionary from lists|`zip()`|
|Filter dictionary|Dictionary comprehension|
|Find common keys|`set() & set()`|
|Convert dictionary to tuples|`.items()`|
|Sort dictionary by values|`sorted()`|

[⬅ Back to Data Strcutures](../Data-Structure.md)
