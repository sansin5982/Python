# Self

In Python, self is a **reference to the current object**. It’s how an object refers to **itself** when accessing its own attributes or methods inside a class.

> Think of self as **"me"** or **"myself"** in the real world.

#### Analogy: A Person Talking About Themselves
Imagine I am a person introducing myself:

> "Hi, my name is **Sandeep**. I am **35 years old**, and I live in **Lucknow**."

* I used words like "**my** name", "**I** am", "**I** live"

We were referring to **our own attributes**

In Python classes, objects do the same using **`self`**.

#### Analogy: Blueprint for a Person
Suppose we have a class `Person`. Every person (object) has a name and age.

When the object talks about its own:

* `name`, it uses `self.name`

* `age`, it uses `self.age`

So `self` allows each object to **access its own data** and **perform its own actions**.

#### Why is self important?
* Each object needs to keep track of its **own data**.

* When a method is called, `self` ensures the method works on the `correct object`.

* Without `self`, we wouldn’t know **which object’s data** we're working with.

#### Juice Glass Analogy
Imagine a **blueprint for a glass of juice**.
Each **glass (object) can have:

* Different flavors

* Different quantities

When a glass needs to describe itself:

> "I have 300 ml of orange juice."
> It’s referring to its own flavor and amount — not someone else’s.

#### Summary

| Term        | Real-world Meaning | OOP Meaning                  |
| ----------- | ------------------ | ---------------------------- |
| `self`      | "Me" / "Myself"    | Refers to the current object |
| `self.name` | "My name"          | The object’s name attribute  |
| `self.age`  | "My age"           | The object’s age attribute   |



```python
self.flavor = "orange"
self.quantity = 300
```


```python
class Customer:
    # set the name attribute of an object to new_name
    def set_name(self, new_name):
        # create an attribute by assigning a value
        self.name = new_name # <--- will create .name when set_name is called
```


```python
cust = Customer()    # <--- .name doesn't exists here yet
cust.set_name("Sandeep Kumar Singh") # <--- .name is and set to "Sandeep Kumar Singh"
print(cust.name)
```

    Sandeep Kumar Singh
    


```python
# New version
class Customer:
    def set_name(self, new_name):
        self.name = new_name
        
    # Using .name from the object itself
    def identify(self):
        print("I am Customer" + self.name)        
```
