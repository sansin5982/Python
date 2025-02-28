## High Order Function
A **higher-order function** is a function that:

1. Takes another function as an argument, or
2. Returns a function as output.

Higher-order functions allow for more modular, readable, and reusable code.

### Passing a Function as an Argument
A function can accept another function as a parameter. This is useful for applying different operations dynamically.


```python
def apply_function(func, value):
    return func(value)

def square(x):
    return x**2

apply_function(square, 5)
```




    25



* `apply_function()` takes a function `func` and a `value`, then applies `func(value)`.
* `square()` is passed as an argument to `apply_function()`.


```python
apply_function(lambda x: x**2, 5) # apply function, labmda x: x**2 is function and 5 is value
```




    25



* Instead of defining a separate **square()** function, we use a **lambda function** inline.

### Returning a Function from Another Function
* A function can return another function, creating flexible function generators.


```python
def power(n):
    def exponent(x):
        return x ** n
    return exponent

square = power(2)
cube = power(3)

print(square(4))
print(cube(3))
```

    16
    27
    

* `power(n)` returns a function that raises `x` to the power `n`.
* `square` and `cube` are generated dynamically.


```python
power = lambda n: lambda x: x ** n

square = power(2)
cube = power(3)

print(square(4))
print(square(3))
```

    16
    9
    

### Built-in Higher-Order Functions
* Python has several built-in higher-order functions, including **map()**, **filter()**, and **reduce()**.

### map() – Apply a Function to an Iterable
* The **map()** function applies a given function to each element in an iterable.


```python
def square(x):
    return x**2

number = [1, 2, 3, 4, 5]
squared_numbers = list(map(square, number))
print(squared_numbers)
```

    [1, 4, 9, 16, 25]
    


```python
squared_numbers = list(map(lambda x: x**2, number))
print(squared_numbers)
```

    [1, 4, 9, 16, 25]
    

### filter() – Filter Elements Based on a Condition
The **filter()** function selects elements from an iterable that satisfy a condition.


```python
def is_even(x):
    return x % 2 == 0
    
number = [1, 2, 3, 4, 5, 6]

even_number = list(filter(is_even, number))
print(even_number)
```

    [2, 4, 6]
    


```python
even_number = list(filter(lambda x: x % 2 == 0, number))
print(even_number)
```

    [2, 4, 6]
    

### reduce() – Reduce an Iterable to a Single Value
* The **reduce()** function (from **functools**) applies a function cumulatively to reduce an iterable to a single value.


```python
from functools import reduce

def multiply(x, y):
    return x * y

numbers = [1, 2, 3, 4, 5]
product = reduce(multiply, numbers)
print(product)
```

    120
    

* reduce(multiply, numbers) computes 1 * 2 * 3 * 4 * 5 = 120.


```python
product = reduce(lambda x, y:x * y, numbers)
product
```




    120



[⬅ Back to Function](../Functions.md)
