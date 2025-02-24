### Loops in python

#### Why are Loops Important?

Loops allow us to execute a block of code multiple times without rewriting it. This is useful when performing repetitive tasks, iterating over sequences, or processing data efficiently.

#### Difference Between `for` and `while` Loops

* **`for` loop**: Used when the number of iterations is known or when iterating over sequences.

* **`while` loop**: Used when the number of iterations is not known and depends on a condition being True.

### The `for` Loop in Python

The for loop is used for iterating over a sequence (like a list, tuple, dictionary, or string) or for running a loop a specific number of times using the `range()` function.

#### The `range()` Function

The `range()` function generates a sequence of numbers and is commonly used in loops.


```python
# syntax
range(start, stop, step)
```

* start: The starting number (default is 0).

* stop: The end number (not included in the range).

* step: The increment (default is 1).

#### Example


```python
for i in range(5):
    print(i)
```

    0
    1
    2
    3
    4
    

#### Explanation:

* range(5) generates numbers from 0 to 4 (5 is not included).

* The loop runs 5 times, printing values from 0 to 4.

* Here i is iteration. Conventionally we use `i`, but we can use any world making sense. Such as `ran`, `Var`, etc


```python
# using list as an example
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

    apple
    banana
    cherry
    

#### Explanation:

* The loop iterates through each element in the list.

* Each fruit name is printed on a new line.


```python
for i in range(2, 10, 2):
    print(i)
```

    2
    4
    6
    8
    


```python
for letter in "Python": # here we used letter rather than i
    print(letter)
```

    P
    y
    t
    h
    o
    n
    


```python
# Using dictionary as an example
student_scores = {"Alice": 90, "Bob": 85, "Charlie": 92}
for name, score in student_scores.items():
    print(f"{name}: {score}")
```

    Alice: 90
    Bob: 85
    Charlie: 92
    

* `.items()` is used to iterate over key-value pairs in the dictionary.

* Both the name and score are printed.

#### List Comprehension with for Loop


```python
squares = [x**2 for x in range(1, 6)]
print(squares)
```

    [1, 4, 9, 16, 25]
    

#### Explanation:

* A compact way to generate a list of squares.

* x**2 computes the square of each number from 1 to 5.

####  Nested for Loop

A nested loop means a loop inside another loop. This is useful when working with multi-dimensional data, li


```python
for i in range(3):
    for j in range(2):
        print(f"i: {i}, j: {j}")
```

    i: 0, j: 0
    i: 0, j: 1
    i: 1, j: 0
    i: 1, j: 1
    i: 2, j: 0
    i: 2, j: 1
    

#### Explanation:

* The outer loop runs 3 times (i varies from 0 to 2).

* The inner loop runs 2 times (j varies from 0 to 1) for each iteration of i.

* This results in a total of 3 × 2 = 6 iterations.


```python
for i in range(2, 11):
    for j in range(1, 11):
        print(i * j, end="-----")
    print()
```

    2-----4-----6-----8-----10-----12-----14-----16-----18-----20-----
    3-----6-----9-----12-----15-----18-----21-----24-----27-----30-----
    4-----8-----12-----16-----20-----24-----28-----32-----36-----40-----
    5-----10-----15-----20-----25-----30-----35-----40-----45-----50-----
    6-----12-----18-----24-----30-----36-----42-----48-----54-----60-----
    7-----14-----21-----28-----35-----42-----49-----56-----63-----70-----
    8-----16-----24-----32-----40-----48-----56-----64-----72-----80-----
    9-----18-----27-----36-----45-----54-----63-----72-----81-----90-----
    10-----20-----30-----40-----50-----60-----70-----80-----90-----100-----
    

#### Explanation:

* The outer loop iterates from 1 to 5.

* The inner loop multiplies i by j.

* end=" " ensures numbers are printed on the same line.

* print() moves to a new line after each row.

### While loop
A `while` loop executes a block of code as long as a specified condition is True.


```python
count = 0
while count < 5:
    print(count)
    count += 1
```

    0
    1
    2
    3
    4
    

#### Explanation:

* The loop runs while count < 5.

* count starts at 0 and increases by 1 in each iteration.

* The loop stops when count reaches 5.


```python
# Using while with User Input
password = "python123"
user_input = ""
while user_input != password:
    user_input = input("Enter password: ")
print("Access granted!")
```

    Enter password: python123
    Access granted!
    

#### Explanation:

* The loop runs until the correct password is entered.

* The user is repeatedly asked to enter a password.

* Once the correct password is entered, the loop stops.

#### Nested while Loops


```python
i = 1
while i <= 3:
    j = 1
    while j <= 2:
        print(f"i: {i}, j: {j}")
        j += 1
    i += 1
```

    i: 1, j: 1
    i: 1, j: 2
    i: 2, j: 1
    i: 2, j: 2
    i: 3, j: 1
    i: 3, j: 2
    

#### Explanation:

* The outer loop runs for i values from 1 to 3.

* The inner loop runs for j values from 1 to 2 for each i.

* The total number of iterations is 3 × 2 = 6.

### Control Transfer Statements

### Break Statement
The `break` statement is used to exit a loop when a certain condition is met.


```python
for i in range(10):
    if i == 5:
        break
    print(i)
```

    0
    1
    2
    3
    4
    


```python
# Using while with break Statement
num = 1
while num <= 10:
    if num == 5:
        break
    print(num)
    num += 1
```

    1
    2
    3
    4
    

#### Explanation:

* The loop prints numbers from 1 to 4.

* When num reaches 5, the break statement terminates the loop immediately.

### Continue Statement
The `continue` statement is used to skip the rest of the code inside the loop for the current iteration and move to the next iteration.


```python
for i in range(5):
    if i == 2:
        continue
    print(i)
```

    0
    1
    3
    4
    


```python
# Using while with continue Statement
num = 0
while num < 10:
    num += 1
    if num % 2 == 0:
        continue
    print(num)
```

    1
    3
    5
    7
    9
    

#### Explanation:

* The loop runs from 1 to 10.

* If num is even, the continue statement skips printing and moves to the next iteration.

* Only odd numbers are printed.

### Pass statement
The `pass` statement is a placeholder that does nothing. It is used when a statement is syntactically required but no action is needed.


```python
for i in range(10):
    if i == 5:
        pass
    print(i)
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    


```python
# Using while with pass Statement
num = 1
while num <= 10:
    if num == 5:
        pass
    print(num)
    num += 1
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    

[⬅ Back to Home](../index.md)
