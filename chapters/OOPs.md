# Object-Oriented Programming
Object-Oriented Programming (OOP) is a programming paradigm that organizes software design around objects, rather than functions or logic.

### Key Concepts in OOP

| Concept           | Description                                                                |
| ----------------- | -------------------------------------------------------------------------- |
| **Class**         | A blueprint for creating objects (like a mold for making toy cars).        |
| **Object**        | An instance of a class (like an actual toy car made from the mold).        |
| **Attributes**    | Properties that define the state of an object (like color or size).        |
| **Methods**       | Functions that define behavior of the object (like `drive()` or `honk()`). |
| **Encapsulation** | Bundling of data and methods inside one unit (object).                     |
| **Constructor**   | Special method called when an object is created.                           |


### OOPs example
An example of a class is the class `Dog`. Don't think of it as a specific dog, or our own dog. We're describing what a dog is and can do, in general. Dogs usually have a `name` and `age`; these are instance attributes. Dogs can also `bark`; this is a `method`.

When we talk about a specific dog, we would have an object in programming: an object is an instantiation of a class. This is the basic principle on which object-oriented programming is based. So my dog `Ozzy`, for example, belongs to the `class Dog`. His attributes are `name = 'Ozzy'` and `age = '2'`. A different dog will have different attributes.

## Procedural programming
Procedural Programming is a **step-by-step** approach to programming where the focus is on **functions and procedures**. The data and behavior are **separate**.

> Think of it like a **recipe**: do Step 1, then Step 2, then Step 3.

#### Key Characteristics
* Code is executed **line-by-line** in a sequence.
* Focuses on **functions** and **procedures**.
* Best suited for **simple, linear problems**.
* Easy to understand for **small programs**.

#### Example
Imagine we're writing instructions for **one person** to cook pasta:
1. Boil water
2. Add pasta
3. Stir
4. Drain water
5. Serve

Works great for **one person**.

But what if we have **five people** making five different dishes? We’ll end up repeating steps, and it’s hard to manage changes. That's where OOP comes in!


```python
# Function-based approach to handle a customer
def greet_customer(name):
    print("Hello", name)

def show_balance(balance):
    print("Your balance is:", balance)

# Usage
greet_customer("Sandeep")
show_balance(5000)

```

    Hello Sandeep
    Your balance is: 5000
    

* Each function works independently.
* Data (`name`, `balance`) is passed manually each time.
* No bundling of data + behavior.

## Object-oriented programming
* Code as interactions of objects
* Great for building frameworks and tools
* Maintainable and reusable code
* Fundamental concepts of OOPs are **objects** and **class**

OOP is a paradigm where **code is organized around objects** — units that **combine data and behavior**.

> Instead of writing instructions for each action, we create models (classes) for entities (like a Customer) and then **create objects** from those models.

### Key Characteristics
* **Objects** encapsulate both data and the functions that operate on the data.
* Code becomes **modular**, **reusable**, and **easier to maintain**.
* Ideal for large and complex programs (e.g., web apps, games, frameworks).

#### Example
Let’s go back to the cooking scenario:

> We’re running a restaurant. Each chef is like an object. Every chef knows how to:
* Boil water
* Add ingredients
* Serve

We don’t write separate instructions every time. We just create **Chef objects**, and they handle the cooking.




```python
class Customer:
    def __init__(self, name, balance):
        self.name = name
        self.balance = balance

    def greet(self):
        print("Hello", self.name)

    def show_balance(self):
        print("Your balance is:", self.balance)

# Create customer objects
cust1 = Customer("Sandeep", 5000)
cust2 = Customer("Anita", 3000)

cust1.greet()
cust1.show_balance()

cust2.greet()
cust2.show_balance()

```

    Hello Sandeep
    Your balance is: 5000
    Hello Anita
    Your balance is: 3000
    

### Key Benefits of OOP

| Benefit             | Explanation                                                    |
| ------------------- | -------------------------------------------------------------- |
| **Encapsulation**   | Keep related data and behavior bundled inside objects          |
| **Reusability**     | Reuse classes to create multiple objects (e.g., 100 customers) |
| **Maintainability** | Easy to update/extend code (just modify the class definition)  |
| **Scalability**     | Handle complexity easily by modeling real-world entities       |


### Procedural vs OOP: Comparison Table

| Feature            | Procedural Programming              | Object-Oriented Programming                   |
| ------------------ | ----------------------------------- | --------------------------------------------- |
| Focus              | Functions and procedure             | Objects and classes                           |
| Data & Behavior    | Separate                            | Combined in objects                           |
| Reusability        | Limited (repetition common)         | High (create many objects from same class)    |
| Best for           | Small tasks, data analysis, scripts | Large systems, frameworks, reusable libraries |
| Real-world analogy | Step-by-step instruction book       | Blueprints + real-world instances             |
| Flexibility        | Hard to adapt or scale              | Easy to modify and extend                     |

