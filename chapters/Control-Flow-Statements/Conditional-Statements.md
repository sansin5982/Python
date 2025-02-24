### 1. Conditional Statements
#### What are Conditional Statements?

Conditional statements in Python allow a program to make decisions based on conditions. They help in controlling the flow of the program by executing different blocks of code depending on whether a condition is **True** or **False**.

#### Why do we need Conditional Statements?

Conditional statements are necessary to make programs dynamic and interactive. They enable a program to respond differently to different inputs and conditions, making them essential in decision-making processes.

### The `input()` Function

Before we move to conditional statements, let's discuss the input() function. This function allows the user to enter values while the program is running.

#### Example


```python
name = input("Enter your name: ")
print("Hello,", name)
# input() takes input from the user.
# The entered value is stored in the variable name.
# The program then prints a greeting using the entered name.
```

    Enter your name: Python
    Hello, Python
    

### Using `if` Statement

The `if` statement checks if a condition is True and executes the corresponding block of code

#### Examples:


```python
age = int(input("Enter your age: "))
if age >= 18:
    print("You are eligible to vote.")
```

    Enter your age: 48
    You are eligible to vote.
    

#### Explanation:

* The user is asked to enter their age.

* int(input()) converts the input into an integer.

* The if condition checks if the age is greater than or equal to 18.

* If True, it prints "You are eligible to vote." If False, nothing happens.

### Using if-else Statement

The `if-else` statement allows us to execute one block of code if the condition is True and another block if the condition is False.


```python
age = int(input("Enter your age: "))
if age >= 18:
    print("You are eligible to vote.")
else:
    print("You are not eligible to vote.")
```

    Enter your age: 25
    You are eligible to vote.
    

#### Explanation:

* The user enters their age.

* If age >= 18, the program prints "You are eligible to vote."

* Otherwise, the program prints "You are not eligible to vote."

### Using if-elif-else Statement

The `if-elif-else` statement is used when we have multiple conditions to check.


```python
marks = int(input("Enter your marks: "))
if marks >= 90:
    print("Grade: A")
elif marks >= 75:
    print("Grade: B")
elif marks >= 60:
    print("Grade: C")
else:
    print("Grade: D")
```

    Enter your marks: 55
    Grade: D
    

#### Explanation:

* The user inputs their marks.

* The program checks the marks against multiple conditions:

    * marks >= 90: Prints "Grade: A".

    * marks >= 75: Prints "Grade: B".

    * marks >= 60: Prints "Grade: C".

    * If none of the above conditions are met, it prints "Grade: D".

#### Q1. Write a Python program that takes two integer variables, x and y, and prints:

* "x is greater than y" if a is greater than b.
* "x and y are equal" if x is equal to y.
* "y is greater than x" if y is greater than x.


```python
x = 10
y = 20
if x > y:
    print("x is greater than y")
elif x == y:
    print("x and y are equal")
else:
    print("y is greater than x")
```

    y is greater than x
    

#### Q2. Write a Python program that takes a student's score as input and assigns a grade based on the following conditions:

* "A" if the score is 90 or above
* "B" if the score is 80 or above but less than 90
* "C" if the score is 70 or above but less than 80
* "D" if the score is 60 or above but less than 70
* "F" if the score is below 60


```python
score = 85
if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"
print(f"Your grade is {grade}")
```

    Your grade is B
    


```python

```
