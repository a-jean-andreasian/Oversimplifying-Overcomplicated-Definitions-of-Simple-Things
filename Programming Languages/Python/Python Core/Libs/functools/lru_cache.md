*This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean
Andreasian.*

---

# `functools.lru_cache`

---

## Table of Contents

* [What is `lru_cache`?](#what-is-lru_cache)
* [How it works](#how-it-works)
* [Arguments `lru_cache` takes](#arguments-lru_cache-takes)
* [Examples](#examples)
* [`lru_cache` and PyPy](#lru_cache-and-pypy)

---

# What is `lru_cache`?

`lru_cache` is a decorator that remembers function results so it doesn't have to do the same work twice. 

> #### For calls with different arguments this is useless!
>
> Only repetitive calls with _**the same**_ stack of arguments.

- It can save time when:
  - **An expensive** or **I/O bound** function is periodically called with the **same arguments**.

---
## How it works?

- The cache is threadsafe so that the wrapped function can be used in multiple threads.
- Whenever you call the function again, it just gives you the stored answer instantly.
- It also throws out old answers if it runs out of space, keeping only the most recently used ones depending on the
  `maxsize` kwarg you provide.
- You can also clear the cache using `decorated_function.cache_clear()` method.


---

## Arguments `lru_cache` takes

- `maxsize: int | None` < 128 : The `maxsize` number of unique sets of arguments/results are cached. 
  - If `maxsize` is set to `None`, the LRU feature is disabled and the cache can grow without bound.


- `typed: bool | None` : If typed is set to `True`, function arguments of different types will be cached separately. 
  - If typed is `False`, the implementation will usually regard them as equivalent calls and only cache a single result. (Some types such as str and int may be cached separately even when typed is false.)

---
## Examples


Simple example:

```python
from functools import lru_cache


@lru_cache(maxsize=128)
def slow_add(a, b):
    print("Doing work...")
    return a + b


if __name__ == '__main__':
    slow_add(1, 2)  # Prints "Doing work..." and returns 3
    slow_add(1, 2)  # Just returns 3 instantly, no print
```


Example with Fibonacci number:

```python
from functools import lru_cache

@lru_cache(maxsize=128)
def fib(n):
    def inner():
        if n < 2:
            return n
        return fib(n - 1) + fib(n - 2)
    return inner()


if __name__ == '__main__':
    print(fib(6))
    print(fib(6))
```

And to measure all this:

```python
from functools import wraps
from functools import lru_cache
from time import time

def timer(func):
    @wraps(func)
    def wrap(*args, **kw):
        ts = time()
        result = func(*args, **kw)
        te = time()
        print(f'func: {func.__name__} took: {te - ts:.4f} sec')
        return result

    return wrap


@timer
@lru_cache
def count():
    for _ in range(5_000_000):
      pass
    return True

if __name__ == '__main__':
    count() # func: count took: 0.0754 sec
    count() # func: count took: 0.0000 sec
```

---
## `lru_cache` and PyPy


It works with PyPy, but with a caveat. 
PyPy has its own version of the `functools` module, and it supports `lru_cache`, but:

* **It's slower than CPython’s version** in some cases because PyPy’s JIT doesn’t optimize the decorator as
  aggressively.
* **It still works correctly**, just maybe not as efficiently, depending on how you're using it.


### If you really care about performance on PyPy, you might consider:

* Writing your own simple cache with a `dict`.
* Using third-party caching libraries that are PyPy-optimized (like `cachetools`).
