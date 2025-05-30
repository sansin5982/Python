# Inheritance

**Inheritance** is when a class (child) gets the properties and behaviors of another class (parent).

Analogy: Family Traits
* You inherit your **eye color, height**, or **last name** from our parents.

* In the same way, **a child class** inherits **attributes and methods** from a **parent class**.

## 1. Single Inheritance
* **Single Inheritance** is when **one child** class inherits from one parent class.

In plain terms:

* A child **receives features** or **behavior** from one parent.

* It’s a **one-to-one relationship**.

#### Analogy: Parent and Child
Imagine a **parent** teaches their child:

* How to **ride a bicycle**

* How to read a book

Now the **child**:

* Doesn’t need to learn these things from scratch

* Can already **do them** because they learned from their parent

That’s exactly how **single inheritance** works in programming:

* A **child class** doesn’t have to write everything itself

* It simply **inherits** properties and abilities from **a single parent class**

#### Examples

| Parent    | Child           | What is Inherited         |
| --------- | --------------- | ------------------------- |
| Teacher   | Math Teacher    | Teaching skills           |
| Bird      | Parrot          | Ability to fly, eat, move |
| Appliance | Washing Machine | Electricity use, buttons  |

#### Why Use It?
* To **avoid repeating code or work**

* To make your program more **organized and reusable**

* To build on something that already exists


```python
class Animal:
    def speak(self):
        print("Animal speaks")

class Dog(Animal):  # Dog inherits from Animal
    def bark(self):
        print("Dog barks")

d = Dog()
d.speak()  # Inherited from Animal
d.bark()   # Defined in Dog
```

    Animal speaks
    Dog barks
    

### What Happened?
* `Dog` automatically got `speak()` from `Animal`

* This avoids repeating code

## 2. Multilevel Inheritance

> **Multilevel Inheritance** is when a class inherits from a **parent**, and **that parent also inherited from another parent** — forming a chain.

Think of it like a family tree across three generations:
* **Inheritance happens in a chain**: Grandparent → Parent → Child

#### Analogy: Generational Learning
Let’s say:

1. **Grandfather** knows how to **farm**

2. **Father** learns farming from grandfather and also learns to **drive a tractor**

3. **Son** learns both **farming and tractor driving** from the father

So now the Son:

* Didn’t directly learn from grandfather, but

* **Still has access** to grandfather’s knowledge, **passed down** through the father

> That’s multilevel inheritance — a **chain of knowledge or features passed down** through generations.

#### Example

| Level       | Role     | Skill Inherited             |
| ----------- | -------- | --------------------------- |
| Grandparent | Human    | Can breathe                 |
| Parent      | Employee | Can work                    |
| Child       | Manager  | Can manage + work + breathe |

So the **Manager** can:

* Manage (own skill)

* Work (from parent)

* Breathe (from grandparent)

#### Why Use Multilevel Inheritance?
* To **build on top** of an existing class without rewriting everything

* To create **layers of specialization**

* To represent **hierarchies or real-world chains**


```python
class LivingBeing:
    def breathe(self):
        print("Breathing")

class Animal(LivingBeing):  # Parent
    def move(self):
        print("Moving")

class Dog(Animal):  # Child
    def bark(self):
        print("Barking")

d = Dog()
d.breathe()  # From LivingBeing
d.move()     # From Animal
d.bark()     # From Dog
```

    Breathing
    Moving
    Barking
    

#### What Happened?
* `Dog` inherits from `Animal`, which inherits from LivingBeing

* `Dog` gets **everything from both** parent and grandparent

## 3. Multiple Inheritance
**Multiple Inheritance** is when a class **inherits from more than one parent** class.

In plain words:

* A child class gets **skills or features** from **multiple sources**

#### Analogy: Learning from Mom and Dad
Let’s say:

* **Mother** is a **chef** — she teaches cooking

* **Father** is a **driver** — he teaches driving

* The **Child** learns **both cooking and driving** from mom and dad

So now the **child**:

* Inherits **two different skill sets**

* Doesn’t have to learn them from scratch — just uses what’s passed down

> That’s **multiple inheritance** — the child gets features from **more than one parent**.

#### Table

