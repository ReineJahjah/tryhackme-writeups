# Room: Data Representation

**Path:** Pre Security

**Date:** August 2026

**Difficulty:** Easy

---

## Objective

Understand how computers represent colors and numbers using binary, hexadecimal, and optionally octal number systems. The room explains how computers work with only two states (`0` and `1`), how bits and bytes represent information, and how RGB colors can be represented using binary and hexadecimal values.

---

## Key Concepts

* **Bit:** The smallest unit of data in computing. A bit can have a value of `0` or `1`.

* **Byte:** A group of 8 bits. A byte can represent 256 different values, from `0` to `255`.

* **Binary:** A base-2 number system using only `0` and `1`.

* **Decimal:** A base-10 number system using digits from `0` to `9`.

* **Hexadecimal:** A base-16 number system using `0-9` and `A-F`.

* **Octal:** A base-8 number system using digits from `0` to `7`.

* **RGB:** A color model using Red, Green, and Blue values to represent colors.

* **Hex Color:** A color representation using hexadecimal values, commonly written as six hexadecimal digits such as `#A3EA2A`.

---

# Task 1: Representing Colors

## How Computers Represent Colors

Computers can represent colors by combining different amounts of **Red, Green, and Blue (RGB)**.

Each color channel controls the intensity of one primary color:

* Red
* Green
* Blue

The number of possible colors depends on how many states each channel can represent.

## Representing 8 Colors

If each RGB channel can only be either **ON (`1`)** or **OFF (`0`)**, each channel has 2 possible states.

Therefore:

```text
2 × 2 × 2 = 8
```

This allows a computer to represent 8 different colors.

A combination such as:

```text
111
```

means:

* Red = ON
* Green = ON
* Blue = ON

Therefore, the resulting color is **white**.

A combination such as:

```text
100
```

means only red is ON, producing **red**.

## 8-Color RGB Table

| Binary | Meaning         | Color   |
| ------ | --------------- | ------- |
| `000`  | All colors OFF  | Black   |
| `001`  | Blue ON         | Blue    |
| `010`  | Green ON        | Green   |
| `100`  | Red ON          | Red     |
| `011`  | Green + Blue ON | Cyan    |
| `101`  | Red + Blue ON   | Magenta |
| `110`  | Red + Green ON  | Yellow  |
| `111`  | All colors ON   | White   |

## Bit

A **bit** is short for **binary digit**.

It can only have two possible values:

```text
0
1
```

One bit can therefore represent **2 states**.

## From 8 Colors to Millions of Colors

Real computer displays need far more than 8 colors.

Instead of allowing each RGB channel to have only 2 states, each channel can have **256 different intensity levels**.

Therefore:

```text
256 × 256 × 256 = 16,777,216
```

This gives more than **16 million possible colors**.

To represent 256 different values, we need **8 bits**:

```text
8 bits = 1 byte
```

Since RGB has three channels:

```text
Red   = 8 bits
Green = 8 bits
Blue  = 8 bits
```

Therefore:

```text
8 + 8 + 8 = 24 bits
```

or:

```text
3 bytes
```

This is commonly called **24-bit color**.

## Example

A color can be represented in binary as:

```text
10100011 11101010 00101010
```

This is 24 bits divided into three groups of 8 bits:

```text
10100011 → Red
11101010 → Green
00101010 → Blue
```

Although binary works well for computers, it is difficult for humans to read. This is why hexadecimal is commonly used to represent colors.

---

# Task 2: Hexadecimal Representation

## What Is Hexadecimal?

Hexadecimal is a **base-16** number system.

Instead of using only:

```text
0-9
```

hexadecimal uses:

```text
0-9 and A-F
```

The letters represent values from 10 to 15:

| Decimal | Hexadecimal | Binary |
| ------: | :---------: | :----: |
|       0 |     `0`     | `0000` |
|       1 |     `1`     | `0001` |
|       2 |     `2`     | `0010` |
|       3 |     `3`     | `0011` |
|       4 |     `4`     | `0100` |
|       5 |     `5`     | `0101` |
|       6 |     `6`     | `0110` |
|       7 |     `7`     | `0111` |
|       8 |     `8`     | `1000` |
|       9 |     `9`     | `1001` |
|      10 |     `A`     | `1010` |
|      11 |     `B`     | `1011` |
|      12 |     `C`     | `1100` |
|      13 |     `D`     | `1101` |
|      14 |     `E`     | `1110` |
|      15 |     `F`     | `1111` |

## Why Hexadecimal Is Useful

Every hexadecimal digit represents exactly **4 bits**.

For example:

```text
A = 1010
3 = 0011
E = 1110
A = 1010
2 = 0010
A = 1010
```

