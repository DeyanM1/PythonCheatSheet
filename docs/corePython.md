# Core Python

---

## Strings
```python
s = "hello world"                      # creates string

len(s)                                 # returns length
s[0]                                   # accesses first character
s[-1]                                  # accesses last character
s[0:5]                                 # slices substring
s[::-1]                                # reverses string

s.upper()                              # converts to uppercase
s.lower()                              # converts to lowercase
s.title()                              # capitalizes words
s.strip()                              # removes surrounding whitespace
s.replace("world", "python")           # replaces substring
s.split(" ")                           # splits into list
"-".join(["a", "b", "c"])              # joins list into string

name = "Deyan"                         # assigns variable
f"Hello {name}"                        # formats string using f-string
```

---

## Tuples

```python
t = (1, 2, 3)                          # creates tuple
t[0]                                   # accesses element
len(t)                                 # returns length

a, b, c = t                            # unpacks tuple
single = (1,)                          # creates single element tuple
```

---

## Lists

```python
lst = [1, 2, 3]                        # creates list
lst.append(4)                          # adds element
lst.extend([5, 6])                     # adds multiple elements
lst.insert(1, 99)                      # inserts at index
lst.remove(99)                         # removes by value
lst.pop()                              # removes last element
lst.sort()                             # sorts list
lst.reverse()                          # reverses list
```

---

## Dictionaries

```python
d = {"a": 1, "b": 2}                   # creates dictionary

d["a"]                                 # accesses value
d.get("c", 0)                          # gets value with default
d["c"] = 3                             # adds key value pair
d.update({"d": 4})                     # updates dictionary
d.pop("a")                             # removes key
d.keys()                               # returns keys view
d.values()                             # returns values view
d.items()                              # returns key value pairs
```

---

## Dictionary comprehensions

```python
squares = {x: x * x for x in range(5)} # creates dict using comprehension
```

---

## Sets

```python
s = {1, 2, 3}                          # creates set
s.add(4)                               # adds element
s.remove(3)                            # removes element
s.discard(10)                          # removes if exists
```

---

## Set operations

```python
a = {1, 2, 3}                          # creates set
b = {3, 4, 5}                          # creates set

a | b                                  # union
a & b                                  # intersection
a - b                                  # difference
a ^ b                                  # symmetric difference
```

---

## None and truthiness

```python
x = None                               # assigns None

bool([])                               # evaluates False
bool([1])                              # evaluates True
bool("")                               # evaluates False
bool("x")                              # evaluates True
```

---

## Built-in functions

```python
abs(-5)                                # returns absolute value
round(3.7)                             # rounds number
pow(2, 3)                              # raises power
sorted([3, 1, 2])                      # returns sorted list
reversed([1, 2, 3])                    # returns reverse iterator
```

---

## zip

```python
a = [1, 2, 3]                          # first list
b = ["a", "b", "c"]                    # second list

list(zip(a, b))                        # pairs elements
```

---

## any and all

```python
any([False, True, False])              # returns True if any True
all([True, True, False])               # returns False if any False
```

---

## enumerate

```python
items = ["x", "y", "z"]                # creates list

for i, v in enumerate(items):          # loops with index
    print(i, v)                        # prints index and value
```

---

## range

```python
list(range(5))                         # generates numbers 0 to 4
list(range(1, 5))                      # generates numbers 1 to 4
list(range(0, 10, 2))                  # generates even numbers
```

---

## Type checking

```python
x = 5                                  # assigns integer

type(x)                                # returns type
isinstance(x, int)                     # checks instance
```

---

## Copy behavior

```python
a = [1, 2, 3]                          # creates list
b = a                                  # assigns same reference
c = a.copy()                           # creates shallow copy
```

---

## Input and output

```python
name = input("Enter name: ")           # reads user input
print(name)                            # prints value
```

---

## Important rules

```python
# everything is an object
# variables store references
# immutable types do not change in place
# mutable types change in place
# indentation defines structure
```