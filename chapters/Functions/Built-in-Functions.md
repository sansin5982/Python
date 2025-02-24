## Built-in Functions in

Python comes with many built-in functions that make programming easier. Here are 20 important built-in functions with examples:

### `print()` 
* Display output


```python
print("Hello, World!")
```

    Hello, World!
    

### `len()` 
* Returns the length of a sequence


```python
print(len("Python"))
```

    6
    

### `type()` 
* Returns the type of an object


```python
print(type(10))
```

    <class 'int'>
    

### `input()`
* Takes user input


```python
name = input("Enter your name: ")
print("Hello,", name)
```

    Enter your name: Sandeep
    Hello, Sandeep
    

### `int()` 
* Converts a value to an integer


```python
print(int("10"))
```

    10
    

### `float()`
* Converts a value to float



```python
print(float("10.5"))
```

    10.5
    

### `str()` 
* Converts a value to a string


```python
print(str(100))
```

    100
    


```python
a = str(100)
type(a)
```




    str



### `abs()` 
* Returns the absolute value


```python
print(abs(-5))
```

    5
    

### `max()`
* Returns the maximum value


```python
max(10, 20, 30)
```




    30



### `min()`
* Returns the minimum value


```python
min(10, 20, 30)
```




    10



### `sum()`
* Return the sum of a sequence


```python
sum([3, 4, 5, 6])
```




    18



### `round()`
* Round a number to the nearest integer


```python
round(44/7, 2) # here 2 is for 2 values after decimals
```




    6.29



### `pow()` 
* Returns the power of a number


```python
pow(2, 3) # here number is 2 and power is 3 so 2 x 2 x 2
```




    8



### sorted()
* Returns a sorted list


```python
sorted([5, 2, 8, 6]) # ascending order
```




    [2, 5, 6, 8]



### list()
* Converts a sequence into a list



```python
list("hello")
```




    ['h', 'e', 'l', 'l', 'o']



### `dict()`
* Creates a dictionary


```python
dict(name='Sandeep', age = 25)
```




    {'name': 'Sandeep', 'age': 25}



### `set`
* Create a set



```python
set([1, 2, 2, 3])
```




    {1, 2, 3}



### `tuple`
* Converts a sequence into a tuple


```python
tuple([1, 2, 3])
```




    (1, 2, 3)



### `enumerate()`
* Returns index-value pairs


```python
for i, v in enumerate(["a", "b", "c"]):
    print(i, v)
```

    0 a
    1 b
    2 c
    

### `zip()`
* Combines multiple sequences


```python
names = ["Alice", "Bob"]
scores = [85, 90]

dict(zip(names, scores))
```




    {'Alice': 85, 'Bob': 90}



[⬅ Back to Function](../Functions.md)
