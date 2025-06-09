_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean Andreasian._

---
## Content
- [What is microcode?](#what-is-microcode)
  - [The flow](#the-flow)
  - [Analogy](#analogy)
  - [Why it exists](#why-it-exists)
  - [Key points](#key-points)
- [You can’t touch microcode in C](#you-cant-touch-microcode-in-c)

---
# What is microcode?

**Microcode** is a low-level layer of instructions **inside the CPU** that defines how machine instructions (like `ADD`, `MOV`, `XOR`) are actually executed by the hardware.

---
## The flow

* You write code in **C**, it compiles to **assembly/machine code**.
* The CPU sees machine instructions like `0x01` (ADD), `0x31` (XOR), etc.
* But even *those* aren’t atomic inside the CPU, each instruction is **broken down into micro-operations** by **microcode**.
* Microcode tells the CPU's internal circuits *how* to do that instruction.

---

### Analogy:

Machine code is like saying "bake a cake"
Microcode is the detailed steps: "crack eggs, mix flour, heat oven..."

---

### Why it exists:

* It allows complex instructions to be supported in hardware (especially in CISC CPUs like x86).
* Enables CPU vendors to **patch bugs** in hardware via microcode updates.
* Makes it possible to change instruction behavior **without redesigning the physical chip**.

---

### Key points:

* Not programmable by regular users.
* Can be updated by the OS or BIOS (e.g. Intel microcode updates).
* Found in **CISC** CPUs (like x86); **RISC** CPUs (like ARM) often avoid microcode or use much less.

---

### You can’t touch microcode in C.

It’s **deep CPU internals**, only accessible to CPU vendors or with special tools/hacks.
