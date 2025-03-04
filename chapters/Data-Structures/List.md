## List
A list in Python is a mutable, ordered, and dynamic collection that allows storing multiple items in a single variable. Lists can hold elements of different data types, including integers, strings, floats, and even other lists.

### 1. Creating a List
Lists are defined using square brackets `[]` and can contain any number of elements.

#### Example 1: Creating a Simple List


```python
my_list = [1, 2, 3, 4, 5]
print(my_list)  
```

    [1, 2, 3, 4, 5]
    

Here, my_list contains five integer elements.

#### Example 2: List with Mixed Data Types


```python
mixed_list = [10, "hello", 3.14, True]
print(mixed_list)
```

    [10, 'hello', 3.14, True]
    

This list contains an integer, a string, a float, and a boolean value.

### 2. Accessing Elements in a List
#### Indexing
Python lists use `zero-based indexing`, meaning the first element is at `index 0`.


```python
my_list = [10, 20, 30, 40, 50]
print(my_list[0])   # Output: 10 (first element)
print(my_list[2])   # Output: 30 (third element)
print(my_list[-1])  # Output: 50 (last element)
```

    10
    30
    50
    

#### Slicing
Slicing allows extracting a subset of a list.


```python
my_list = [10, 20, 30, 40, 50]
print(my_list[1:4])  # Output: [20, 30, 40] (elements from index 1 to 3)
print(my_list[:3])   # Output: [10, 20, 30] (first 3 elements)
print(my_list[2:])   # Output: [30, 40, 50] (from index 2 to end)
print(my_list[-3:])  # Output: [30, 40, 50] (last 3 elements)
```

    [20, 30, 40]
    [10, 20, 30]
    [30, 40, 50]
    [30, 40, 50]
    

### 3. Modifying a List (Mutable)
Lists allow modification after creation.

#### Example 1: Changing Elements


```python
my_list = [10, 20, 30, 40, 50]
my_list[1] = 25  # Change value at index 1
print(my_list)  
```

    [10, 25, 30, 40, 50]
    

#### Example 2: Adding Elements
* Using `append()` → Adds an element to the end.
* Using `insert()` → Adds an element at a specific index.
* Using `extend()` → Adds multiple elements.


```python
# append
my_list = [1, 2, 3]
my_list.append(4) # adding 4 at the end 
print(my_list)  
```

    [1, 2, 3, 4]
    


```python
# insert
my_list.insert(1, 10)  # adding 10 at index 1
print(my_list)  
```

    [1, 10, 2, 3, 4]
    


```python
# extend
my_list.extend([5, 6, 7])  # adding 5, 6, 7
print(my_list)  
```

    [1, 10, 2, 3, 4, 5, 6, 7]
    

### 4. Removing Elements from a List
* Using `remove(value)` → Removes the first occurrence of the value.
* Using `pop(index)` → Removes and returns the element at a given index.
* Using `del` → Deletes an element or the entire list.
* Using `clear()` → Removes all elements.


```python
# remove
my_list = [10, 20, 30, 40, 50]

my_list.remove(30)  
print(my_list)  
```

    [10, 20, 40, 50]
    


```python
# pop
popped_value = my_list.pop(1)  
print(popped_value)  
print(my_list)
```

    20
    [10, 40, 50]
    


```python
# del
del my_list[0]  
print(my_list)  
```

    [40, 50]
    


```python
# clear
my_list.clear()  
print(my_list)  
```

    []
    

### 5. Looping Through a List
#### Example 1: Using `for` Loop


```python
my_list = [10, 20, 30, 40]
for item in my_list:
    print(item)
```

    10
    20
    30
    40
    

#### Example 2: Using while Loop


```python
my_list = [10, 20, 30, 40]
i = 0
while i < len(my_list):
    print(my_list[i])
    i += 1
```

    10
    20
    30
    40
    

### 6. List Comprehension (Shorter Code)
A compact way to create lists.

#### Example: Creating a List of Squares


```python
squares = [x ** 2 for x in range(5)]
print(squares)
```

    [0, 1, 4, 9, 16]
    

#### Example: Filtering Even Numbers


```python
numbers = [1, 2, 3, 4, 5, 6]
evens = [x for x in numbers if x % 2 == 0]
print(evens)
```

    [2, 4, 6]
    

### 7. Sorting and Reversing a List
#### Sorting a List
* Using `sort()` → Sorts the list in ascending order.
* Using `sorted()` → Returns a sorted copy.


```python
my_list = [5, 3, 8, 1, 4]
my_list.sort()
print(my_list) 
```

    [1, 3, 4, 5, 8]
    


```python
sorted_list = sorted(my_list, reverse=True)
print(sorted_list)
```

    [8, 5, 4, 3, 1]
    

#### Reversing a List


