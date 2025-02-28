## Real World Application of Higher-Order Functions

### Data Processing and cleaning
#### Scenario: Normalizing Text Data


```python
# Before using text data for NLP tasks, we often need to clean and normalize it.
data = ["Hello", "WORLD", "Python ", " is awesome!"]
# issue is spaces and unnecessary upper case

normalized_data = list(map(lambda x: x.strip().lower(), data))
print(normalized_data)
```

    ['hello', 'world', 'python', 'is awesome!']
    

* `map()` is used to apply multiple transformations to each string.
* This is useful for preprocessing text for machine learning or databases.

### Filtering Data from a Large Dataset 
#### Extracting Active Users
Imagine you have a list of users with their status and need to extract only active users.


```python
users = [
    {"name": "Alice", "active": True},
    {"name": "Bob", "active": False},
    {"name": "Charlie", "active": True},
]

active_users = list(filter(lambda user: user["active"], users))

print(active_users)
```

    [{'name': 'Alice', 'active': True}, {'name': 'Charlie', 'active': True}]
    

* `filter()` helps select specific data without writing complex loops.

### Financial Calculations
#### Calculating Total Sales from a Transaction List
Businesses often need to calculate total revenue from a list of transactions.


```python
from functools import reduce
sales = [1200, 850, 3000, 4100, 1500]

# compute total revenue
total_revenue = reduce(lambda x, y: x + y, sales)
print(total_revenue)
```

    10650
    

### Sorting Data 
#### Sorting Products by Price
E-commerce platforms often sort products based on price, reviews, or other attributes


```python
products = [
    {"name": "Laptop", "price": 900},
    {"name": "Phone", "price": 600},
    {"name": "Tablet", "price": 400},
]

# sort products by price (ascending)
sorted_products = sorted(products, key=lambda x: x["price"])

print(sorted_products)
```

    [{'name': 'Tablet', 'price': 400}, {'name': 'Phone', 'price': 600}, {'name': 'Laptop', 'price': 900}]
    

* `sorted()` with `lambda` is useful for dynamic sorting.

### Dynamic Function Selection
#### Simple Calculator
You can create a flexible function dispatcher for a calculator.


```python
operations = {
    "add": lambda x, y: x + y,
    "sub": lambda x, y: x - y,
    "mul": lambda x, y: x * y,
    "div": lambda x, y: x / y if y != 0 else "Error: Division by zero",
}

# select an operation dynamically
operation = "mul"
result = operations[operation](10, 5)
print(result)
```

    50
    

* This approach is scalable and modular compared to multiple if-else statements.

### Machine Learning – Feature Transformation
#### Converting Categorical Data into Numeric Values
Many ML models require numerical input, so categorical data needs encoding.


```python
categories = ["Male", "Female", "Non-binary", "Male", "Female"]

# convert gender to numerical values
gender_map = {"Male": 0, "Female": 1, "Non-binary": 2}
encoded = list(map(lambda x: gender_map[x], categories))

print(encoded)
```

    [0, 1, 2, 0, 1]
    

* This is a common step in data preprocessing for machine learning.

### Automating Data Extraction 
#### Extracting Emails from a List of Strings
Useful in web scraping and email filtering applications.


```python
data = ["hello@example.com", "contact@company.com", "invalid-email", "user123@gmail.com", "github.com"]

valid_emails = list(filter(lambda x: "@" in x and ".com" in x, data))
print(valid_emails)

```

    ['hello@example.com', 'contact@company.com', 'user123@gmail.com']
    

### Encryption & Security
#### Simple Character Substitution Cipher
Basic encryption technique where characters are shifted by 3 places.


```python
message = "hello"

# Shift characters by 3 places (Caesar Cipher)
encrypted = "".join(map(lambda char: chr (ord(char) + 3), message))
print(encrypted)
```

    khoor
    

### Stock Market Analysis
#### Finding Maximum Stock Price
You have historical stock prices and need to find the highest price.


```python
from functools import reduce

stock_prices = [230, 215, 250, 275, 260, 280]

# find the highest stock price
max_price = reduce(lambda x, y: x if x > y else y, stock_prices)

print(max_price)
```

    280
    

### Image Processing 
#### Converting Pixel Values to Grayscale
Each RGB pixel needs to be converted to grayscale using the formula:
$$
Grayscale = 0.3R + 0.59G + 0.11B
$$


```python
pixels = [(120, 150, 200), (30, 90, 150), (200, 220, 250)]

grey_scale = list(map(lambda p: int(0.3*p[0] + 0.59*p[1] + 0.11*p[2]), pixels))
print(grey_scale)
```

    [146, 78, 217]
    

[⬅ Back to Function](../Functions.md)
