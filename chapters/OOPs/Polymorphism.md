# Polymorphism

**Polymorphism** means **"many forms"**.

In object-oriented programming, it allows the **same method name** to behave **differently** depending on **which object** is calling it.

#### Analogy: A "Speak" Button
Imagine you press a **"Speak" button** on:

* A **TV** → it reads the news

* A **Toy** → it says “Hello!”

* A **Robot Dog** → it barks

It’s the **same button ("speak")**, but the action is **different for each device**.

> That’s polymorphism — one interface, multiple behaviors depending on the object.

## Types of Polymorphism in Python

### 1. Method Overriding (Runtime Polymorphism)


**Method Overriding** means a **child class redefines a method** that already exists in the **parent class** — same method name, same arguments, but **different behavior**.

#### Analogy:
Imagine a **parent** teaches all children to "introduce" themselves by saying:

> “Hi, I’m a person.”

But the **child** wants to be more specific and says:

> “Hi, I’m a student.”

Both say **"introduce yourself"**, but **the child's version replaces the parent's version**.

That’s **overriding**.

* It is a part of **inhertiance** and **polymorhisms** both 

| Belongs To       | Why                                                                              |
| ---------------- | -------------------------------------------------------------------------------- |
| **Inheritance**  | Because a **child class inherits** a method from the parent class                |
| **Polymorphism** | Because the **same method name** behaves **differently** depending on the object |



```python
class Animal:
    def speak(self):
        print("Animal makes a sound")

class Dog(Animal):
    def speak(self):
        print("Dog barks")

class Cat(Animal):
    def speak(self):
        print("Cat meows")
```

#### Using polymorphism


```python
def animal_sound(animal):
    animal.speak()  # same method, behaves differently

# Create different animal objects
a = Animal()
d = Dog()
c = Cat()

animal_sound(a)  # Animal makes a sound
animal_sound(d)  # Dog barks
animal_sound(c)  # Cat meows
```

    Animal makes a sound
    Dog barks
    Cat meows
    

#### Explanation
* All classes have a method named `speak()`

* The function `animal_sound()` works with **any object**

* It **calls the correct version** of `speak()` based on the **object type**

* That’s polymorphism: **same function name, different behavior**

#### Table 

| Concept           | Description                                  |
| ----------------- | -------------------------------------------- |
| Polymorphism      | One function/method, many behaviors          |
| Method Overriding | Subclass redefines method of parent class    |
| Benefit           | More flexible, reusable, and extensible code |


### 2. Operator Overloading

Polymorphism where **the same operator** behaves **differently** depending on the objects involved.

#### Analogy:
Think of the "+" **sign**:

**2 + 3** → adds numbers

**"Hello"** + **"World"** → joins strings

**[1, 2]** + **[3, 4]** → merges lists

So `+` behaves **differently** depending on the data type — that’s **operator overloading**.


```python
print(2 + 3)            # 5
print("Hi " + "there")  # Hi there
print([1, 2] + [3, 4])  # [1, 2, 3, 4]
```


```python
class Book:
    def __init__(self, pages):
        self.pages = pages

    def __add__(self, other):
        return Book(self.pages + other.pages)

b1 = Book(100)
b2 = Book(150)

b3 = b1 + b2  # Internally calls b1.__add__(b2)
print("Total pages:", b3.pages) 
```

    Total pages: 250
    

Each `+` is doing something different — **but Python handles it automatically** behind the scenes using special methods like `__add__()`.

### 3. Duck Typing

* If it walks like a duck and quacks like a duck, it's a duck.

#### Analogy:
You don't care **what brand** a TV is.
If it has a **remote**, and you can **press 'power'**, you’re good.

In Python:

* You don’t check **types**.

* You just expect the object to **have the required method**.


```python
class Cat:
    def speak(self):
        print("Meow")

class Dog:
    def speak(self):
        print("Bark")

def make_it_speak(animal):
    animal.speak()

# No need to check type!
make_it_speak(Cat())  # Meow
make_it_speak(Dog())  # Bark
```

    Meow
    Bark
    

* No need to check if isinstance(animal, Dog or Cat)
* As long as the object has speak(), it works!
* That’s duck typing: focus on behavior, not type.

#### Table

| Polymorphism Type    | Description                                          | Example                       |
| -------------------- | ---------------------------------------------------- | ----------------------------- |
| Operator Overloading | Same operator, different behavior                    | `+` on int, str, list, object |
| Duck Typing          | Don’t care about type, just behavior (method exists) | `obj.speak()`                 |



### 4. Method Overloading 

**Method Overloading** means having **multiple methods with the same name** but **different parameters**.

It’s a way to **perform similar tasks** using the **same method name**, but with **different inputs**.

#### Analogy: A "Book Ticket" Counter
Imagine you're booking tickets:

* Just **name** → default seat

* Name + **seat choice** → your seat

* Name + seat + **meal preference** → extra option

The same action "book_ticket()" is done — but with different info.

#### Python Doesn’t Support True Method Overloading

####  How Does Python Simulate It?
Python simulates method overloading using:

* **default parameters**

* or `*args` and `**kwargs`


```python
class Ticket:
    def book(self, name, seat="Auto", meal="None"):
        print("Booking for:", name)
        print("Seat:", seat)
        print("Meal:", meal)

# Create object
t = Ticket()

# Call with 1 argument
t.book("Sandeep")

# Call with 2 arguments
t.book("Sandeep", "A5")

# Call with all 3 arguments
t.book("Sandeep", "A5", "Veg")
```

    Booking for: Sandeep
    Seat: Auto
    Meal: None
    Booking for: Sandeep
    Seat: A5
    Meal: None
    Booking for: Sandeep
    Seat: A5
    Meal: Veg
    

####  Alternate Approach: *args


```python
class Calculator:
    def add(self, *args):
        return sum(args)

c = Calculator()
print(c.add(2, 3))           
print(c.add(1, 2, 3, 4))     
```

    5
    10
    

#### What Happened?
* `*args` allows you to send **any number of arguments**
* Inside the method, you handle them accordingly

#### Table

| Concept              | Python Style                      | Real-Life Analogy             |
| -------------------- | --------------------------------- | ----------------------------- |
| Method Overloading   | Same method, different parameters | Book ticket with more details |
| Default Arguments    | `seat="Auto"`                     | Optional information          |
| `*args` / `**kwargs` | Flexible arguments                | Accept any number of options  |



```python

```
