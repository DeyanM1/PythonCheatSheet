# Async and Concurrency

---

## Threading: Shared Memory (I/O Bound)

```python
import threading
import time

# --- Basic Threading ---
def print_numbers():
    for i in range(5):
        time.sleep(0.1)                                 # simulates I/O (waiting)
        print(f"Thread: {i}")

t1 = threading.Thread(target=print_numbers)             # creates thread object
t1.start()                                              # launches the thread
t1.join()                                               # waits for thread to finish before continuing

# --- Race Conditions & Locks ---
counter = 0
lock = threading.Lock()                                 # creates a mutex lock

def increment():
    global counter
    for _ in range(100000):
        with lock:                                      # ensures only one thread modifies at a time
            counter += 1                                # critical section

threads = [threading.Thread(target=increment) for _ in range(2)]
for t in threads: t.start()
for t in threads: t.join()
print(f"Final counter: {counter}")                      # guaranteed 200000 with lock

```

## Multiprocessing: Parallel CPU (CPU Bound)

```python
import multiprocessing
import os

# --- Parallel Execution ---
# Bypasses the Global Interpreter Lock (GIL) by using separate memory spaces
def compute_heavy_task(n):
    print(f"Process {os.getpid()} calculating...")      # shows unique OS process ID
    return sum(i * i for i in range(n))

if __name__ == "__main__":                              # required on Windows for multiprocessing
    p1 = multiprocessing.Process(target=compute_heavy_task, args=(10**6,))
    p1.start()                                          # starts a new Python instance
    p1.join()                                           # joins main process

# --- Using a Pool ---
    with multiprocessing.Pool(processes=4) as pool:     # creates a pool of 4 workers
        results = pool.map(compute_heavy_task, [10**6, 10**7, 10**8]) # distributes tasks

```

## Asyncio: Cooperative Multitasking

```python
import asyncio

# --- Async/Await Basics ---
async def fetch_data(id):                               # defines a coroutine
    print(f"Task {id} starting...")
    await asyncio.sleep(1)                              # non-blocking wait (yields control to loop)
    print(f"Task {id} finished.")
    return {"id": id, "data": "success"}

# --- Running Tasks Concurrently ---
async def main():
    # schedule multiple coroutines at once
    task1 = asyncio.create_task(fetch_data(1))          # schedules execution
    task2 = asyncio.create_task(fetch_data(2))
    
    res1 = await task1                                  # waits for specific task result
    res2 = await task2
    
    # OR use gather for many tasks
    results = await asyncio.gather(fetch_data(3), fetch_data(4))
    print(results)

# asyncio.run(main())                                   # entry point to start the event loop

```

## Concurrent Futures: High-level API

```python
from concurrent.futures import ThreadPoolExecutor, ProcessPoolExecutor

# --- Unified Interface for Pools ---
def task(n):
    return n * 2

# Use ThreadPoolExecutor for I/O tasks
with ThreadPoolExecutor(max_workers=3) as executor:
    futures = [executor.submit(task, i) for i in range(5)] # submits tasks to threads
    results = [f.result() for f in futures]             # retrieves results as they complete

# Use ProcessPoolExecutor for CPU tasks
with ProcessPoolExecutor() as executor:
    results = list(executor.map(task, range(10)))       # easy mapping of function to data

```