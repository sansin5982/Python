# OS module
### What is the os Module?
The `os` module in Python provides a **portable way of using operating system-dependent functionality**, such as reading or writing to the file system, handling directories, environment variables, executing shell commands, and interacting with processes.

### Why is `os` Important?
* Cross-platform compatibility (Windows, macOS, Linux)
* Automates file and directory manipulation
* Useful for scripting and DevOps tasks
* Helps build command-line tools
* Interface between Python and the underlying OS


```python
# importing os module
import os
```

## Working with Directories and Paths
#### Get Current Working Directory `os.getcwd()`

Shows where your Python script is currently operating from.


```python
print("Current Directory:", os.getcwd())
```

    Current Directory: C:\Users\hp\PYTHON\Python Github\Modules
    

#### Change Working Directory `os.chdir(path)` 
Switch to a different directory.


```python
os.chdir('C:/Users/\hp\PYTHON')
print("Changed Directory:", os.getcwd())
```

    Changed Directory: C:\Users\hp\PYTHON
    

#### List Files in Directory `os.listdir(path='.')`
Lists all files and folders in the given path (default is current).


```python
files = os.listdir()
print("Files and folders:", files)
```

    Files and folders: ['.ipynb_checkpoints', 'ParentFolder', 'PRACTICE QUESTION', 'Python Github', 'PYTHON NOTES', 'TestFolder']
    

#### `os.mkdir()` and `os.makedirs()`
Create directories; `makedirs()` can create intermediate folders too.


```python
# Create a single folder
os.mkdir('TestFolder')

# Create nested folders
os.makedirs('ParentFolder/ChildFolder')# creating ParentFolder then ChildFolder inside ParentFolder
```

#### `os.rmdir()` and `os.removedirs()`
Delete empty folders.


```python
# Remove empty folder
os.rmdir('TestFolder')

# Remove nested empty folders
os.removedirs('ParentFolder/ChildFolder')
```

#### Rename Files or Folders os.rename(src, dst) 


```python
os.rename('old_file.txt', 'new_file.txt') # renaming old_file.txt into new_file.txt
```

## File Path Manipulations (with os.path)


```python
from os import path
```

#### `os.path.join()`
Builds a platform-independent path.


```python
file_path = os.path.join('folder', 'file.txt')
print(file_path)
```

    folder\file.txt
    

#### `os.path.exists()` and `os.path.isfile()/isdir()`
Check existence or type of path.


```python
print(os.path.exists('folder'))
print(os.path.isfile('data.csv'))
print(os.path.isdir('folder'))
```

    False
    False
    False
    

#### `os.path.basename()` and `os.path.dirname()`
Extract file name or directory from path.


```python
full_path = 'C:/Users/hp/PYTHON/data.csv'
print(os.path.basename(full_path))  
print(os.path.dirname(full_path))   
```

    data.csv
    C:/Users/hp/PYTHON
    

#### Get File Size `os.path.getsize()`
Check file size (bytes).


```python
size = os.path.getsize('new_file.txt')
print("Size in bytes:", size)
```

    Size in bytes: 12
    

## Environment Variables

#### Access System Environment `os.environ` 


```python
print(os.environ['PYTHON'])  # Unix
print(os.environ.get('PATH'))  # Safer
```

#### Set or Modify Variables
Useful in configuration or accessing system paths.


```python
os.environ['MY_ENV_VAR'] = 'TestValue'
print(os.environ['MY_ENV_VAR'])
```

## Running System Commands
#### Execute Shell Commands `os.system()` 


```python
os.system('dir')  # Windows
os.system('ls')   # Unix
```




    1



#### Walking Through Directories – `os.walk()`


