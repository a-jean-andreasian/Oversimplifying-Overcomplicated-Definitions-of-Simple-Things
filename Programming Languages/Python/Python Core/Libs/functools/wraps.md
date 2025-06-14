*This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean
Andreasian.*

---

# `functools.wraps`

---

## Table of Contents

* [What is `wraps`?](#what-is-wraps)
* [Examples](#examples)

---

### What is `wraps`?

- Wraps is a decorator for the inner function of the [decorator](../../../Paradigms%20in%20Python/Functional%20Programming/Decorator/decorator.md) function.
- The point of `wraps` is to **keep the original metadata of the decorated function**, which in case of custom decorators are being lost and switched to metadata of the decorator function.


- The metadata it copies includes: `__name__`, `__doc__`, `__module__`, `__annotations__`, and `__dict__`. 

---

#### Without `wraps`:

```python
def split_function(function):
    def wrapper():
        return function()
    return wrapper


@split_function
def passphrase():
    """Some doc"""
    return "Horizontal Omit Station Reflection"


print(passphrase.__name__)  # wrapper
print(passphrase.__doc__)  # None
```

#### With `wraps`:

```python
from functools import wraps


def split_function(function):
    @wraps(function)
    def wrapper():
        return function()

    return wrapper


@split_function
def passphrase():
    """Some doc"""
    return "Horizontal Omit Station Reflection"


print(passphrase.__name__)  # passphrase
print(passphrase.__doc__)  # Some doc
```