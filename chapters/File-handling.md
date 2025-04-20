# File Handling in Python
File handling allows Python programs to read from and write to files stored on disk.

### Why is File Handling Important?
* Persistent data storage
* Reading external data like .txt, .csv, .json
* Logging, configuration, and report generation
* Data processing in real-world applications

### Types of Files in Python
* **1. Text files**: .txt, .csv, .log, .xml, .json
* **2. Binary files**: Images, audio, video, .exe, etc.

## File Operations in Python

## 🔹 Opening Files with `open()`
`open(file, mode)` is used to open a file.

| Mode | Description |
|------|-------------|
| `'r'` | Read mode (default) |
| `'w'` | Write mode (overwrites file) |
| `'a'` | Append mode |
| `'x'` | Create mode |
| `'b'` | Binary mode |
| `'t'` | Text mode (default) |
| `'+'` | Read and write mode |


```python
# Example: Open file in read mode
f = open('example.txt', 'r')
print(f)
```

    <_io.TextIOWrapper name='example.txt' mode='r' encoding='cp1252'>
    

## Reading Files

### 1. `read()`: Read full content


```python
f = open('example.txt', 'r')
content = f.read()
print(content)
f.close()
```

    This is python class.
    We are learning File handling.
    It is a very important topic.
    

#### Using with statement (Best peactice)


```python
# Read full content using with
with open('example.txt', 'r') as f:
    content = f.read()
    print(content)
f.close()
```

    This is python class.
    We are learning File handling.
    It is a very important topic.
    

### 2. `readline()`: Reads a single line


```python
f = open('example.txt', 'r')
line = f.readline()
print(line)
f.close()
```

    This is python class.
    
    


```python
with open('example.txt', 'r') as f:
    content = f.readline()
    print(content)
f.close()
```

    This is python class.
    
    

### 3. `readlines()`: Reads all lines as a list


```python
f = open('example.txt', 'r')
lines = f.readlines()
print(lines)
f.close()
```

    ['This is python class.\n', 'We are learning File handling.\n', 'It is a very important topic.']
    


```python
with open('example.txt', 'r') as f:
    content = f.readlines()
    print(content)

f.close()
```

    ['This is python class.\n', 'We are learning File handling.\n', 'It is a very important topic.']
    

## Writing to a file
### 1. `write()`: writes a string to the file


```python
f = open('newfile.txt', 'w')
f.write("Hello, this is a new file")
f.close()
```


```python
# Write to a file
with open('newfile1.txt', 'w') as f:
    f.write("This is another new file.\n")
```

### 2. `writelines()`: Writes a list of strings


```python
lines = ["Line 1\n", "Line 2\n"]
f = open('newfile.txt', 'w')
f.writelines(lines)
f.close()
```


```python
with open('newfile1.txt', 'w') as f:
    f.writelines(line)
```

## Appending to a file



```python
f = open('newfile.txt', 'a')
f.write("\nThis is append.")
f.close()
```


```python
# Append to a file
with open('newfile1.txt', 'a') as f:
    f.write("This line is appended.\n")
```

## Closing a file


```python
f.close()
```

## Reading Lines One-by-One


```python
# Read line by line
with open('newfile.txt', 'r') as f:
    for line in f:
        print(line.strip())
```

    Line 1
    Line 2
    
    This is append.
    

## Using `os` and `pathlib` for File Handling


```python
import os

# Check if file exists
if os.path.exists('example.txt'):
    print("File exists")
```

    File exists
    


```python
# Rename a file
os.rename('newfile.txt', 'renamed.txt')
# newfile.txt is renamed as renamed.txt
```


```python
# remove a file
os.remove('renamed.txt')
# renamed.txt is removed
```


```python
os.mkdir('myfolder') # create a folder
```


```python
os.rmdir('myfolder') # remove a folder
```


```python
from pathlib import Path

# Check if file exists
file_path = Path('newfile.txt')
print(file_path.exists())
```

    False
    

### Example: Read & Write Text File


```python
# write
with open("Data.txt", 'w') as f:
    f.write("Python is awesome.\n")
    
# append
with open("Data.txt", 'a') as f:
    f.write("Learn it fast.\n")
    
# read
with open("Data.txt", 'r') as f:
    for line in f:
        print(line.strip())
```

    Python is awesome.
    Learn it fast.
    

## CSV File Handling


```python
import csv

# Writing CSV
with open('sample.csv', 'w', newline='') as f:
    writer = csv.writer(f)
    writer.writerow(['Name', 'Age'])
    writer.writerow(['Alice', 25])

# Reading CSV
with open('sample.csv', 'r') as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)
```

    ['Name', 'Age']
    ['Alice', '25']
    

## JSON File Handling


```python
import json

# Write JSON
data = {"name": "Alice", "age": 25}
with open('sample.json', 'w') as f:
    json.dump(data, f)

# Read JSON
with open('sample.json', 'r') as f:
    content = json.load(f)
    print(content)
```

    {'name': 'Alice', 'age': 25}
    


```python

```
