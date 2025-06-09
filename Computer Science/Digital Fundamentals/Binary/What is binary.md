_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean Andreasian._

---
## Content
- [What is binary?](#what-is-binary)
- [Binary Representation](#binary-representation)
  - [The Length of Binary Representation](#the-length-of-binary-representation)
  - [Shortcuts](#shortcuts)

---
# What is binary?

Long story short.

- All data in hardware level is represented in `1` and `0`.
- Each binary `1` or `0` is exactly 1 bit.
- If we go deeper `1` when we have power in transistors on CPU, `0` when we don't.

---
# Binary Representation


> A **bit** (short for "binary digit") is the smallest unit of data in computing, representing either an ON (1) or OFF (0) state.

## Table

| Measure         | Value                                       |
|-----------------|---------------------------------------------|
| 1 bit           | 1 binary digit (0 or 1)                     |
| 1 byte          | 8 bits                                      |
| 1 kilobyte (KB) | 1024 bytes (8192 bits)                      |
| 1 megabyte (MB) | 1024 kilobytes (8,388,608 bits)             |
| 1 gigabyte (GB) | 1024 megabytes (8,589,934,592 bits)         |
| 1 terabyte (TB) | 1024 gigabytes (8,796,093,022,208 bits)     |
| 1 petabyte (PB) | 1024 terabytes (9,007,199,254,740,992 bits) |

---

## The Length of Binary Representation

The same binary number can be represented with different bit lengths depending on the context.

For example, the binary number `1` can be represented in various ways:

- `00000001` which is 8 bits, because there are 8 symbols in it, each 1 bit long.
- `1` which is 1 bit.

> You might ask, so "Why to use 8 bits for `1` if we can use just 1 bit?"


The answer is that it depends on the context and the system you are working with, because **each context has its own standards for binary representation**:

- In **text encoding**, characters are usually **fixed to 8 bits (ASCII or UTF-8)**.
- In **networking**, some fields are **fixed-size** (like 16-bit segments in IPv6).
- In **binary arithmetic**, numbers are often padded to **match CPU word sizes** (e.g., 32-bit, 64-bit).

**Conclusion:** Binary itself has no length limitation—it’s just a sequence of 0s and 1s, and the length of it depends on representation type.

---

## Shortcuts

- `0b` prefix. In Python, you can use the `0b` prefix to denote binary literals (leading zeros) for convenience.
  - For example, `0b1010` represents the binary number `1010`. (Which is equal to `10` in decimal.)
