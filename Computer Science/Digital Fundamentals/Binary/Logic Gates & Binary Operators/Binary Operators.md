_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean
Andreasian._

---

## Content

- [Binary Operators](#binary-operators)

---

# Binary Operators

The common binary operators:

* `^` — **XOR** (bitwise exclusive OR): `1^1=0`, `1^0=1`, `0^1=1`, `0^0=0`. Read more about XOR [here](xor.md)
* `&` — **AND** (bitwise AND): `1&1=1`, else `0`
* `|` — **OR** (bitwise OR): `0|0=0`, else `1`
* `&&` — **Logical AND** (used for boolean expressions, not bitwise)
* `||` — **Logical OR** (boolean OR)

---
# Visualization

| Operator | Type        | Description                        |                                 |                                   |
|----------|-------------|------------------------------------|---------------------------------|-----------------------------------|
| `^`      | Bitwise XOR | Compares bits, true if bits differ |                                 |                                   |
| `&`      | Bitwise AND | Compares bits, true if both 1      |                                 |                                   |
| \`       | \`          | Bitwise OR                         | Compares bits, true if either 1 |                                   |
| `&&`     | Logical AND | True if both expressions are true  |                                 |                                   |
| \`       |             | \`                                 | Logical OR                      | True if either expression is true |
