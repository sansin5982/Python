# `__init__`

In Python classes, `__init__` is called a constructor.

> Think of `__init__` as the **setup function** or **welcoming ceremony** that runs **automatically** every time you create a new object.

It **initializes** (i.e., sets up) the object with some starting information — like name, age, balance, color, etc.

#### Analogy 1: New Phone Setup
When you buy a **new phone**, what happens first?

* You **set the language**

* You **add your name**

* You **connect to Wi-Fi**

* You **choose a ringtone**

This is the **initial setup process** — it happens once, right when you start the phone for the **first time**.

That’s exactly what `__init__` does for an object — it runs once at the beginning to **initialize** it with values.


#### Analogy 2: School Admission
When a student joins a school:

* Name is recorded

* Age is noted

* Class is assigned

* Roll number is given

This all happens during the **admission process** — it only happens once per student.

In programming:

* `Student` is the class

* `Sandeep` is an object (a specific student)

* `__init__` is the **admission desk** setting up that student’s details

#### What does __init__ actually do?
1. It runs **automatically** when an object is created

2. It takes **initial values** and stores them as **attributes**

3. It helps every object start with its **own personalized data**

#### Table
| Concept    | Real-Life Equivalent                         | OOP Meaning                                     |
| ---------- | -------------------------------------------- | ----------------------------------------------- |
| `__init__` | Setup process / Admission / First-time setup | Initializes object attributes when it's created |
| Attributes | Name, Age, Roll Number, etc.                 | Stored info like `name`, `age`, `balance`       |
| Object     | A real student or phone                      | An instance created from a class                |


> Without `__init__`, every object would be born empty, with no data.

It’s like creating a phone with no number, no language, no apps — completely unusable.


```python
class Customer:
    def __init__(self, name):
        self.name = name # create the .name attribute and set it to name parameter
        print("The __init__ method was called")
```


```python
cust = Customer("Sandeep Kumar Singh") # __init__ is simplicitly called
print(cust.name)
```

    The __init__ method was called
    Sandeep Kumar Singh
    


```python
class Customer:
    def __init__(self, name, balance):
        self.name = name
        self.balance = balance # balance attribute added
        print("The __init__ method was called")
```


```python
cust = Customer("Sandeep Kumar Singh", 5000)
print(cust.name)
print(cust.balance)
```

    The __init__ method was called
    Sandeep Kumar Singh
    5000
    


```python
# Setting a default value for balance
class Customer:
    def __init__(self, name, balance = 0): # set default value for balance
        self.name = name
        self.balance = balance
        print("The __init__ method was called")

cust = Customer("Sandeep Kumar Singh") # do not specify balance explicitly
print(cust.name)
print(cust.balance)
```

    The __init__ method was called
    Sandeep Kumar Singh
    0
    

* There are two way to define attributes:
    * Attributes in methods
    * Atrributes in constructor

* We can define all attributes together in the constructor
* If possible try to avoid defining attributes outside the constructor

* easier to know all the attributes
* attributes are created when the object is created
* more usable and maintainable code

### Best practice
- 1. Initialize attributes in `__init__()`
- 2. Naming: `CamelCase` for class, `lower_snake_case` for functions and attributes
- 3. `self` is `self`
- 4. Use docstrings