```python
my_list = [10, 20, 30, 40]
my_list.reverse()
print(my_list)  
```

    [40, 30, 20, 10]
    

### 8. Copying a List
* Using `copy()` → Creates a shallow copy.
* Using `slicing [:]` → Another way to copy.


```python
list1 = [1, 2, 3]
list2 = list1.copy()
print(list2)
```

    [1, 2, 3]
    

### 9. List Functions

#### len()
returns the length of the value


```python
my_list = [1, 2, 3, 4 , 5]
len(my_list)
```




    5



#### max()
returns the largest value


```python
max(my_list)
```




    5



#### min()
returns the smallest value


```python
min(my_list)
```




    1



#### sum()
Returns the sum of all elements


```python
sum(my_list)
```




    15



#### index() 
returns the index of `x`


```python
my_list.index(4)
```




    3



#### count()
Counts occurences of `x`


```python
my_list = [2, 3, 4, 5, 3]
my_list.count(3)
```




    2



### Practice problems

#### Write a function to return the sum of all elements in a list.


```python
def list_sum(num):
    return sum(num)

my_list = [25, 50, 75]

list_sum(my_list)
```




    150



#### Write a function that returns both the maximum and minimum values in a list.


```python
def min_max(num):
    return min(num), max(num)

min_max(my_list)
```




    (25, 75)



#### Write a function that removes duplicate elements from a list and returns a new list.


```python
def remove_dup(num):
    return (set(num))

my_list = [25, 25, 50, 75, 100]
remove_dup(my_list)
```




    {25, 50, 75, 100}



#### Write a function that returns a list of common elements between two lists.


```python
def common_elements(num1, num2):
    return list(set(num1) & set(num2)) # & is used for intersection

my_list1 = [1, 2, 3, 4, 5]
my_list2 = [3, 4, 5, 6, 7]

common_elements(my_list1, my_list2)
```




    [3, 4, 5]



#### Write a function that reverses a list without using the built-in reverse() method.


```python
def reverse_list(num):
    return num[::-1]

reverse_list(my_list)
```




    [100, 75, 50, 25, 25]



#### Write a function that checks if a list is the same when read forwards and backwards.


```python
def is_palindrome(num):
    return num == num[::-1]

print(is_palindrome([1, 2, 3, 2, 1]))
print(is_palindrome([1, 2, 3, 4, 5]))
```

    True
    False
    

#### Write a function that finds the second largest number in a list.


```python
def second_largest(num):
    unique_num = list(set(num)) # to remove duplicates
    unique_num.sort() # sort in ascending order
    return unique_num[-2] # second last number

my_list = [2, 5, 9, 3, 4]
second_largest(my_list)
```




    5



#### Write a function that counts how many times each element appears in a list.


```python
my_list = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4, 5, 5]


def freq_count(num):
    freq = {} # dictionary to store count
    for i in num:
        freq[i] = num.count(i)             
    return freq


freq_count(my_list)
```




    {1: 1, 2: 2, 3: 3, 4: 4, 5: 2}



#### Explanation:
* The .count(item) method counts occurrences of item in lst.
* This method works but is not efficient for large lists because .count() iterates through the list multiple times.


```python
def freq_count(lst):
    freq_dict = {}  
    for item in lst:
        freq_dict[item] = freq_dict.get(item, 0) + 1  # Increase count
    return freq_dict


freq_count(my_list)
```




    {1: 1, 2: 2, 3: 3, 4: 4, 5: 2}



####  Why is this method better?
* Efficiency: It only loops through the list once (O(n)), unlike .count(), which loops multiple times (O(n²)).
* Scalability: Works well with large lists.

#### Write a function that merges two sorted lists into a single sorted list.


```python
list1 = [1, 5, 3, 9, 10, 4]
list2 = [1, 2, 3, 9, 7, 3]

def sort_list(num1, num2):
    return sorted(num1 + num2)

sort_list(list1, list2)
```




    [1, 1, 2, 3, 3, 3, 4, 5, 7, 9, 9, 10]



#### Write a function that finds all pairs of numbers in a list that sum up to a given target.
For example: list is [1, 2, 3, 4, 5] and target is 6. So 5 + 1 = 6 and 4 + 2 = 6


```python
my_list = [1, 2, 3, 4, 5]

# We need index position not actual value
def find_pairs(lst, target):
    pairs = []
    for i in range(len(lst)): # Outer loop iterates through each element. length of list is 5 hence range is 0 till 4 (len - 1)
        for j in range(i + 1, len(lst)): # # Inner loop checks pairs
            if lst[i] + lst[j] == target:
                pairs.append((lst[i], lst[j]))
    return pairs

print(find_pairs(my_list, 6))
```

    [(1, 5), (2, 4)]
    

[⬅ Back to Data Strcutures](../Data-Structure.md)
