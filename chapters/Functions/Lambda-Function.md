## Lambda Function

### What is a Lambda Function?
A **lambda function** in Python is an **anonymous function** (i.e., a function without a name) that is defined using the `lambda` keyword. It can take multiple arguments but can only have one **expression**.

### Why Do We Use Lambda Functions?
* **Concise & Readable**: They allow writing short functions in a single line.
* **Inline Usage**: They are useful in functions like map(), filter(), and sorted() where a small function is needed temporarily.
* **No Need for a Name**: They are great when we don’t need to reuse the function elsewhere in the code.

### Lambda vs User-Defined Function
Lambda functions are **better** than user-defined functions when we need a small and temporary function. Below is a comparison:


```python
# Using a regular function to multiply 2 numbers
def multiply(x, y):
    return x * y

multiply(4, 5)
```




    20




```python
# using lambda function
multiply = lambda x, y: x * y

multiply(4, 5)
```




    20



### Why is Lambda Better Here?
* The **lambda function** is **shorter** and **doesn't require a name**.
* It’s **ideal for quick, one-time-use functions** (e.g., inside map(), filter()).
* If the function is **used only once**, defining a full function is unnecessary.

#### Q: Adding two numbers


```python
add = lambda x, y: x + y

add(5, 9)
```




    14



#### Square a number


```python
square = lambda x: x ** 2

square(5)
```




    25



#### Find the maximum of three numbers


```python
max_of_three = lambda x, y, z: x if (x > y and x > z) else (y if y > z else z)
max_of_three(15, 7, 9)
```




    15



#### Checking If a Year Is a Leap Year
* A year is a leap year if:

    * It is divisible by 4 AND
    * Not divisible by 100, unless it is also divisible by 400.


```python
is_leap_year = lambda year: (year % 4 == 0 and year % 100 !=0) or (year % 400 == 0)
is_leap_year(1800)
```




    False



#### Convert Temperature Between Celsius and Fahrenheit
* for Celisus, temp * 9/5 + 32
* for fahrenheit (temp - 32) * 5/9)


```python
convert_temp = lambda temp, unit: (temp * 9/5 +32) if unit == "C" else ((temp -32) * 5/9)
convert_temp(-40, "C")
```




    -40.0




```python
convert_temp(-40, "F")
```




    -40.0



#### Calculate the Quadratic Equation Result
$$
ax^2 + bx + c
$$


```python
quadratic = lambda a, b, c, x: a*x**2 + b*x + c
quadratic(1, -3, 2, 2)
```




    0



[⬅ Back to Function](../Functions.md)
