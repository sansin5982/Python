### Recursive Function

#### What is a Recursive Function?
A recursive function is a function that calls itself to solve a problem. It typically breaks down a larger problem into smaller, simpler subproblems and has a base case to stop the recursion.

#### Why Do We Need Recursive Functions?
* Helps in breaking complex problems into simpler ones.
* Useful for tree and graph traversal.
* Can be more elegant and readable than iterative solutions.
* Some problems (like Fibonacci, Factorial, Tower of Hanoi) are naturally recursive.

### Example 1: Factorial Calculation
Factorial of `n` is defined as `n!`

$$
n! = n(n - 1)!
$$

where base case is `1! = 1`


```python
def factorial(n):
    if n == 0 or n == 1: # base case
        return 1
    return n * factorial(n-1) # recursive case

factorial(5)
```




    120



### Example 2: Fibonacci Sequence
The Fibonacci sequence is defined as:

$$
F(n) = F(n - 1) + F(n - 2)
$$

where **base cases** are `F(0) = 0` and `F(1) = 1` 


```python
def fibonacci(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    return fibonacci(n - 1) + fibonacci(n - 2) # recursive case

print(fibonacci(6))
    
```

    8
    

### Example 3: Sum of Digits


```python
def sum_of_digits(n):
    if n == 0: # base case
        return 0
    return (n%10) + sum_of_digits(n // 10)

print(sum_of_digits(1234)) # 1 + 2 + 3 + 4
```

    10
    

### Example 4: Reverse a String


```python
def reverse_string(s):
    if len(s) == 0:
        return s
    return s[-1] + reverse_string(s[:-1])

reverse_string("hello")
```




    'olleh'



### Example 5: Tower of Hanoi
The Tower of Hanoi is a famous problem where we move n disks from a source peg to a destination peg using an auxiliary peg, following these rules:

1. Only one disk can be moved at a time.
A disk can only be placed on a larger disk.
All disks start on the source peg.

[⬅ Back to Function](../Functions.md)
