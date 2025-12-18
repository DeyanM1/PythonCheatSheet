# Python Classes

All examples use valid Python syntax.  
Each line ends with an end of line comment explaining exactly what happens.  
You copy any block straight into Jupyter.

---

## Define a class
```python
class Person:                          # defines a new class
    pass                               # empty class body
```

---

## Create objects

```python
p = Person()                           # creates an instance of Person
type(p)                                # returns instance type
```

---

## **init** constructor

```python
class Person:                          # defines class
    def __init__(self, name, age):     # runs on object creation
        self.name = name               # stores name on instance
        self.age = age                 # stores age on instance

p = Person("Deyan", 20)                # creates initialized object
p.name                                 # accesses instance attribute
p.age                                  # accesses instance attribute
```

---

## Instance methods

```python
class Counter:                         # defines class
    def __init__(self):                # constructor
        self.value = 0                 # initializes value

    def inc(self):                     # defines instance method
        self.value += 1                # increments value
        return self.value              # returns new value

c = Counter()                          # creates object
c.inc()                                # calls method
```

---

## **repr** and **str**

```python
class Point:                           # defines class
    def __init__(self, x, y):          # constructor
        self.x = x                     # assigns x
        self.y = y                     # assigns y

    def __repr__(self):                # developer string
        return f"Point({self.x}, {self.y})"  # returns representation

    def __str__(self):                 # user string
        return f"{self.x}, {self.y}"   # returns readable text

p = Point(1, 2)                        # creates object
repr(p)                                # uses __repr__
str(p)                                 # uses __str__
```

---

## Attribute access hooks

```python
class Test:                            # defines class
    def __getattr__(self, name):       # runs on missing attribute
        return "missing"               # returns fallback value

t = Test()                             # creates object
t.anything                             # triggers __getattr__
```

---

## **eq** comparison

```python
class Box:                             # defines class
    def __init__(self, v):             # constructor
        self.v = v                     # stores value

    def __eq__(self, other):           # defines equality
        return self.v == other.v       # compares internal values

Box(1) == Box(1)                       # evaluates equality
```

---

## Ordering methods

```python
class Num:                             # defines class
    def __init__(self, n):             # constructor
        self.n = n                     # stores number

    def __lt__(self, other):           # defines less-than
        return self.n < other.n        # compares values

Num(1) < Num(2)                        # evaluates comparison
```

---

## **len** and **bool**

```python
class Data:                            # defines class
    def __init__(self, items):         # constructor
        self.items = items             # stores list

    def __len__(self):                 # defines length
        return len(self.items)         # returns size

    def __bool__(self):                # defines truth value
        return bool(self.items)        # converts to boolean

d = Data([1, 2])                       # creates object
len(d)                                 # calls __len__
bool(d)                                # calls __bool__
```

---

## **call**

```python
class Adder:                           # defines class
    def __init__(self, n):             # constructor
        self.n = n                     # stores value

    def __call__(self, x):             # makes object callable
        return x + self.n              # returns computed result

a = Adder(5)                           # creates callable object
a(10)                                  # calls __call__
```

---

## Class variables

```python
class Car:                             # defines class
    wheels = 4                         # defines class attribute

c1 = Car()                             # creates object
c2 = Car()                             # creates object
c1.wheels                              # reads class attribute
```

---

## Class methods

```python
class User:                            # defines class
    count = 0                          # class variable

    def __init__(self):                # constructor
        User.count += 1                # increments class variable

    @classmethod
    def total(cls):                    # defines class method
        return cls.count               # returns shared state

User()                                 # creates object
User.total()                           # calls class method
```

---

## Static methods

```python
class Math:                            # defines class
    @staticmethod
    def add(a, b):                     # defines static method
        return a + b                   # returns sum

Math.add(2, 3)                         # calls static method
```

---

## Inheritance

```python
class Animal:                          # defines base class
    def speak(self):                   # defines method
        return "sound"                 # returns text

class Dog(Animal):                     # defines subclass
    def speak(self):                   # overrides method
        return "bark"                  # returns new text

Dog().speak()                          # calls overridden method
```

---

## super()

```python
class A:                               # defines base class
    def __init__(self):                # constructor
        self.x = 1                     # sets value

class B(A):                            # defines subclass
    def __init__(self):                # constructor
        super().__init__()             # calls base constructor
        self.y = 2                     # sets extra value

b = B()                                # creates object
```

---

## Multiple inheritance

```python
class X:                               # defines class
    def a(self):                       # defines method
        return "X"                     # returns value

class Y:                               # defines class
    def b(self):                       # defines method
        return "Y"                     # returns value

class Z(X, Y):                         # inherits from X and Y
    pass                               # no extra logic

z = Z()                                # creates object
z.a()                                  # resolves from X
z.b()                                  # resolves from Y
```

---

## **slots**

```python
class Slim:                            # defines class
    __slots__ = ("x", "y")             # restricts attributes

s = Slim()                             # creates object
s.x = 1                                # assigns allowed attribute
```

---

## **del** destructor

```python
class Temp:                            # defines class
    def __del__(self):                 # runs on deletion
        print("deleted")               # prints message

t = Temp()                             # creates object
del t                                  # deletes object
```

---

## Operator overloading

```python
class Vec:                             # defines class
    def __init__(self, x):             # constructor
        self.x = x                     # stores value

    def __add__(self, other):          # overloads +
        return Vec(self.x + other.x)   # returns new object

Vec(1) + Vec(2)                        # adds objects
```

---

## Context manager

```python
class Manager:                         # defines class
    def __enter__(self):               # runs on enter
        return "inside"                # returns context value

    def __exit__(self, t, v, tb):      # runs on exit
        pass                            # handles cleanup

with Manager() as m:                   # enters context
    m                                  # uses returned value
```

---

## Dataclass style

```python
from dataclasses import dataclass      # imports decorator

@dataclass
class Item:                            # defines data container
    name: str                          # defines field
    price: int                         # defines field

i = Item("pen", 2)                     # creates object
i.name                                 # accesses field
```

---

## Introspection

```python
p.__dict__                             # shows instance attributes
Person.__dict__                        # shows class attributes
isinstance(p, Person)                 # checks instance type
issubclass(Dog, Animal)               # checks inheritance
```

---

## Performance notes

```python
# attribute lookup checks instance then class
# __slots__ reduces memory usage
# method calls bind self automatically
# inheritance follows method resolution order
```
