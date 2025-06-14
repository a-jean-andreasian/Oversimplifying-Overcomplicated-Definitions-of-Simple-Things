*This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean
Andreasian.*

---

# Decorator

---

## Table of Contents

* [What is a decorator?](#what-is-a-decorator)
* [Decorator without arguments](#decorator-without-arguments)
* [Decorator with arguments](#decorator-with-arguments)
* [The order of execution of multiple decorators](#the-order-of-execution-of-multiple-decorators)
* [`functools.wraps`](#functoolswraps)
* [Class decorator](#class-decorator)

---

# What is a decorator?

- Decorator is a way to **extend or modify** logic to an existing function.
  - That additional logic will be executed before or after the execution of that function.
  - This way we can extend, or radically modify the behaviour of the function.

- Decorator is a way to "bake-in" the function into a [closure](../Closure/closure.md).


---
## Decorator without arguments

This decorator is a two-level decorator.

1. First-level **(captured forever)** of the decorator takes the decorable (original) function
2. Second-level **(dynamic)** the arguments of the decorable function.
    - arguments are optional, custom, args, kwargs, but the level is mandatory
- The second-level function should call the passed function.
- The first-level nested function should return the next inner function


```python
def decorator(func):  # first level
    def wrapper(*args, **kwargs):  # second level
        result = func(*args, **kwargs)
        return result
    return wrapper
```

---
## Decorator with arguments

This decorator is a three-level decorator.

1. First level **(captured forever)** of the decorator takes arguments
    - arguments: custom, args, kwargs. but the level is not optional because if no arguments no sense to use this type of decorator)
2. Second level **(captured forever)** of the decorator takes the decorable function
    - arguments are optional, custom, args, kwargs, but the level is mandatory
3. Third level **(dynamic)** of the decorator takes the arguments of the decorable function
- The second-level function should call the passed function.
- The first-level nested function should return the next inner function


```python
def outer(some_arg):
    def decorator(func):
        def wrapper(*args, **kwargs):
          if some_arg:
            return func(*args, **kwargs)
          return None
        return wrapper
    return decorator
```

---
## The order of execution of multiple decorators

Example:
```python
@decorator1
@decorator2
def func():
   ...
```

In such case first `decorator1` works, then `decorator2`

---
## [`functools.wraps`](../../../Python%20Core/Libs/functools/wraps.md)

### Problem
When we use a decorator the original function's metadata becomes the wrapper.

Solution:
To see the metadata of the original function we use `wraps` module from `functools` lib. 

Read more about `functools.wraps` [here](../../../Python%20Core/Libs/functools/wraps.md).

---
## Class decorator

Class decorator is a way of [metaprogramming](../../../Techniques/Metaprogramming/metaprogramming.md).

- It modifies class variables
- It modifies class methods

Example of Singleton class decorator:
```python
def singleton(cls):
    """Ensures a class has only one instance"""
    instances = {}
    def wrapper(*args, **kwargs):
        if cls not in instances:
            instances[cls] = cls(*args, **kwargs)
        return instances[cls]
    return wrapper

@singleton
class AppConfig:
    def __init__(self):
        self.settings = {"theme": "dark"}

config1 = AppConfig()
config2 = AppConfig()
print(config1 is config2)  # True (same instance)
```

The flow:

```
1. **Initial Call** (`AppConfig()`)
   → Triggers `wrapper(*args, **kwargs)`

2. **Wrapper Execution**
   ├─ Checks `instances` cache (miss)
   └─ Calls `cls(*args, **kwargs)` → Activates Python's instantiation protocol

3. **Class Instantiation Protocol**
   a. `type.__call__(cls)` (metaclass-level)
   ├─ 1. `cls.__new__(cls)` → creates raw instance
   └─ 2. `instance.__init__(*args, **kwargs)` → initializes instance

4. **Wrapper Completion**
   ├─ Stores result in `instances[cls]`
   └─ Returns initialized instance

5. **Subsequent Calls**
   ├─ Cache hit → returns existing instance
   └─ **Skips** both `__new__` and `__init__`
```

