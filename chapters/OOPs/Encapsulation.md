# Encapsulation

**Encapsulation** means **bundling** the data (attributes) and the actions (methods) together inside an object — and controlling who can access or change that data.

> Think of it as putting sensitive information **inside a locker** and giving access only through a **key** (method).

#### Analogy: ATM Machine
* The **ATM machine** is an object.
* You **can’t directly touch the money inside** the machine.
* Instead, you **interact** through buttons like "Withdraw", "Check Balance".

So:

* **Money inside ATM** = sensitive data (attribute)

* **Buttons** = methods to access that data

* **Encapsulation** = hiding the data and exposing only safe, controlled methods




```python
class Person:
    def __init__(self, name):
        self.name = name  # attribute

    def say_hello(self):  # method
        print("Hello, my name is", self.name)

# Create objects
p1 = Person("Virat")
p2 = Person("Rohit")

# Use method
p1.say_hello()   
p2.say_hello()   
```

    Hello, my name is Virat
    Hello, my name is Rohit
    

#### What’s Happening?
* `Person` → is the **class** (blueprint)

* `p1`, `p2` → are **objects** created from that class

* `name` → is an **attribute** (stored data)

* `say_hello()` → is a **method** (an action)

The `self.name` means **“this object's** name”.

> **Encapsulation = bundling data + behavior into one unit (object)**

* `self.name` is the **data** (state of the object)

* `say_hello()` is the **behavior** (action)

Together, they are **wrapped inside** the `Person` object.

#### Think of a smartwatch:

* It has **data** like steps, heart rate (attributes)

* It has **functions** like display time, measure steps (methods)

* All these things are built **into the same object** — the watch.

That’s encapsulation:

> Putting everything about a person (name + behavior) into **one container** — the object.

## Public, Private, Protected Attributes  (`_attr`, `__attr`)

| Visibility | Syntax   | Who Can Access It?                              |
| ---------- | -------- | ----------------------------------------------- |
| Public     | `name`   | Anyone                                          |
| Protected  | `_name`  | Meant to be used *within* the class or subclass |
| Private    | `__name` | Not directly accessible from outside            |


#### Analogy: Smartphone

| Attribute Type | Real-world Example              | Access                                      |
| -------------- | ------------------------------- | ------------------------------------------- |
| Public         | Phone Color (visible to anyone) | Anyone can see                              |
| Protected      | SIM card inside the phone       | You can remove it carefully if you know how |
| Private        | Password to unlock the phone    | Only you know it                            |

> Python doesn't **strictly enforce** these rules like Java/C++, but it encourages them using naming conventions.



### Public Attribute

#### Analogy: A person's shirt
You can see someone's shirt color — it's **visible to everyone**.


```python
# Public
class Person:
    def __init__(self, name):
        self.name = name  # Public attribute

p1 = Person("Sandeep")
print(p1.name)  # Accessible from outside

```

    Sandeep
    

#### Key Point:
* `self.name` is public.
* Anyone can read or modify it from outside.

### Protected Attribute – Internal Use (with a hint of privacy)
#### Analogy: A person’s email ID
We usually don’t show our email to everyone, but it's not a secret for your team or family. So it's meant for limited access.


```python
class Person:
    def __init__(self, name, email):
        self.name = name
        self._email = email  # Protected attribute (single underscore)

p1 = Person("Sandeep", "sandeep@example.com")
print(p1._email)  # ⚠️ Possible, but not recommended
```

    sandeep@example.com
    

#### Key Point:
* _email is **conventionally** protected.

* We **can** access it, but you shouldn’t unless you're working inside the class or subclass.

### Private Attribute – Strictly Hidden

#### Analogy: A person’s bank PIN
You don't share your ATM PIN with anyone. It's fully private.


```python
class Person:
    def __init__(self, name, pin):
        self.name = name
        self.__pin = pin  # Private attribute (double underscore)

p1 = Person("Sandeep", 1234)
# print(p1.__pin)  # ❌ Will cause an error
p1
```




    <__main__.Person at 0x141568f2490>



#### Accessing Private Attribute (Not Recommended, but Possible)


```python
print(p1._Person__pin)  # ✅ Name mangling trick (used for special cases)
```

    1234
    

#### Key Point:
* __pin is private.

* Can't be accessed directly.

* Python internally renames it (_ClassName__attribute) for protection.

#### Table

| Type      | Syntax   | Access Level              | Example Attribute | Analogy     |
| --------- | -------- | ------------------------- | ----------------- | ----------- |
| Public    | `name`   | Fully accessible          | `self.name`       | Shirt color |
| Protected | `_email` | Intended for internal use | `self._email`     | Email ID    |
| Private   | `__pin`  | Hidden from outside       | `self.__pin`      | ATM PIN     |


## Getter and Setter Methods

Since private data is **not directly accessible**, we use methods to:

### Getter
A **getter** is a method used to **safely access the value** of a private attribute.
Since private attributes **can’t be accessed directly**, getters act like a **"window"** through which you can see the value.

* **Get** the value → getter

#### Analogy: Checking Your Bank Balance
You **can’t open the vault** to see your money, but you can go to an ATM and press "Check Balance".
The machine shows you the balance — that’s a **getter**.




