# Exception Handling
**Exception handling** is a way to detect, manage, and respond to errors during program execution **without crashing the program**. It helps you control how your program behaves when unexpected situations arise.

## Types of error in Python
Python errors can be broadly classified into two categories:

### 1. Syntax Errors (Compile-Time Errors)
These occur before the program runs, due to incorrect code structure or grammar.


```python
if True
    print("Hello")
```


      File "C:\Users\hp\AppData\Local\Temp\ipykernel_13516\1694349398.py", line 1
        if True
               ^
    SyntaxError: invalid syntax
    


**Explanation**:
* Python expects a colon (`:`) at the end of the `if` statement.
* These errors must be fixed before the code runs.

### 2. Exceptions (Runtime Errors)
These occur **while the program is running**. They are raised when the program encounters something it cannot handle.

### Type Error
* Operation on incompatible data types


```python
"Hello" + 5
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_20736\3719883255.py in <module>
    ----> 1 "Hello" + 5
    

    TypeError: can only concatenate str (not "int") to str


### Value error
* Invalid value passed to a function (like int("abc"))


```python
float("Hello")
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_20736\1727209013.py in <module>
    ----> 1 float("Hello")
    

    ValueError: could not convert string to float: 'Hello'


### Key Error
Accessing a missing dictionary key


```python
# Import pandas package
import pandas as pd

# Create pandas DataFrame
products = pd.DataFrame({"ID": ["ABC1"], "price": [29.99]})

products
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ABC1</td>
      <td>29.99</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Try to access the non-existent "tag" column
products["tag"]
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    ~\anaconda3\lib\site-packages\pandas\core\indexes\base.py in get_loc(self, key, method, tolerance)
       3628             try:
    -> 3629                 return self._engine.get_loc(casted_key)
       3630             except KeyError as err:
    

    ~\anaconda3\lib\site-packages\pandas\_libs\index.pyx in pandas._libs.index.IndexEngine.get_loc()
    

    ~\anaconda3\lib\site-packages\pandas\_libs\index.pyx in pandas._libs.index.IndexEngine.get_loc()
    

    pandas\_libs\hashtable_class_helper.pxi in pandas._libs.hashtable.PyObjectHashTable.get_item()
    

    pandas\_libs\hashtable_class_helper.pxi in pandas._libs.hashtable.PyObjectHashTable.get_item()
    

    KeyError: 'tag'

    
    The above exception was the direct cause of the following exception:
    

    KeyError                                  Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_20736\2351853232.py in <module>
          1 # Try to access the non-existent "tag" column
    ----> 2 products["tag"]
    

    ~\anaconda3\lib\site-packages\pandas\core\frame.py in __getitem__(self, key)
       3503             if self.columns.nlevels > 1:
       3504                 return self._getitem_multilevel(key)
    -> 3505             indexer = self.columns.get_loc(key)
       3506             if is_integer(indexer):
       3507                 indexer = [indexer]
    

    ~\anaconda3\lib\site-packages\pandas\core\indexes\base.py in get_loc(self, key, method, tolerance)
       3629                 return self._engine.get_loc(casted_key)
       3630             except KeyError as err:
    -> 3631                 raise KeyError(key) from err
       3632             except TypeError:
       3633                 # If we have a listlike key, _check_indexing_error will raise
    

    KeyError: 'tag'


### ZeroDivisionError
Dividing a number by zero


```python
10/0
```


    ---------------------------------------------------------------------------

    ZeroDivisionError                         Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_13516\530406163.py in <module>
    ----> 1 10/0
    

    ZeroDivisionError: division by zero


### IndexError
Accessing index out of a list's range


```python
lst = [1,2] 
lst[3]
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_13516\1536589071.py in <module>
          1 lst = [1,2]
    ----> 2 lst[3]
    

    IndexError: list index out of range


### FileNotFoundError
Opening a file that doesn't exist


```python
open("nofile.txt")
```


    ---------------------------------------------------------------------------

    FileNotFoundError                         Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_13516\1781735528.py in <module>
    ----> 1 open("nofile.txt")
    

    FileNotFoundError: [Errno 2] No such file or directory: 'nofile.txt'


### AttributeError
Using a method/attribute that doesn’t exist on an object


```python
"hello".push("!")
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_13516\3856389170.py in <module>
    ----> 1 "hello".push("!")
    

    AttributeError: 'str' object has no attribute 'push'


### ModuleNotFoundError
Module or function can’t be imported


```python
import maths
```


    ---------------------------------------------------------------------------

    ModuleNotFoundError                       Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_13516\1716165428.py in <module>
    ----> 1 import maths
    

    ModuleNotFoundError: No module named 'maths'


### Indentation error


```python
# Incorrect indentation – will raise an IndentationError
def greet():
print("Hello, world!")
```


      File "C:\Users\hp\AppData\Local\Temp\ipykernel_13516\3682147451.py", line 3
        print("Hello, world!")
        ^
    IndentationError: expected an indented block
    


### NameError


```python
# Trying to use a variable that hasn’t been defined
print(score)  # 'score' has not been defined yet
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_13516\2306661418.py in <module>
          1 # Trying to use a variable that hasn’t been defined
    ----> 2 print(score)  # 'score' has not been defined yet
    

    NameError: name 'score' is not defined


