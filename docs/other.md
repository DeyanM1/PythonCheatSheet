
# Python Control Flow and Core Syntax. Complete Reference.

All examples use valid Python syntax.  
Each code line ends with a comment explaining exactly what happens.  
You copy any block straight into Jupyter.

---

## if statement
```python
x = 10                                 # assigns value to x

if x > 5:                              # checks condition
    print("big")                       # runs when condition is true
```

---

## if else

```python
x = 3                                  # assigns value

if x > 5:                              # checks condition
    print("big")                       # runs when true
else:                                  # fallback branch
    print("small")                     # runs when false
```

---

## if elif else

```python
x = 7                                  # assigns value

if x > 10:                             # first condition
    print("large")                     # runs if true
elif x > 5:                            # second condition
    print("medium")                    # runs if true
else:                                  # fallback branch
    print("small")                     # runs if all false
```

---

## Nested if

```python
x = 8                                  # assigns value

if x > 5:                              # outer condition
    if x < 10:                         # inner condition
        print("range")                 # runs if both true
```

---

## match case switch

```python
value = 2                              # assigns value

match value:                           # starts pattern matching
    case 1:                            # matches literal 1
        print("one")                   # runs on match
    case 2:                            # matches literal 2
        print("two")                   # runs on match
    case _:                            # default case
        print("other")                 # runs when no match
```

---

## match with multiple values

```python
x = "b"                                # assigns value

match x:                               # starts match
    case "a" | "b":                    # matches a or b
        print("letter")                # runs on match
    case _:                            # default
        print("other")                 # fallback
```

---

## for loop

```python
for i in range(3):                     # loops from 0 to 2
    print(i)                           # prints current value
```

---

## for loop over list

```python
items = [10, 20, 30]                   # creates list

for item in items:                    # loops through elements
    print(item)                        # prints element
```

---

## for with enumerate

```python
items = ["a", "b", "c"]                # creates list

for i, v in enumerate(items):          # loops with index
    print(i, v)                        # prints index and value
```

---

## for with break

```python
for i in range(5):                     # starts loop
    if i == 3:                         # checks condition
        break                          # exits loop
    print(i)                           # prints value
```

---

## for with continue

```python
for i in range(5):                     # starts loop
    if i == 3:                         # checks condition
        continue                       # skips iteration
    print(i)                           # prints value
```

---

## for else

```python
for i in range(3):                     # loops values
    print(i)                           # prints value
else:                                  # runs after normal completion
    print("done")                      # prints after loop
```

---

## while loop

```python
i = 0                                  # initializes counter

while i < 3:                           # checks condition
    print(i)                           # prints value
    i += 1                             # increments counter
```

---

## while with break

```python
i = 0                                  # initializes counter

while True:                            # infinite loop
    if i == 3:                         # checks exit condition
        break                          # exits loop
    print(i)                           # prints value
    i += 1                             # increments counter
```

---

## while else

```python
i = 0                                  # initializes counter

while i < 3:                           # loop condition
    print(i)                           # prints value
    i += 1                             # increments counter
else:                                  # runs after normal exit
    print("done")                      # prints message
```

---

## pass

```python
x = 5                                  # assigns value

if x > 0:                              # checks condition
    pass                               # placeholder with no action
```

---

## lambda

```python
square = lambda x: x * x               # creates anonymous function
square(4)                              # returns 16
```

---

## lambda with sort

```python
items = [(1, 3), (2, 1), (3, 2)]        # creates list of tuples

items.sort(key=lambda x: x[1])         # sorts by second value
items                                  # shows sorted list
```

---

## try except

```python
try:                                   # starts error handling
    x = 10 / 0                         # raises error
except ZeroDivisionError:              # catches error
    x = 0                              # assigns fallback value
```

---

## try except else finally

```python
try:                                   # starts block
    x = 10 / 2                         # runs risky code
except ZeroDivisionError:              # handles error
    x = 0                              # fallback
else:                                  # runs when no error
    print("ok")                        # prints message
finally:                               # always runs
    print("end")                       # cleanup logic
```

---

## assert

```python
x = 5                                  # assigns value

assert x > 0                           # stops program if false
```

---

## with statement

```python
with open("file.txt", "w") as f:       # opens file safely
    f.write("data")                    # writes content
```

---

## comprehension with condition

```python
nums = [1, 2, 3, 4, 5]                 # creates list

evens = [x for x in nums if x % 2 == 0]# filters even numbers
```

---

## ternary expression

```python
x = 10                                 # assigns value

result = "big" if x > 5 else "small"   # assigns based on condition
```

---

## important rules

```python
# indentation controls blocks
# break exits loops
# continue skips iteration
# else after loops runs on normal exit
# match replaces long if chains
# lambda stores single expressions
# try blocks protect risky code
```
