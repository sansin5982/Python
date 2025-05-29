# Object and Class

## Object


**`Object = State + Behavior`**

* An object may be a customer's phone number and email associated and **behaviors** like place, order and cancel order.

* The distinctive feature of OOPs is that **state and behavior are bundled together**. Instead of thinking of customer data separately from customer actions, we think of them as one unit representing a customer. This is called **Encapsulation**.
* **Encapsulation** - bundling data with code operating on it.

## Class
* Blueprint for objects outlining possible states and behaviors that every object of a certain type could have.
* For example: every customer will have phone number and email, and will be able to place and cancel orders. We just defined a class.
* Then a specific customer object is just a relaization of this with particular state values.

### Objects in python
* Everything in python is an object
* Every object has a class
* Use `type()` to find the class

|Object|Class|
|---|---|
|`5`|`int`|
|`"Hello"`|`str`|
|`pd.DataFrame()`|`DataFrame`|
|`np.mean`|`function`|
|...|...|


### Class vs Object — Analogy
#### Class: The Blueprint
Imagine you’re an architect. You design a **blueprint** for a house.
This blueprint describes:
* Number of rooms
* Type of windows
* Size of kitchen
* Placement of doors

But here's the thing:

> We can’t live in the blueprint.
It’s just a design or plan.

That’s what a class is — it’s a **template** or **definition**.

#### Object: The Real House
Now, you take that blueprint and build **actual houses**:
* One in Delhi with red bricks
* One in Mumbai with white paint
* One in Lucknow with a garden

Each house:
* Follows the blueprint (same structure)
* But has **its own features** (color, address, owner)

These real, physical houses are **objects** — created **from the class (blueprint)**.

#### Summary
* **Class = Blueprint** (design)
* **Object = House** (actual thing)


We can make many objects from one class, just like we can build many houses from one blueprint.

## Class anatomy

### A basic class
* `class <name>:` start a class definition
* code inside `class` is indented
* use `pass` to create an **"empty"** class


```python
class Customer:
    # code for class goes here
    
    pass
```

Even though class is empty, we can already create objects of the class, followed by paranthesis
* use `ClassName()` to create an object of `ClassName`.


```python
c1 = Customer()
c2 = Customer()
```

* Here, c1 and c2 are two different objects of the empty class Customer.
* We want to create objects that actually store data and operate on it -- in other words have attributes and methods.


```python
class Customer:
    
    def identify(self, name):
        print("I am Customer " + name)
```

* method definition = function definition within class
* **use `self` as the 1st argument in method definition** followed by other


```python
cust = Customer()
cust.identify("Sandeep") # ignore self when calling method on an object
```

    I am Customer Sandeep
    