### Common Types of Exceptions in Python

| Exception Name       | Description                                                 | Example Code                        | Raised Error                    |
|----------------------|-------------------------------------------------------------|-------------------------------------|----------------------------------|
| `ZeroDivisionError`  | Raised when dividing a number by zero                      | `10 / 0`                            | `ZeroDivisionError: division by zero` |
| `ValueError`         | Raised when a function receives an argument of correct type but inappropriate value | `int("abc")`         | `ValueError: invalid literal for int()` |
| `TypeError`          | Raised when an operation is performed on incompatible types | `"5" + 5`                           | `TypeError: can’t concat str and int` |
| `IndexError`         | Raised when accessing an index that’s out of range          | `lst = [1, 2]; lst[5]`              | `IndexError: list index out of range` |
| `KeyError`           | Raised when accessing a missing key in a dictionary         | `d = {"a":1}; d["b"]`               | `KeyError: 'b'`                 |
| `FileNotFoundError`  | Raised when a file is not found                            | `open("nofile.txt")`               | `FileNotFoundError: No such file or directory` |
| `AttributeError`     | Raised when attribute reference or assignment fails         | `"hello".push("!")`                | `AttributeError: 'str' object has no attribute 'push'` |
| `ImportError`        | Raised when an import fails                                | `import doesnotexist`              | `ImportError: No module named 'doesnotexist'` |
| `ModuleNotFoundError`| A subclass of `ImportError` for non-existing modules       | `import somemodule` (not installed)| `ModuleNotFoundError: No module named 'somemodule'` |
| `NameError`          | Raised when a variable is not defined                      | `print(x)` (x not defined)         | `NameError: name 'x' is not defined` |
| `IndentationError`   | Raised when there’s an error in indentation                | Incorrect indentation               | `IndentationError: unexpected indent` |


### Error hanling
* `except`, `raise`
* Try to anticipate how errors might occur

#### Design thinking
* How might people use our custom function?
* Test these different approaches
* Find what errors occur

#### Where might they go wrong
* Provide more than one argument
* Use the wrong data type

#### Error handling techniques
* Control `if`, `elif`, `else`
* Docstrings

### Basic structure `try` and `except`


```python
try:
    # Code that might raise an error
except ErrorType:
    # Code to handle the error
```

### try-except



```python
try:
    num = int(input("Enter a number: "))
    print(10 / num)
except ZeroDivisionError:
    print("You can't divide by zero!")
except ValueError:
    print("Invalid input! Please enter a number.")
```

    Enter a number: 0
    You can't divide by zero!
    

**Explanation**:
* Code inside `try` is executed.
* If an error occurs, control jumps to the matching `except`.
* You can have multiple `except` blocks for different error types.

### `finally Block`
The finally block is **always executed**, whether an error occurs or not. It’s typically used for **cleanup activities** like closing files or releasing resources.


```python
try:
    f = open("trial.txt", "r")
    content = f.read()
    print(content)
except FileNotFoundError:
    print("File not found.")
finally:
    print("Closing file (if open).")
```

    File not found.
    Closing file (if open).
    

**Explanation**:
* Whether file is found or not, `finally` runs and prints the cleanup message.

### raise
We can manually raise an exception using raise.


```python
age = int(input("Enter your age: "))
if age < 0:
    raise ValueError("Age cannot be negative.")
else:
    print("Your age is:", age)
```

    Enter your age: -15
    


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_13516\3891175787.py in <module>
          1 age = int(input("Enter your age: "))
          2 if age < 0:
    ----> 3     raise ValueError("Age cannot be negative.")
          4 else:
          5     print("Your age is:", age)
    

    ValueError: Age cannot be negative.


### `assert Statement`
* `assert` is used for **debugging**. It tests if a condition is **True**. If not, it raises an **AssertionError**.
#### Syntax
assert condition, "Error message if condition is False"


```python
marks = -70
assert marks >= 0, "Marks cannot be negative"
print("Marks entered:", marks)
```


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_13516\2962238508.py in <module>
          1 marks = -70
    ----> 2 assert marks >= 0, "Marks cannot be negative"
          3 print("Marks entered:", marks)
    

    AssertionError: Marks cannot be negative


### Multiple Exceptions in One Block


```python
try:
    a = int(input("Enter number 1: "))
    b = int(input("Enter number 2: "))
    result = a / b
except (ValueError, ZeroDivisionError) as e:
    print("Error occurred:", e)
else:
    print("Result:", result)
finally:
    print("Program ended.")
```

    Enter number 1: 25
    Enter number 2: "5"
    Error occurred: invalid literal for int() with base 10: '"5"'
    Program ended.
    

**Explanation**:
* Combines multiple exceptions.
* `else` runs **only if** no exception occurred.
* `finally` always runs.