| Parent 1 | Parent 2 | Child            | What the child inherits       |
| -------- | -------- | ---------------- | ----------------------------- |
| Artist   | Engineer | Product Designer | Creativity + Technical Skills |
| Mother   | Father   | Child            | Cooking + Driving             |
| Keyboard | Mouse    | Hybrid Device    | Typing + Pointing             |


#### What’s Special About It?
* The child combines **different traits** from **multiple sources**

* It makes the child **more capable** or **specialized**

* But if both parents have the **same-named feature**, it can cause **confusion** — Python handles this using something called **Method Resolution Order (MRO)**

#### Why Use Multiple Inheritance?
* To combine features from **different, unrelated classes**

* To create **hybrid roles**

* To build **more powerful objects** by reusing existing parts


```python
class Mother:
    def skills(self):
        print("Cooking")

class Father:
    def skills(self):
        print("Driving")

class Child(Mother, Father):
    pass

c = Child()
c.skills()  # ⚠️ Calls Mother's skills() by default due to method resolution order
```

    Cooking
    

#### What Happened?
* `Child` inherits from both `Mother` and `Father`

* If both have a method with the same name, Python uses the one from **the first parent listed**

## 4. Hierarchical Inheritance

**Hierarchical Inheritance** is when **multiple child classes** inherit from **the same single parent class**.

In simple words:

* **One parent**, but **many children**

* All the children get the **same features** from the **same parent**

#### Analogy: Parent Teaching Multiple Kids
Let’s say:

* A **parent** teaches **basic manners** and **language skills**

* They have **three children**:

    * **Alice** wants to be a doctor

    * **Bob** wants to be an engineer

    * **Cathy** wants to be an artist

Each child:

* Learns **basic life skills** (from the parent)

* Then learns their **own special skills**

That’s hierarchical inheritance:

> All children **inherit shared features** from **one parent**, but each can also have **unique features**.

#### Table

| Parent Class | Child 1     | Child 2        | Child 3        |
| ------------ | ----------- | -------------- | -------------- |
| Vehicle      | Car         | Bike           | Truck          |
| Animal       | Dog         | Cat            | Elephant       |
| Teacher      | MathTeacher | EnglishTeacher | ScienceTeacher |

All the child classes **share common features** (from the parent), like:

* Vehicles can **move**

* Animals can **eat**

* Teachers can **teach**

But each one also has **special behavior**.

#### Why Use Hierarchical Inheritance?
* To share **common logic** across multiple child classes

* To avoid writing the **same code multiple times**

* To build **specific roles** from a **common base class**

#### Summary

| Concept                  | Description                                            |
| ------------------------ | ------------------------------------------------------ |
| Hierarchical Inheritance | One parent → many children                             |
| Purpose                  | Share features across multiple child classes           |
| Analogy                  | One parent teaches different children different things |


#### Analogy:
Let’s say:

* The **Parent class** is `Animal`, which knows how to eat()

* The **Child classes** are:

    * `Dog` → can `bark()`

    * `Cat` → can `meow()`
    
    * `Cow` → can `moo()`

All of them can eat, but each has its own sound.



```python
# Parent class
class Animal:
    def __init__(self, name):
        self.name = name  # attribute initialized using self

    def eat(self):
        print(self.name, "eats food.")

# Child class 1
class Dog(Animal):
    def bark(self):
        print(self.name, "barks.")

# Child class 2
class Cat(Animal):
    def meow(self):
        print(self.name, "meows.")

# Child class 3
class Cow(Animal):
    def moo(self):
        print(self.name, "moos.")
```


```python
# Creating Objects (Instances)
d = Dog("Bruno")     # Object of Dog
c = Cat("Whiskers")  # Object of Cat
cow = Cow("Gauri")   # Object of Cow

```


```python
# Calling Methods
d.eat()    # Inherited from Animal
d.bark()   # Dog-specific method

c.eat()    
c.meow()   

cow.eat()  
cow.moo()

```

    Bruno eats food.
    Bruno barks.
    Whiskers eats food.
    Whiskers meows.
    Gauri eats food.
    Gauri moos.
    

## Hybrid Inheritance

**Hybrid Inheritance** is a combination of **two or more types** of inheritance patterns in one program.

It’s called hybrid because it **mixes**:

