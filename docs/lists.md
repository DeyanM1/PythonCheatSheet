# Python Lists. Complete Reference.

Copy sections directly into a Jupyter notebook.

---

## Create Lists

```python
a = []                                  # creates an empty list
b = list()                              # creates an empty list using constructor
c = [1, 2, 3]                           # creates a list with three integers
d = list(range(5))                      # creates list from 0 to 4
e = [x for x in range(10)]              # creates list using comprehension
f = [[1, 2], [3, 4]]                    # creates a nested list
````

---

## Basic Access and Slicing

```python
len(c)                                 # returns number of elements
type(c)                                # returns the list type
c[0]                                   # accesses first element
c[-1]                                  # accesses last element
c[1:3]                                 # slices from index 1 to 2
c[:2]                                  # slices first two elements
c[::2]                                 # slices every second element
c[::-1]                                # reverses the list
```

---

## Modify Elements

```python
c[0] = 100                             # replaces first element
c[1:3] = [200, 300]                    # replaces a slice with new values
```

---

## Add Elements

```python
c.append(400)                          # adds element to end
c.extend([500, 600])                   # adds multiple elements
c.insert(1, 150)                       # inserts element at index 1
```

---

## Remove Elements

```python
c.remove(150)                          # removes first matching value
c.pop()                                # removes and returns last element
c.pop(0)                               # removes and returns element at index 0
del c[0]                               # deletes element at index 0
del c[1:3]                             # deletes a slice
c.clear()                              # removes all elements
```

---

## Search and Count

```python
x = [1, 2, 2, 3, 4]                    # creates list with duplicates
x.index(2)                             # returns index of first match
x.count(2)                             # counts occurrences
```

---

## Sort and Reverse

```python
y = [5, 1, 4, 2, 3]                    # creates unsorted list
y.sort()                               # sorts ascending
y.sort(reverse=True)                   # sorts descending
y.reverse()                            # reverses current order
```

---

## Copy Lists

```python
z = y.copy()                           # shallow copy
z2 = list(y)                           # shallow copy using constructor
z3 = y[:]                              # shallow copy using slicing
```

---

## Membership

```python
3 in y                                 # checks if value exists
10 not in y                            # checks if value does not exist
```

---

## Iteration

```python
for item in y:                         # loops through elements
    print(item)                        # prints element

for i, item in enumerate(y):           # loops with index
    print(i, item)                     # prints index and value
```

---

## List Comprehensions

```python
squares = [i * i for i in range(10)]   # generates squares
evens = [i for i in range(20) if i % 2 == 0]  # filters even numbers
pairs = [(i, j) for i in range(3) for j in range(3)]  # creates pairs
flat = [n for row in f for n in row]   # flattens nested list
```

---

## Map and Filter Style

```python
mapped = list(map(lambda x: x * 2, y))       # applies function to each element
filtered = list(filter(lambda x: x > 2, y))  # filters elements
```

---

## Aggregations

```python
nums = [1, 2, 3, 4]                    # numeric list
sum(nums)                              # returns sum
min(nums)                              # returns minimum
max(nums)                              # returns maximum
```

---

## Comparison

```python
[1, 2, 3] == [1, 2, 3]                 # compares values
[1, 2] < [1, 3]                       # lexicographical comparison
```

---

## Nested Lists

```python
matrix = [
    [1, 2, 3],                         # first row
    [4, 5, 6],                         # second row
    [7, 8, 9]                          # third row
]

matrix[0][1]                           # accesses row 0 column 1
transpose = list(zip(*matrix))         # transposes matrix
```

---

## Unpacking

```python
a, b, c = [1, 2, 3]                    # assigns by position
a, *rest = [1, 2, 3, 4]                # stores remaining values
first, *middle, last = [10, 20, 30, 40]# splits list
```

---

## Join Lists

```python
l1 = [1, 2]                            # first list
l2 = [3, 4]                            # second list
joined = l1 + l2                       # creates new list
l1 += l2                               # extends list in place
```

---

## Repeat Elements

```python
zeros = [0] * 5                        # repeats element
```

---

## Identity vs Equality

```python
p = [1, 2, 3]                          # creates list
q = p                                  # same reference
r = p.copy()                           # new object

p is q                                 # checks identity
p is r                                 # checks different objects
p == r                                 # checks values
```

---

## Rare and Internal Methods

```python
help(list)                             # displays list documentation
[1, 2].__add__([3, 4])                 # adds lists internally
[1, 2].__mul__(3)                      # repeats list internally
[1, 2, 3].__contains__(2)              # checks membership internally
[1, 2, 3].__len__()                    # returns length internally
[10, 20, 30].__getitem__(1)            # accesses element internally

x = [1, 2, 3]                          # creates list
x.__setitem__(0, 99)                   # sets value internally
x                                     # shows updated list
x.__delitem__(1)                       # deletes value internally
x                                     # shows updated list
```

---

## Convert From Other Types

```python
list("abc")                            # converts string to list
list((1, 2, 3))                        # converts tuple
list({1, 2, 3})                        # converts set
list({1: "a", 2: "b"})                 # converts dict keys
```

---