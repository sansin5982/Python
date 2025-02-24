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


```python

```
