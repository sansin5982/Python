## Data Strcutures
A data structure is a way of organizing and storing data in a program to perform operations efficiently. Python provides several built-in data structures, including lists, tuples, sets, and dictionaries.

### 1. List
* **square bracket `[]`** is used
* **Ordered** → Maintains the order of elements.
* **Mutable** → Can be modified (elements can be added, removed, or changed).
* **Allows duplicates** → Same value can appear multiple times.


```python
my_list = [1, 2, 3, 4, 5]  # Creating a list
print(my_list)             
```

    [1, 2, 10, 4, 5, 6]
    

### 2. Tuple
* **round bracket `()`** is used
* **Ordered** → Maintains the order of elements.
* **Immutable** → Cannot be modified after creation.
* **Allows duplicates** → Same value can appear multiple times.


```python
my_tuple = (1, 2, 3, 4, 5)  # Creating a tuple
print(my_tuple)
```

    (1, 2, 3, 4, 5)
    

#### Why Use Tuples?
* Tuples are faster than lists.
* Used when data should not change (e.g., storing months of a year).

### 3. Set
* **curly bracket `{}`** is used
* **Unordered** → No specific order of elements.
* **Mutable** → Can add/remove elements.
* **Unique elements only** → No duplicates allowed.


```python
my_set = {1, 2, 3, 4, 5, 5}  # Duplicate '5' is ignored
print(my_set)  

```

    {1, 2, 3, 4, 5}
    

### 4. Dictionary
* **curly bracket {}** is used 
* **Key-Value Pairs** → Stores data in {key: value} format.
* **Keys are unique** → No duplicate keys allowed.
* **Values can be modified** → Mutable data structure.


```python
my_dict = {"name": "Alice", "age": 25, "city": "New York"}
print(my_dict)  
```

    {'name': 'Alice', 'age': 25, 'city': 'New York'}
    

#### Summary
|Data Structure|Orderd|Mutable|Duplicates|Key:Value pair|
|:---|:---|:---|:---|:---|
|**List**|Yes|Yes|Yes|No|
|**Tuple**|No|Yes|Yes|No|
|**Set**|No|Yes|No|No|
|**Dictionary**|Yes|Yes|No (Keys)|No|

[⬅ Back to Home](../index.md)
