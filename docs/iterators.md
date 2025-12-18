# Iterators and Generators

---

## The Iterator Protocol

```python
# --- Manual Iteration ---
my_list = [10, 20]                                      # an iterable
it = iter(my_list)                                      # gets an iterator object (calls __iter__)
print(next(it))                                         # returns 10 (calls __next__)
print(next(it))                                         # returns 20
# next(it)                                              # raises StopIteration exception

# --- Custom Iterator Class ---
class Countdown:
    def __init__(self, start):
        self.count = start                              # initializes state
    def __iter__(self):
        return self                                     # an iterator must return itself as an iterator
    def __next__(self):
        if self.count <= 0:                             # check for end condition
            raise StopIteration                         # signals end of iteration
        self.count -= 1                                 # decrements state
        return self.count + 1                           # returns current value

```

## Advanced Itertools

```python
import itertools

# --- Combining & Repeating ---
# chain: treats multiple sequences as a single continuous one
combined = itertools.chain([1, 2], ['a', 'b'])          # yields 1, 2, 'a', 'b'

# product: cartesian product (nested for-loop equivalent)
colors = ['red', 'blue']
sizes = ['S', 'M']
pairs = itertools.product(colors, sizes)                # yields ('red', 'S'), ('red', 'M'), etc.

# --- Grouping & Filtering ---
# Note: groupby only groups CONSECUTIVE identical items (sort first!)
data = [('A', 1), ('A', 2), ('B', 3), ('B', 4)]
for key, group in itertools.groupby(data, lambda x: x[0]):
    print(key, list(group))                             # prints 'A' [('A', 1), ('A', 2)]...

# --- Infinite Iterators ---
# counter = itertools.count(start=10, step=2)           # yields 10, 12, 14... forever
# cycle = itertools.cycle('ABC')                        # yields A, B, C, A, B, C... forever

```

## Generator Patterns: Pipelines & Lazy Evaluation

```python
# --- Lazy Evaluation ---
def get_large_data():
    for i in range(1000000):                            # simulates huge dataset
        yield i                                         # produces value only when requested (saves memory)

# --- Generator Pipelines (Processing Streams) ---
def integers():
    for i in range(1, 10): yield i                      # source: yields 1 to 9

def squared(seq):
    for i in seq: yield i * i                           # transformation: squares values

def filtered(seq):
    for i in seq:
        if i % 2 == 0: yield i                          # filter: keeps only even squares

# Connect the pipeline
pipeline = filtered(squared(integers()))                # nothing is calculated yet (lazy)
results = list(pipeline)                                # execution happens here; values "pull" through
print(results)                                          # output: [4, 16, 36, 64]

# --- Yield From (Subgenerators) ---
def count_to_three():
    yield from [1, 2, 3]                                # delegates to another iterable or generator

```