```python
class BankAccount:
    def __init__(self, name, balance):
        self.name = name
        self.__balance = balance  # Private attribute

    def get_balance(self):  # Getter method
        return self.__balance

# Create an object
acc = BankAccount("Sandeep", 5000)

# Try to access balance directly
# print(acc.__balance)  # Error: private attribute

# Use getter method
print("Account Balance:", acc.get_balance()) 
```

    Account Balance: 5000
    

#### Why Use a Getter?
* We can access **private data safely**

* You can **control how the data is shown** (e.g., round off, format)

* It’s part of **encapsulation**: only expose what’s needed

#### Summary:

| Concept           | Action                       | Example             |
| ----------------- | ---------------------------- | ------------------- |
| Private Attribute | Hidden from outside          | `self.__balance`    |
| Getter            | Method to view that value    | `get_balance()`     |
| Analogy           | ATM’s "Check Balance" option | Shows amount safely |


### Setter

A **setter** is a method used to **safely update the value** of a **private attribute**.

> Since private data can’t be changed directly, a setter lets us **control how** and **when** it gets updated.

#### Analogy: Depositing Money in a Bank
You **can’t go into the vault** to add money yourself.
You use the **deposit** form, and a **bank employee** updates your account.
That form is like a **setter** — it updates your balance safely.

* **Set** the value → setter

#### Analogy: School Report Card
* The report card is **private** (not handed to just anyone).
* Only the **teacher** can:
    * View your grade **(getter)**
    * Update your grade **(setter)**

> So you don’t get to touch the real data. You **ask** for it or **request a change** through trusted **methods**.



```python
class BankAccount:
    def __init__(self, name, balance):
        self.name = name
        self.__balance = balance  # Private attribute

    def get_balance(self):  # Getter
        return self.__balance

    def set_balance(self, amount):  # Setter
        if amount >= 0:
            self.__balance = amount
        else:
            print("Balance cannot be negative!")

# Create an object
acc = BankAccount("Sandeep", 5000)

# Use getter
print("Initial Balance:", acc.get_balance())  # Output: 5000

# Use setter to update balance
acc.set_balance(7000)
print("Updated Balance:", acc.get_balance())  # Output: 7000

# Try invalid value
acc.set_balance(-300)  # Output: Balance cannot be negative!
```

    Initial Balance: 5000
    Updated Balance: 7000
    Balance cannot be negative!
    

#### Why Use a Setter?
* You **control what values** are allowed (e.g., no negative balance)

* You **prevent errors or corruption**

* You enforce **rules or logic** when updating data

#### Table

| Concept           | Action                        | Python Method   | Real-Life Analogy         |
| ----------------- | ----------------------------- | --------------- | ------------------------- |
| Getter            | Access private data           | `get_balance()` | Check balance on ATM      |
| Setter            | Update private data           | `set_balance()` | Fill deposit form at bank |
| Private Attribute | Hidden data inside the object | `__balance`     | Actual money inside vault |



## @property Decorator
#### Why use it?
Sometimes, we want to **access private data like an attribute**, but still **protect it**.

Python’s `@property` lets us do this:

* It lets you call a method like it’s a variable

* Looks simple like: `person.age`

* But actually calls a getter behind the scenes

#### Analogy: Automatic Door
Imagine a hotel room with an **automatic door**:

* When you walk toward it, it opens.

* You didn’t press any button, but **something happened behind the scenes**.

That's what `@property` does:

> You **read/write** an attribute, but Python runs a **function quietly in the background**.

* Instead of calling `get_balance()` or `set_balance()`, we can write:


```python
acc.balance       # acts like a variable
acc.balance = 7000  # updates using setter
```


```python
class BankAccount:
    def __init__(self, name, balance):
        self.name = name
        self.__balance = balance  # private attribute

    @property
    def balance(self):  # Getter
        return self.__balance

    @balance.setter
    def balance(self, amount):  # Setter
        if amount >= 0:
            self.__balance = amount
        else:
            print("Balance cannot be negative!")

# Create object
acc = BankAccount("Sandeep", 5000)

# Access like a variable (but it's using the getter)
print("Initial Balance:", acc.balance)  

# Update like a variable (but it's using the setter)
acc.balance = 8000
print("Updated Balance:", acc.balance)

# Try invalid update
acc.balance = -1000  #  Will print a warning
```

    Initial Balance: 5000
    Updated Balance: 8000
    Balance cannot be negative!
    

| Code                 | What Python Did Internally        |
| -------------------- | --------------------------------- |
| `acc.balance`        | Called the `balance()` **getter** |
| `acc.balance = 8000` | Called the `balance()` **setter** |


#### Summary Table

| Concept             | What It Means                          | Layman Example                         |
| ------------------- | -------------------------------------- | -------------------------------------- |
| **Encapsulation**       | Data + behavior bundled in one place   | ATM: Money + buttons                   |
| **Public Attribute**    | Can be accessed by anyone              | Phone color                            |
| **Protected Attribute** | Semi-private, used in subclasses       | SIM card                               |
| **Private Attribute**   | Strictly hidden, accessed via methods  | Phone password                         |
| **Getter Method**       | Retrieve private data                  | “Check Balance” on ATM                 |
| **Setter Method**       | Change private data                    | “Deposit” on ATM                       |
| **`@property`**         | Looks like attribute, acts like method | Automatic door that runs in background |



```python

```