Therefore:

```text
A3EA2A
```

can represent:

```text
1010 0011 1110 1010 0010 1010
```

This is much easier for humans to read than a long binary sequence.

## Hexadecimal and RGB Colors

A typical RGB color uses:

```text
2 hexadecimal digits → Red
2 hexadecimal digits → Green
2 hexadecimal digits → Blue
```

For example:

```text
#A3EA2A
```

can be divided into:

```text
A3 → Red
EA → Green
2A → Blue
```

Each pair represents one byte, meaning each color channel can have a value from:

```text
00 → 0
FF → 255
```

Therefore, a 6-digit hexadecimal color can represent:

```text
256 × 256 × 256 = 16,777,216
```

different colors.

## Important Relationship

```text
1 hexadecimal digit = 4 bits
2 hexadecimal digits = 8 bits = 1 byte
```

Therefore:

```text
#RRGGBB
```

represents:

```text
RR → Red   → 1 byte
GG → Green → 1 byte
BB → Blue  → 1 byte
```

---

# Task 3: Binary Numbers

## Why Do Computers Use Binary?

Computers operate using physical systems that can distinguish between two states.

For example:

* Low and high voltage
* Magnetic polarity
* Presence or absence of light

These two states can be represented as:

```text
0
1
```

This is why computers use the **binary (base-2)** number system.

## Decimal Number System

Humans normally use decimal, which is **base-10**.

For example:

```text
213
```

can be expanded as:

```text
2 × 10² + 1 × 10¹ + 3 × 10⁰
```

which gives:

```text
2 × 100 + 1 × 10 + 3 × 1
= 200 + 10 + 3
= 213
```

## Binary Number System

Binary works in the same way, but uses powers of **2** instead of powers of 10.

For example:

```text
1001
```

can be expanded as:

```text
1 × 2³ + 0 × 2² + 0 × 2¹ + 1 × 2⁰
```

Therefore:

```text
1 × 8 + 0 × 4 + 0 × 2 + 1 × 1
= 8 + 0 + 0 + 1
= 9
```

So:

```text
1001₂ = 9₁₀
```

## Binary Place Values

For 4 bits, the place values are:

| Bit   | 2³ | 2² | 2¹ | 2⁰ |
| ----- | -: | -: | -: | -: |
| Value |  8 |  4 |  2 |  1 |

This gives the useful pattern:

```text
8  4  2  1
```

For example:

```text
1101
```

means:

```text
1×8 + 1×4 + 0×2 + 1×1
= 8 + 4 + 0 + 1
= 13
```

Therefore:

```text
1101₂ = 13₁₀
```

## Common 4-Bit Binary Values

| Binary | Decimal |
| ------ | ------: |
| `0000` |       0 |
| `0001` |       1 |
| `0010` |       2 |
| `0011` |       3 |
| `0100` |       4 |
| `0101` |       5 |
| `0110` |       6 |
| `0111` |       7 |
| `1000` |       8 |
| `1001` |       9 |
| `1010` |      10 |
| `1011` |      11 |
| `1100` |      12 |
| `1101` |      13 |
| `1110` |      14 |
| `1111` |      15 |

---

# Task 4: Hexadecimal Numbers

## Hexadecimal as Base-16

Hexadecimal uses 16 possible digits:

```text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

The values are:

```text
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

A hexadecimal number can be converted to decimal using powers of 16.

For example:

```text
9BDF
```

can be expanded as:

```text
9 × 16³ + B × 16² + D × 16¹ + F × 16⁰
```

Since:

```text
B = 11
D = 13
F = 15
```

we get:

```text
9 × 4096 + 11 × 256 + 13 × 16 + 15 × 1
= 36,864 + 2,816 + 208 + 15
= 39,903
```

Therefore:

```text
9BDF₁₆ = 39903₁₀
```

## Important Relationship

Hexadecimal is especially useful because it provides a compact representation of binary data:

```text
1 hex digit = 4 bits
```

For example:

```text
F = 1111
A = 1010
7 = 0111
```

Therefore:

```text
FA7
```

represents:

```text
1111 1010 0111
```

---

# Task 5: Optional — Octal Numbers

## What Is Octal?

Octal is a **base-8** number system.

It uses only:

```text
0 1 2 3 4 5 6 7
```

Unlike hexadecimal, octal does not use digits 8 or 9.

## Octal and Binary

Every octal digit represents exactly **3 bits**.

