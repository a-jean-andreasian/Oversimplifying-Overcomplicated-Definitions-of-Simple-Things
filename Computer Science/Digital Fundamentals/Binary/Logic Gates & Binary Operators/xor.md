_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean Andreasian._

---
## Content
- [What is XOR?](#what-is-xor)
  - [Example](#example)
  - [Code](#code)
- [Use cases](#use-cases)
---
# What is XOR

XOR (exclusive or) from the perspective of the result, is identical to `==`. The difference is how they work:

- `XOR`: Compares the bits of values and returns `0` for "yes" and `1` for "no".
- `==`: Compares the actual values and returns `true` or `false`.

---
## Example
```
a = 5
b = 5

a ^ b => comparing 0000000000000101 and 0000000000000101
```

Quick recap:
- Bits are compared one by one.
- You can use `0b` prefix to write the prefix of a binary number in Python.


---
## Code

```python
a = 5
b = 5

print(a == b)      # True
print(a ^ b == 0)  # True
```

---
# Use cases

The use case is rare and not about software development, where `==` is enough.
Used in:
- discrete mathematics
- systems programming
- cryptography
- reverse engeneering
- algorithms
