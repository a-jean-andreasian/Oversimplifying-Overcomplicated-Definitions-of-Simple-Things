_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean Andreasian._

---
## Content

- [Introduction to the conversion approach](#introduction-to-the-convertion-approach)
  - [Step-by-step example](#step-by-step-example)
  - [Visualization of the example](#visualization-of-the-example)
  - [Quick Check: Convert back to decimal](#quick-check-convert-back-to-decimal)
- [Shortcuts](#shortcuts)
  - [Shortcut 1: Memorize Key Binary Values](#shortcut-1-memorize-key-binary-values)
  - [Shortcut 2: Use Doubling](#shortcut-2-use-doubling)
  - [Shortcut 3: Recognize Common Patterns](#shortcut-3-recognize-common-patterns)
- [How to count other data](#how-to-count-other-data)
  - [ACII](#ascii)
  - [UTF-8](#utf-8)
  - [UTF-16](#utf-16)
  - [UTF-32](#utf-32)
- [Sandbox: Trying to count](#sandbox-trying-to-count)
---
# Introduction to the convertion approach

To convert a number into binary, we use the **division by 2 method**, which repeatedly divides the number by 2 and
records the remainders.

---
## **Step-by-step example** 

The number is 174.

1. **Divide** the number by 2.
2. **Write down the remainder** (0 or 1).
3. **Repeat** until you reach 0.
4. **Read the remainders from bottom to top**.

---

## **Visualization of the example**

| Division | Quotient | Remainder |
|----------|----------|-----------|
| 174 ÷ 2  | **87**   | 0         |
| 87 ÷ 2   | **43**   | 1         |
| 43 ÷ 2   | **21**   | 1         |
| 21 ÷ 2   | **10**   | 1         |
| 10 ÷ 2   | **5**    | 0         |
| 5 ÷ 2    | **2**    | 1         |
| 2 ÷ 2    | **1**    | 0         |
| 1 ÷ 2    | **0**    | 1         |

Now, reading from **bottom to top**, we get:  
**174 = 10101110₂**

---
## **Quick Check: Convert back to decimal**

Going from right to left of `10101110`:

- 0 × 2<sup>0</sup> = 0
- 1 × 2<sup>1</sup> = 2
- 1 × 2<sup>2</sup> = 4
- 1 × 2<sup>3</sup> = 8
- 0 × 2<sup>4</sup> = 0
- 1 × 2<sup>5</sup> = 32
- 0 × 2<sup>6</sup> = 0
- 1 × 2<sup>7</sup> = 128

128 + 32 + 8 + 4 + 2 = 174

---

# Shortcuts

A **quick shortcut** for estimating binary values without converting each bit manually:

---
### **Shortcut 1: Memorize Key Binary Values**

| Binary     | Decimal |
|------------|---------|
| `00000001` | **1**   |
| `00000010` | **2**   |
| `00000100` | **4**   |
| `00001000` | **8**   |
| `00010000` | **16**  |
| `00100000` | **32**  |
| `01000000` | **64**  |
| `10000000` | **128** |

Each **1** in a binary number represents one of these values.

---

### **Shortcut 2: Use Doubling**

Each bit from **right to left** is **double** the previous one.

Example:  
`101101`

- **Start from right (1, 2, 4, 8, 16, 32)**
- Add **only** where there is `1`:  
  **32 + 8 + 4 + 1 = 45** ✅

---

### **Shortcut 3: Recognize Common Patterns**

- **All 1s in 8-bit:** `11111111 = 255`
- **Halfway (first 4 bits 1s):** `11110000 = 240`
- **Alternating:** `10101010 = 170`


---
# How to count other data

How much is the symbol depends on encoding.


#### **ASCII**
- Uses **1 byte (8 bits) per character**.
- Only supports **English letters, numbers, and basic symbols**.


#### **UTF-8** (most common Unicode encoding)
- Uses **1 to 4 bytes per character**.
- **English letters** (A-Z, a-z, 0-9, symbols) → **1 byte** (same as ASCII).
- **Special characters, emojis, non-Latin scripts** → **2, 3, or 4 bytes**.

####  **UTF-16**
- Uses **2 or 4 bytes per character**.

####  **UTF-32**
- Uses **4 bytes per character** (fixed size).

---
# Sandbox: Trying to count

1. Hello: as all are ASCII symbols, `5 * 8 = 40` bits
2. Solskjær: 7 ASCII symbols and 1 UTF-8 (æ is 2 bytes), `7 * 8 + 2 * 8 = 56 + 16 = 72` bits
