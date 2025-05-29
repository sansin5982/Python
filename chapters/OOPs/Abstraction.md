# Abstraction
**Showing only the necessary details** and **hiding the internal complexity** from the user.

We use it every day — without even realizing it!

#### Analogy 1: Driving a Car
When we drive a car:
* We use the steering wheel, accelerator, and brake
* But we don’t need to know how the engine, gearbox, or fuel injection works

That’s **abstraction**:
* We’re given a simple interface (pedals, wheel)
* The internal workings are hidden

### Abstraction in Python: Why Do We Use It?
* To **hide unnecessary details**

* To **create a blueprint** that forces certain behavior in all subclasses

* To **organize code better** for large systems

#### Example: Payment System
Imagine we are building an app where users can pay using:

* Credit Card

* PayPal

* UPI

We want all payment types to follow the **same rule**:

> They must have a method called `make_payment()`

But each payment system will implement that method **differently**.

### Basic Abstract Class Structure
In Python, abstraction is implemented using the `abc` module.


```python
from abc import ABC, abstractmethod
```

* ABC means **Abstract Base Class**

* `@abstractmethod` means a **method that must be implemented** in the child class

### Create an Abstract Base Class


```python
from abc import ABC, abstractmethod

class Payment(ABC):  # Abstract class

    @abstractmethod
    def make_payment(self, amount):
        pass  # no implementation here
```

#### What this does:
* `Payment` is a blueprint

* It says: “**Any subclass MUST have a** `make_payment()` method”

* But it doesn’t define `how` that method works

### Create Subclasses that Implement the Method


```python
class CreditCard(Payment):
    def make_payment(self, amount):
        print("Paid", amount, "using Credit Card")

class PayPal(Payment):
    def make_payment(self, amount):
        print("Paid", amount, "using PayPal")
```

### Use the Subclasses


```python
c = CreditCard()
c.make_payment(500)

p = PayPal()
p.make_payment(800)
```

    Paid 500 using Credit Card
    Paid 800 using PayPal
    

### What if a subclass doesn’t implement make_payment()?


```python
class UPI(Payment):
    pass

u = UPI()  # ❌ ERROR: Can't instantiate
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    ~\AppData\Local\Temp\ipykernel_18240\3535876284.py in <module>
          2     pass
          3 
    ----> 4 u = UPI()  # ❌ ERROR: Can't instantiate
    

    TypeError: Can't instantiate abstract class UPI with abstract method make_payment


#### What does this code mean?
1. `UPI` is a subclass of the abstract class `Payment`
2. `Payment` has an abstract method: `make_payment()`
3. `UPI` does **not implement** `make_payment()`

When we try to do:

u = UPI()

* Python throws an error

### Why is this Important?
Because the abstract class `Payment` **promised** that:

> "Any child class **must** define how `make_payment()` works."

By writing:


```python
class UPI(Payment):
    pass
```

You're saying:

> "I want to be a Payment class, but I won’t define how to make a payment."

#### Analogy
Imagine a contract:

* You agree to become a **driver** (i.e., inherit from `Payment`)

* The contract says: "**You must bring your own vehicle**" (i.e., implement `make_payment()`)

Now you show up with **no vehicle** (`pass`):

You can’t start the job → Python refuses to create the object.

#### Correct Version (define the method)


```python
class UPI(Payment):
    def make_payment(self, amount):
        print("Paid", amount, "using UPI")

u = UPI()
u.make_payment(600)
```

    Paid 600 using UPI
    

 Now it works because we’ve fulfilled the contract by implementing the required method.
 
 #### Summary
 
 | Code                       | Meaning                                   | Valid?      |
| -------------------------- | ----------------------------------------- | ----------- |
| `class UPI(Payment): pass` | I’m a Payment but won’t define the method | ❌           |
| `u = UPI()`                | Try to create the object                  | ❌ TypeError |
| Must implement method      | `def make_payment(self, amount): ...`     | ✅           |

#### Table

| Concept             | Description                                          | Example                |
| ------------------- | ---------------------------------------------------- | ---------------------- |
| **Abstraction**     | Hides unnecessary details, shows only required parts | Car dashboard          |
| **Abstract Class**  | Blueprint with abstract methods                      | `Payment(ABC)`         |
| **Abstract Method** | Declared but not defined method                      | `@abstractmethod`      |
| **Child Class**     | Must define all abstract methods or throw error      | `CreditCard`, `PayPal` |

* Abstraction makes our code cleaner, more consistent, and enforces rules.

* We focus on what needs to be done, not how it's done internally.
