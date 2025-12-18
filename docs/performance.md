# Python Data and Performance. Complete Reference.

---

## Time Complexity (Big O)

| Operation | List | Dict / Set | Notes |
| --- | --- | --- | --- |
| **Access** |  |  | Dict/Set use hash tables for instant lookup |
| **Search** |  |  | `item in my_dict` is much faster than `item in my_list` |
| **Insert** |  |  | List insertion at start/middle requires shifting elements |
| **Delete** |  |  | List deletion requires shifting; Dict/Set is nearly instant |
| **Append** |  | N/A | Adding to the end of a list is very efficient |

## Profiling: timeit and cProfile

```python
import timeit
import cProfile

# --- Quick Timing with timeit ---
# Useful for small code snippets
setup = "data = list(range(1000))"                       # setup code run once
code = "500 in data"                                     # code to be timed
time = timeit.timeit(stmt=code, setup=setup, number=1000)# returns total time for 1000 executions
print(f"Time taken: {time}")                             # prints execution time

# --- Detailed Profiling with cProfile ---
# Useful for finding bottlenecks in entire functions/scripts
def complex_function():                                  # sample function
    sum([i**2 for i in range(10000)])                    # list comprehension
    return [x for x in range(100)]                       # another operation

cProfile.run('complex_function()')                       # prints table showing calls, time per call, and cumulative time

```

## Memory: References & GC

```python
import sys
import gc

# --- Reference Counting ---
a = [1, 2, 3]                                            # creates list object, ref count = 1
b = a                                                    # b points to same object, ref count = 2
count = sys.getrefcount(a)                               # returns ref count (usually +1 due to temp arg)
print(f"References: {count}")                            # outputs the number of references

# --- Object Identity vs Equality ---
c = [1, 2, 3]                                            # new object with same values
print(a == c)                                            # True: values are the same
print(a is c)                                            # False: different memory addresses

# --- Garbage Collection (GC) ---
# Python uses ref counting + a cyclic garbage collector for "islands" of references
gc.collect()                                             # manually triggers garbage collection
gc.get_stats()                                           # returns list of generation stats
# del a                                                  # removes a reference; if count hits 0, memory is freed

```

## Performance Tips

```python
# --- Generator Expressions vs List Comprehensions ---
# Use generators for large datasets to save memory
large_list = [x**2 for x in range(1000000)]              # builds entire list in memory (heavy)
large_gen = (x**2 for x in range(1000000))               # yields items one-by-one (memory efficient)

# --- Slotting for Classes ---
class FastPoint:
    __slots__ = ('x', 'y')                               # prevents dynamic __dict__ creation, saving memory
    def __init__(self, x, y):
        self.x = x                                       # assigns x
        self.y = y                                       # assigns y

```