* **Single Inheritance**

* **Multilevel Inheritance**

* **Multiple Inheritance**

* **Hierarchical Inheritance**

All of these can appear together in different ways.

#### Analogy: A Mixed-Skills Family Tree
Imagine a family like this:

* **Grandparent** teaches basic survival skills

* **Parent 1 (Engineer)** inherits those and also learns tech stuff

* **Parent 2 (Artist)** also inherits the basics and adds creativity

* **Child** inherits **both** technical and creative skills from **both parents**

Now this child:

* Can **code like a parent**

* **Paint like the other parent**

* **And survive in the wild**, thanks to the grandparent

This complex setup — where inheritance comes from **different paths** and **multiple levels** — is what we call **hybrid inheritance**.

#### Key Characteristics
* Combines **multiple inheritance forms**

* Used to model **real-world complex systems**

* Must be handled carefully to avoid confusion (especially when same method appears in multiple parent classes)

#### Why Use Hybrid Inheritance?
* To reuse logic from many sources

* To build flexible and realistic class structures

* To organize systems like real-life (e.g., school → staff → teachers, admins, etc.)


```python
# Base class
class Person:
    def __init__(self, name):
        self.name = name

    def introduce(self):
        print("Hi, I'm", self.name)

# First derived class
class Teacher(Person):
    def teach(self):
        print(self.name, "teaches students.")

# Second derived class
class Researcher(Person):
    def research(self):
        print(self.name, "conducts research.")

# Hybrid class inheriting from both Teacher and Researcher
class HybridProfessional(Teacher, Researcher):
    def work(self):
        print(self.name, "teaches and does research.")

```


```python
hp = HybridProfessional("Sandeep")
hp.introduce()    # Inherited from Person
hp.teach()        # From Teacher
hp.research()     # From Researcher
hp.work()         # Own method
```

    Hi, I'm Sandeep
    Sandeep teaches students.
    Sandeep conducts research.
    Sandeep teaches and does research.
    

#### Explanation

| Class                | Inherits From        | What It Adds                         |
| -------------------- | -------------------- | ------------------------------------ |
| `Person`             | Base class           | Common intro method                  |
| `Teacher`            | Person               | Adds teaching behavior               |
| `Researcher`         | Person               | Adds research behavior               |
| `HybridProfessional` | Teacher + Researcher | Inherits both, adds its own behavior |



### Method Overriding
A child class redefines a method it inherited from the parent


```python
class Animal:
    def speak(self):
        print("Animal makes sound")

class Dog(Animal):
    def speak(self):  # Overriding parent method
        print("Dog barks")

d = Dog()
d.speak() 

```

    Dog barks
    

#### Why Override?
To **change or customize** behavior from the parent class

### `super()` Keyword
* Used in a child class to **call the parent class’s method**


```python
class Animal:
    def speak(self):
        print("Animal sound")

class Dog(Animal):
    def speak(self):
        super().speak()  # Call parent method
        print("Dog barks")

d = Dog()
d.speak()
```

    Animal sound
    Dog barks
    

#### Why use super()?
* To **reuse the parent’s method** and **add extra behavior**

### `Constructor` Chaining
Using `super().__init__()` to **call the parent’s constructor**


```python
class Person:
    def __init__(self, name):
        self.name = name
        print("Person constructor called")

class Student(Person):
    def __init__(self, name, roll):
        super().__init__(name)  # Calling Person's constructor
        self.roll = roll
        print("Student constructor called")

s = Student("Sandeep", 101)
```

    Person constructor called
    Student constructor called
    

#### Why use Constructor Chaining?
* To make sure the **parent class is initialized properly**

#### Table

| Concept              | Description                     | Example Class              |
| -------------------- | ------------------------------- | -------------------------- |
| Single Inheritance   | One child from one parent       | `Dog(Animal)`              |
| Multilevel           | Chain of inheritance            | `Dog(Animal(LivingBeing))` |
| Multiple             | One child, multiple parents     | `Child(Mother, Father)`    |
| Overriding           | Redefine parent method          | `Dog.speak()`              |
| `super()`            | Call parent method inside child | `super().speak()`          |
| Constructor Chaining | Initialize parent constructor   | `super().__init__()`       |