```python
for dirpath, dirnames, filenames in os.walk('.'):
    print("Directory:", dirpath)
    print("Sub-directories:", dirnames)
    print("Files:", filenames)
```

    Directory: .
    Sub-directories: ['.ipynb_checkpoints', 'ParentFolder', 'PRACTICE QUESTION', 'Python Github', 'PYTHON NOTES']
    Files: ['new_file.txt']
    Directory: .\.ipynb_checkpoints
    Sub-directories: []
    Files: []
    Directory: .\ParentFolder
    Sub-directories: ['ChildFolder']
    Files: []
    Directory: .\ParentFolder\ChildFolder
    Sub-directories: []
    Files: []
    Directory: .\PRACTICE QUESTION
    Sub-directories: ['.ipynb_checkpoints']
    Files: ['for loop practice question.ipynb', 'Function.ipynb', 'If else question.ipynb', 'RE PRACTICE.ipynb', 'While loop questions.ipynb']
    Directory: .\PRACTICE QUESTION\.ipynb_checkpoints
    Sub-directories: []
    Files: ['for loop practice question-checkpoint.ipynb', 'Function-checkpoint.ipynb', 'If else question-checkpoint.ipynb', 'RE PRACTICE-checkpoint.ipynb', 'While loop questions-checkpoint.ipynb']
    Directory: .\Python Github
    Sub-directories: ['.ipynb_checkpoints', 'Data Structures', 'Functions', 'Libraries', 'Modules']
    Files: ['Conditional-Statements.ipynb', 'Control-Flow-Statements.ipynb', 'Data-Types-Operators.ipynb', 'Data.txt', 'example.txt', 'Exception-Handling.ipynb', 'File_handling.ipynb', 'Introduction.ipynb', 'Loops.ipynb', 'Modules_Libraries.ipynb', 'newfile1.txt', 'sample.csv', 'sample.json', 'String_Manipulation.ipynb', 'Syntax-and-Variable.ipynb']
    Directory: .\Python Github\.ipynb_checkpoints
    Sub-directories: []
    Files: ['Conditional-Statements-checkpoint.ipynb', 'Control-Flow-Statements-checkpoint.ipynb', 'Data-Types-Operators-checkpoint.ipynb', 'Exception-Handling-checkpoint.ipynb', 'File_handling-checkpoint.ipynb', 'Introduction-checkpoint.ipynb', 'Loops-checkpoint.ipynb', 'Modules_Libraries-checkpoint.ipynb', 'String_Manipulation-checkpoint.ipynb', 'Syntax-and-Variable-checkpoint.ipynb']
    Directory: .\Python Github\Data Structures
    Sub-directories: ['.ipynb_checkpoints']
    Files: ['Data-Structure.ipynb', 'Dictionary.ipynb', 'List.ipynb', 'Set.ipynb', 'Tuple.ipynb']
    Directory: .\Python Github\Data Structures\.ipynb_checkpoints
    Sub-directories: []
    Files: ['Data-Structure-checkpoint.ipynb', 'Dictionary-checkpoint.ipynb', 'List-checkpoint.ipynb', 'Set-checkpoint.ipynb', 'Tuple-checkpoint.ipynb']
    Directory: .\Python Github\Functions
    Sub-directories: ['.ipynb_checkpoints']
    Files: ['Built-in-Functions.ipynb', 'Functions.ipynb', 'High-Order-Function.ipynb', 'Lambda-Function.ipynb', 'Real-World-HOF.ipynb', 'Recursive-Functions.ipynb', 'User-Defined-Functions.ipynb']
    Directory: .\Python Github\Functions\.ipynb_checkpoints
    Sub-directories: []
    Files: ['Built-in-Functions-checkpoint.ipynb', 'Functions-checkpoint.ipynb', 'High-Order-Function-checkpoint.ipynb', 'Lambda-Function-checkpoint.ipynb', 'Real-World-HOF-checkpoint.ipynb', 'Recursive-Functions-checkpoint.ipynb', 'User-Defined-Functions-checkpoint.ipynb']
    Directory: .\Python Github\Libraries
    Sub-directories: ['.ipynb_checkpoints']
    Files: ['brighter.png', 'Matplotlib.ipynb', 'mtcars_cleaned.csv', 'my_plot.png', 'NumPy.ipynb', 'NumPY_Random.ipynb', 'Pandas.ipynb', 'reshape.png', 'sales_plot.png', 'Seaborn.ipynb', 'shape.png', 'Vector.png']
    Directory: .\Python Github\Libraries\.ipynb_checkpoints
    Sub-directories: []
    Files: ['Matplotlib-checkpoint.ipynb', 'NumPy-checkpoint.ipynb', 'NumPY_Random-checkpoint.ipynb', 'Pandas-checkpoint.ipynb', 'Seaborn-checkpoint.ipynb']
    Directory: .\Python Github\Modules
    Sub-directories: ['.ipynb_checkpoints']
    Files: ['os.ipynb', 'RegEx.ipynb']
    Directory: .\Python Github\Modules\.ipynb_checkpoints
    Sub-directories: []
    Files: ['os-checkpoint.ipynb', 'RegEx-checkpoint.ipynb']
    Directory: .\PYTHON NOTES
    Sub-directories: ['.ipynb_checkpoints']
    Files: ['Chapter 1 Python Introduction.ipynb', 'Custom functions.ipynb', 'Data Structure.ipynb', 'Dictionaries.ipynb', 'Handling Errors.ipynb', 'In-built-Functions.ipynb', 'Lambda and high order functions.ipynb', 'List.ipynb', 'Modules & Packages.ipynb', 'OOPs.ipynb', 'Operators.ipynb', 'Sets.ipynb', 'Strings.ipynb', 'Tuples.ipynb']
    Directory: .\PYTHON NOTES\.ipynb_checkpoints
    Sub-directories: []
    Files: ['Chapter 1 Python Introduction-checkpoint.ipynb', 'Custom functions-checkpoint.ipynb', 'Data Structure-checkpoint.ipynb', 'Dictionaries-checkpoint.ipynb', 'Handling Errors-checkpoint.ipynb', 'In-built-Functions-checkpoint.ipynb', 'Lambda and high order functions-checkpoint.ipynb', 'List-checkpoint.ipynb', 'Modules & Packages-checkpoint.ipynb', 'OOPs-checkpoint.ipynb', 'Operators-checkpoint.ipynb', 'Sets-checkpoint.ipynb', 'Strings-checkpoint.ipynb', 'Tuples-checkpoint.ipynb']
    

### Practical Applications
Example 1: List all .txt files in a directory


```python
for file in os.listdir():
    if file.endswith('.txt'):
        print(file)
```

    new_file.txt
    

#### Example 2: Move all .csv files to a new folder


```python
source = os.getcwd()
target = os.path.join(source, 'csv_files')
os.makedirs(target, exist_ok=True)

for file in os.listdir(source):
    if file.endswith('.csv'):
        os.rename(file, os.path.join(target, file))
```

### Important Notes
* Use `os.path` or `pathlib` for cross-platform code.
* Be cautious with `os.remove`, `rmdir` — they don’t ask for confirmation.
* Use `os.system()` sparingly; `subprocess` is more powerful and safer.
