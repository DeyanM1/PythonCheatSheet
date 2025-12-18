# Error Handling

All examples are valid Python syntax.  
Each line ends with a comment explaining exactly what happens.  
Copy any block directly into Jupyter.

---

## Basic try except
```python
try:                                   # starts protected block
    x = 10 / 0                         # risky code, raises ZeroDivisionError
except ZeroDivisionError:              # catches specific error
    x = 0                              # assigns fallback value
```

---

## Multiple except clauses

```python
try:                                   # starts block
    lst = [1, 2]                       # creates list
    x = lst[5]                         # raises IndexError
except ZeroDivisionError:              # handles division errors
    print("divided by zero")           # prints message
except IndexError:                      # handles index errors
    print("index out of range")        # prints message
```

---

## Catch all exceptions

```python
try:                                   # risky code
    y = int("abc")                     # raises ValueError
except Exception as e:                 # catches any exception
    print(e)                            # prints error message
```

---

## else clause

```python
try:                                   # risky block
    x = 10 / 2                         # no error
except ZeroDivisionError:              # handles error
    print("division by zero")          # would run on error
else:                                  # runs only if no error
    print("ok")                        # prints message
```

---

## finally clause

```python
try:                                   # risky block
    x = 10 / 2                         # code runs
except ZeroDivisionError:              # handles error
    x = 0                              # fallback
finally:                               # always runs
    print("cleanup")                   # prints cleanup message
```

---

## Raising exceptions

```python
def div(a, b):                         # defines function
    if b == 0:                         # checks condition
        raise ValueError("b cannot be 0")  # raises exception
    return a / b                        # returns division

# div(10, 0) would raise ValueError
```

---

## Custom exceptions

```python
class MyError(Exception):               # defines new exception
    pass                                # no extra logic

def test(n):                            # function that raises
    if n < 0:                            # check condition
        raise MyError("negative!")      # raises custom error
    return n                             # returns value if ok
```

---

## try except with else and finally

```python
try:                                   # start block
    x = int("5")                        # risky code
except ValueError as e:                 # handle value errors
    print("error:", e)                  # prints error
else:                                  # runs if no error
    print("ok:", x)                     # prints value
finally:                               # always runs
    print("done")                       # prints message
```

---

## Nested try except

```python
try:                                   # outer block
    try:                               # inner block
        x = 1 / 0                       # raises ZeroDivisionError
    except ZeroDivisionError:          # catches inner error
        print("inner handled")          # prints message
except Exception:                       # catches outer error
    print("outer handled")              # prints if uncaught inner
```

---

## Assertions

```python
x = 5                                  # assign value
assert x > 0, "x must be positive"     # raises AssertionError if false
```

---

## Context manager for error cleanup

```python
with open("file.txt", "w") as f:       # opens file safely
    try:                               # risky write
        f.write("data")                # writes content
    except IOError as e:               # catches I/O errors
        print(e)                       # prints message
```

---

## Best practices notes

```python
# Catch specific exceptions, not bare 'except'
# Use finally for cleanup (files, sockets)
# Use else for code that runs only if no exception
# Raise exceptions for invalid states
# Custom exceptions should inherit from Exception
# Assertions for debugging checks, not runtime control
```
