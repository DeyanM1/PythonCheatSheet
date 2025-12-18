# Python Functions. Complete Reference.

All examples below use valid Python syntax.  
Each line ends with a comment explaining exactly what happens.  
You copy any block straight into Jupyter.

---

## Define functions
```python
def f():                               # defines a function with no parameters
    pass                               # does nothing

def add(a, b):                         # defines function with two parameters
    return a + b                       # returns sum
````

---

## Call functions

```python
f()                                    # calls function with no arguments
add(2, 3)                              # calls function with arguments
```

---

## Return behavior

```python
def g():                               # defines function
    return 5                           # returns value

def h():                               # defines function
    x = 10                             # assigns local variable

g()                                    # returns 5
h()                                    # returns None
```

---

## Parameters and arguments

```python
def power(base, exp):                  # defines positional parameters
    return base ** exp                 # raises base to exp

power(2, 3)                            # positional arguments
power(base=2, exp=3)                   # keyword arguments
```

---

## Default values

```python
def greet(name="World"):               # defines default parameter
    return "Hello " + name             # returns greeting

greet()                                # uses default value
greet("Deyan")                         # overrides default
```

---

## Mutable default pitfall

```python
def bad(x=[]):                         # defines mutable default
    x.append(1)                        # modifies same list
    return x                           # returns list

bad()                                  # returns [1]
bad()                                  # returns [1, 1]

def good(x=None):                      # defines safe default
    if x is None:                      # checks missing argument
        x = []                         # creates new list
    x.append(1)                        # modifies list
    return x                           # returns list
```

---

## Variable length arguments

```python
def total(*args):                      # collects positional arguments
    return sum(args)                   # returns sum

total(1, 2, 3)                         # passes multiple values
```

---

## Keyword variable arguments

```python
def show(**kwargs):                    # collects keyword arguments
    return kwargs                      # returns dict

show(a=1, b=2)                         # passes named values
```

---

## Mixed argument order

```python
def mix(a, b=2, *args, **kwargs):      # combines all argument types
    return a, b, args, kwargs          # returns all parts

mix(1, 3, 4, 5, x=10)                  # calls mixed arguments
```

---

## Positional-only parameters

```python
def div(a, b, /):                      # enforces positional-only
    return a / b                       # divides values

div(10, 2)                             # valid call
```

---

## Keyword-only parameters

```python
def scale(x, *, factor):               # enforces keyword-only argument
    return x * factor                  # multiplies value

scale(5, factor=3)                    # valid keyword usage
```

---

## Annotations

```python
def square(x: int) -> int:             # annotates parameter and return
    return x * x                       # returns squared value

square.__annotations__                # shows annotations dictionary
```

---

## Docstrings

```python
def info():                            # defines function
    """Returns static text"""          # documents function
    return "data"                      # returns value

help(info)                             # displays documentation
```

---

## Local vs global scope

```python
x = 10                                 # defines global variable

def scope():                           # defines function
    x = 5                              # defines local variable
    return x                           # returns local value

scope()                                # returns 5
x                                      # remains 10
```

---

## Global keyword

```python
y = 1                                  # defines global variable

def change():                          # defines function
    global y                           # refers to global y
    y = 99                             # modifies global variable

change()                               # updates y
y                                      # equals 99
```

---

## Nonlocal keyword

```python
def outer():                           # defines outer function
    x = 10                             # defines enclosing variable
    def inner():                       # defines inner function
        nonlocal x                     # refers to enclosing x
        x += 1                         # modifies enclosing variable
        return x                       # returns value
    return inner()                     # calls inner

outer()                                # returns 11
```

---

## Lambda functions

```python
square = lambda x: x * x               # creates anonymous function
square(5)                              # returns 25
```

---

## Functions as objects

```python
def inc(x):                            # defines function
    return x + 1                       # increments value

f = inc                                # assigns function to variable
f(10)                                  # calls function via variable
```

---

## Passing functions as arguments

```python
def apply(fn, value):                  # accepts function as argument
    return fn(value)                   # calls function

apply(inc, 5)                          # passes function
```

---

## Returning functions

```python
def make_adder(n):                     # defines factory function
    def adder(x):                      # defines inner function
        return x + n                   # adds captured value
    return adder                       # returns function

add5 = make_adder(5)                   # creates new function
add5(10)                               # returns 15
```

---

## Closures

```python
def counter():                         # defines function
    n = 0                              # defines enclosed variable
    def inc():                         # defines inner function
        nonlocal n                     # refers to enclosed variable
        n += 1                         # increments value
        return n                       # returns value
    return inc                         # returns function

c = counter()                          # creates closure
c()                                    # returns 1
c()                                    # returns 2
```

---

## Decorators

```python
def deco(fn):                          # defines decorator
    def wrap():                        # defines wrapper
        return "Hi " + fn()            # modifies output
    return wrap                        # returns wrapper

@deco                                  # applies decorator
def name():                            # defines function
    return "Deyan"                     # returns name

name()                                 # returns decorated result
```

---

## Built-in function helpers

```python
callable(add)                          # checks object callability
id(add)                                # returns memory identity
type(add)                              # returns function type
```

---

## Introspection

```python
add.__name__                           # returns function name
add.__doc__                            # returns docstring
add.__defaults__                       # returns default values
add.__code__                           # returns code object
```

---

## Error handling inside functions

```python
def safe_div(a, b):                    # defines function
    try:                               # starts error handling
        return a / b                   # divides values
    except ZeroDivisionError:          # handles division error
        return None                    # returns fallback
```

---

## Recursion

```python
def fact(n):                           # defines recursive function
    if n == 0:                         # checks base case
        return 1                       # stops recursion
    return n * fact(n - 1)             # calls itself

fact(5)                                # returns factorial
```

---

## Generator functions

```python
def count_up(n):                       # defines generator
    for i in range(n):                 # loops values
        yield i                        # yields value

list(count_up(5))                      # consumes generator
```

---

## Yield from

```python
def chain(a, b):                       # defines generator
    yield from a                       # yields first iterable
    yield from b                       # yields second iterable

list(chain([1, 2], [3, 4]))            # combines sequences
```

---

## Function performance notes

```python
# local variables resolve faster than globals
# recursion uses call stack
# lambdas store single expressions
# decorators wrap function calls
```