| Decimal | Octal | Binary |
| ------: | :---: | :----: |
|       0 |  `0`  |  `000` |
|       1 |  `1`  |  `001` |
|       2 |  `2`  |  `010` |
|       3 |  `3`  |  `011` |
|       4 |  `4`  |  `100` |
|       5 |  `5`  |  `101` |
|       6 |  `6`  |  `110` |
|       7 |  `7`  |  `111` |

Therefore:

```text
1 octal digit = 3 bits
```

## Converting Octal to Decimal

For example:

```text
357
```

can be expanded using powers of 8:

```text
3 × 8² + 5 × 8¹ + 7 × 8⁰
```

Therefore:

```text
3 × 64 + 5 × 8 + 7 × 1
= 192 + 40 + 7
= 239
```

So:

```text
357₈ = 239₁₀
```

Octal is less commonly encountered than binary and hexadecimal, but it can still appear in computing, especially in areas such as Linux file permissions.

---

# Task 6: Conclusion

Computers represent information using binary because their underlying hardware can distinguish between two physical states.

The main number systems covered are:

* **Decimal (Base-10):** Uses digits `0-9` and is commonly used by humans.
* **Binary (Base-2):** Uses `0` and `1` and is the fundamental representation used by computers.
* **Hexadecimal (Base-16):** Uses `0-9` and `A-F` and provides a compact way to represent binary data.
* **Octal (Base-8):** Uses `0-7` and groups binary digits into sets of 3.

## Bits and Bytes

A **bit** can represent two states:

```text
0 or 1
```

A **byte** contains 8 bits:

```text
8 bits = 1 byte
```

Therefore, one byte can represent:

```text
2⁸ = 256
```

different values.

## Color Representation

Modern RGB colors commonly use 24 bits:

```text
8 bits → Red
8 bits → Green
8 bits → Blue
```

Therefore:

```text
24 bits = 3 bytes
```

and the number of possible colors is:

```text
256 × 256 × 256 = 16,777,216
```

A hexadecimal RGB color is commonly written as:

```text
#RRGGBB
```

For example:

```text
#A3EA2A
```

where:

```text
A3 → Red
EA → Green
2A → Blue
```

---

# Key Terminology

* **Bit:** A binary digit that can be `0` or `1`.

* **Byte:** A group of 8 bits.

* **Binary:** Base-2 number system using `0` and `1`.

* **Decimal:** Base-10 number system using `0-9`.

* **Hexadecimal:** Base-16 number system using `0-9` and `A-F`.

* **Octal:** Base-8 number system using `0-7`.

* **RGB:** Red, Green, and Blue color model.

* **Hex Color:** A color represented using hexadecimal RGB values.

* **Base:** The number of unique digits/symbols used by a number system.

---

# Key Takeaways

* Computers fundamentally work with **two states**, represented as `0` and `1`.

* A **bit** is the smallest unit of information and can represent two states.

* **8 bits = 1 byte**, and one byte can represent 256 different values.

* Binary is **base-2**, decimal is **base-10**, hexadecimal is **base-16**, and octal is **base-8**.

* **1 hexadecimal digit represents 4 bits**, making hexadecimal a convenient and compact representation of binary data.

* **1 octal digit represents 3 bits**.

* RGB colors use three channels: **Red, Green, and Blue**.

* With 8 bits for each RGB channel, computers can represent **16,777,216 different colors**.

* A 24-bit RGB color consists of **3 bytes**, one for each color channel.

* Hexadecimal color codes such as `#A3EA2A` are a human-friendly way of representing RGB values.

* Understanding binary and hexadecimal is especially important in **cybersecurity**, where they commonly appear in IP addresses, memory values, file formats, permissions, hashes, packet data, and other low-level representations.

---

## What I Learned

This room helped me understand how computers represent information using different number systems. I learned that while humans normally use the decimal system, computers fundamentally operate using binary because their hardware can distinguish between two states, represented as `0` and `1`.

The most important concept for me was understanding the relationship between **bits, bytes, binary, and hexadecimal**. A bit can represent two states, while 8 bits make a byte and can represent 256 different values. Hexadecimal makes binary data much easier for humans to read because every hexadecimal digit represents exactly 4 bits.

I also learned how computers represent colors using the **RGB model**. With 8 bits for each of the red, green, and blue channels, a computer can represent more than 16 million colors. Hexadecimal color codes such as `#A3EA2A` provide a compact way to represent these RGB values.

The binary conversion exercises helped me understand how powers of 2 are used to calculate the decimal value of a binary number. Similarly, hexadecimal uses powers of 16, while octal uses powers of 8.

Most importantly for my cybersecurity learning, I now understand why **binary and hexadecimal are so common in security and computer science**. They provide compact ways to represent the low-level data that computers actually process, which will become useful when working with things such as networking, memory, file formats, permissions, and other security-related concepts.
