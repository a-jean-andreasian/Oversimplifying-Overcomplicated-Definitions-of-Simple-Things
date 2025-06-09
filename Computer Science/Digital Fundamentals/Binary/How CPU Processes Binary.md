_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean Andreasian._

---
## Content
- [Binary processing](#binary-processing)
- [How Binary Processing Works](#how-binary-processing-works)
  - [Endianness](#endianness)
  - [The order of Bit Processing](#the-order-of-bit-processing)

---

# Binary processing

Binary processing is the manipulation of binary data, which is essential in computer science and digital electronics. 

It involves operations on binary numbers, such as addition, subtraction, multiplication, and division, as well as bitwise operations like AND, OR, XOR, and NOT.


---
## How Binary Processing Works

The processor processes binary data by manipulating bits, which are the smallest units of data in a computer.

---
### Endinianness

**Endianness**: is the order of bytes in a multi-byte data type. It can be **big-endian** (most significant byte first) or **little-endian** (least significant byte first).


---
## The order of Bit Processing
The order in which bits are processed (left to right or right to left) depends on the **architecture**, **endianness**, **logic implementation**, and even **compiler** or **microcode** optimizations.



It's _"nice to know"_ but not important for you as a software developer, no matter what some room-sitting gatekeepers might tell you.
- Your program absolutely does not depend on which side of the processor started processing the bits.
- The result of operations like `a + b`, `a - b`, or `a & b` will always be the same with the same inputs, regardless of the processor's endianness or bit processing order.


#### Why? 
Because the programming languages and compilers abstract these details away. This means this CPU processing is far deeper than your code.

#### Even with `C` you can not fully control how the bits are processed.
- `C` gives low-level access to memory (pointers, bitwise ops, manual alignment).
- But it doesn't give you precise control over how the CPU executes individual instructions, their order, or bitwise direction of evaluation.
- Things like endianness, instruction reordering, bit scanning direction are hardware-specific and abstracted away by compilers.


#### You need Assembly

- Only in assembly you can directly dictate which CPU instructions are used and in what form.
- **Maybe** also using intrinsics/extensions in `C/C++` according to my research. However, none of `C` or `C++` are in my priorities, so I haven't tested it. By the way, maybe just like those who said that.