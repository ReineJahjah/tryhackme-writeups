# Room: Data Encoding

**Path:** Pre Security

**Date:** August 2026

**Difficulty:** Easy

---

## Objective

Understand how computers represent text, symbols, and emojis as numbers. The room introduces **character encoding**, explains **ASCII and its limitations**, and covers **Unicode** and the UTF-8, UTF-16, and UTF-32 encoding formats.

---

## Key Concepts

* **Encoding:** A standard mapping that tells a computer which numerical value represents a particular character.

* **ASCII:** An early character encoding standard using values from `0-127` to represent English letters, digits, punctuation, and control characters.

* **Unicode:** A universal character set that assigns a unique code point to characters from languages and writing systems around the world.

* **Code Point:** A unique number assigned to a character by Unicode, written in a format such as `U+0041`.

* **UTF-8:** A Unicode encoding that uses 1 to 4 bytes per character and is the most common encoding on the modern web.

* **UTF-16:** A Unicode encoding that uses 2 or 4 bytes per character.

* **UTF-32:** A Unicode encoding that uses exactly 4 bytes for every Unicode code point.

* **Gibberish:** Incorrectly displayed text that can occur when data is decoded using a different encoding from the one used to encode it.

---

# Task 1: Introduction to Data Encoding

## Representation vs Encoding

Computers store information as **bits and numbers**.

In the previous room, we learned that everything ultimately becomes binary data. However, numbers alone do not tell us what a particular value means.

For example, a number could represent:

* A letter
* A digit
* A punctuation mark
* A color
* An emoji

**Encoding** provides the agreed-upon mapping between numbers and characters.

For example, if an encoding standard says:

```text
65 → A
```

then a computer can store the number `65` and interpret it as the character `A`.

Therefore:

```text
Character → Numeric code → Binary data
```

When displaying the data:

```text
Binary data → Numeric code → Character
```

Both sides must understand the same encoding.

## Why Encoding Matters

If a file is saved using one encoding but opened using another incompatible encoding, characters may appear as strange or incorrect symbols.

This is commonly called **garbled text** or **gibberish**.

Therefore:

> The same encoding must be understood when data is encoded and decoded.

---

# Task 2: ASCII

## What Is ASCII?

**ASCII** stands for:

```text
American Standard Code for Information Interchange
```

ASCII is an early character encoding standard introduced in **1963**.

The original ASCII standard uses **7 bits** and supports:

```text
0 - 127
```

This gives:

```text
2⁷ = 128
```

possible values.

ASCII represents:

* English uppercase letters
* English lowercase letters
* Digits
* Punctuation
* Control characters

## ASCII Examples

Some important ASCII values are:

| Character | Decimal | Hexadecimal | Binary     |
| --------- | ------: | ----------: | ---------- |
| `0`       |      48 |        `30` | `00110000` |
| `9`       |      57 |        `39` | `00111001` |
| `A`       |      65 |        `41` | `01000001` |
| `X`       |      88 |        `58` | `01011000` |
| `Y`       |      89 |        `59` | `01011001` |
| `Z`       |      90 |        `5A` | `01011010` |
| `a`       |      97 |        `61` | `01100001` |
| `b`       |      98 |        `62` | `01100010` |
| `c`       |      99 |        `63` | `01100011` |
| `z`       |     122 |        `7A` | `01111010` |
| `DEL`     |     127 |        `7F` | `01111111` |

## Useful ASCII Patterns

ASCII characters are arranged in useful sequences.

For lowercase letters:

```text
a = 61
b = 62
c = 63
...
z = 7A
```

For uppercase letters:

```text
A = 41
B = 42
C = 43
...
Z = 5A
```

For digits:

```text
0 = 30
1 = 31
2 = 32
...
9 = 39
```

This means that if you know the ASCII value of one character, you can often determine the values of nearby characters.

---

# Task 3: "TryHackMe" in ASCII

Suppose we create a file containing:

```text
TryHackMe
```

The computer does not store the word as letters directly. Each character is stored using its numerical encoding.

Using ASCII, the binary representation is:

```text
01010100 01110010 01111001 01001000 01100001 01100011 01101011 01001101 01100101
```

Each 8-bit group represents one character.

For example:

```text
01010100 → T
01110010 → r
01111001 → y
01001000 → H
01100001 → a
01100011 → c
01101011 → k
01001101 → M
01100101 → e
```

A newline character is also stored:

```text
00001010
```

This represents a new line (`\n`).

## Hexadecimal Representation

Binary is difficult for humans to read, so hexadecimal is commonly used instead.

The same data can be represented as:

```text
54 72 79 48 61 63 6B 4D 65 0A
```

For example:

```text
54 → T
72 → r
79 → y
48 → H
61 → a
63 → c
6B → k
4D → M
65 → e
0A → newline
```

This demonstrates an important relationship:

```text
Binary → Hexadecimal → Character
```

---

# Task 4: Limitations of ASCII

## Why ASCII Is Not Enough

ASCII was designed mainly for English text.

It supports:

```text
A-Z
a-z
0-9
punctuation
control characters
```

However, many languages contain characters that ASCII cannot represent.

Examples include:

```text
ñ
é
ß
ü
ł
č
ř
```

ASCII uses only 7 bits:

```text
2⁷ = 128 characters
```

Even adding another bit would only provide 256 possible values, which is still not enough to represent all characters used by languages around the world.

## Regional Encodings

Different standards were created to support additional characters.

Examples include:

### ISO-8859-1 (Latin-1)

Supports many Western European languages, including characters such as:

```text
é
ç
ñ
ü
ß
```

### ISO-8859-2 (Latin-2)

Supports many Central and Eastern European languages, including:

```text
ł
ń
č
ř
ș
ț
```

## Encoding Compatibility Problem

Different regional encodings can assign different meanings to the same numerical value.

For example, a document saved using one encoding may display incorrectly if opened using another encoding.

This can result in:

```text
Correct character → Wrong encoding → Incorrect character
```

This problem helped motivate the development and adoption of **Unicode**.

---

# Task 5: Unicode

## What Is Unicode?

**Unicode** is a universal character standard designed to represent characters from languages and writing systems around the world.

Instead of creating separate standards for different languages, Unicode assigns each character a unique **code point**.

Examples:

```text
U+0041 → A
U+03A9 → Ω
U+3042 → あ
```

Unicode can represent:

* English
* Arabic
* Greek
* Japanese
* Chinese
* European languages
* Mathematical symbols
* Chess symbols
* Emojis
* Many other writing systems

## Unicode Code Points

A Unicode code point is written using:

```text
U+XXXX
```

where `XXXX` represents the character's hexadecimal value.

For example:

```text
A → U+0041
Ω → U+03A9
あ → U+3042
ت → U+062A
♞ → U+265E
```

The important idea is:

```text
Unicode character → Unique code point
```

Unicode itself defines the characters and their code points. Formats such as **UTF-8, UTF-16, and UTF-32** determine how those code points are encoded into bytes.

---

# Task 6: UTF-8, UTF-16, and UTF-32

Unicode provides code points, but computers still need to store those code points as bytes.

This is where **UTF** encoding formats are used.

UTF stands for **Unicode Transformation Format**.

The three important formats covered in this room are:

* UTF-8
* UTF-16
* UTF-32

---

## UTF-8

**UTF-8** is extremely common, especially on the modern web.

It uses between:

```text
1 - 4 bytes
```

depending on the character.

### Examples

ASCII characters use exactly 1 byte.

For example:

```text
A → U+0041 → 1 byte in UTF-8
```

Other characters require more bytes.

For example:

```text
Ω → U+03A9 → 2 bytes
```

An emoji such as:

```text
🔥 → U+1F525 → 4 bytes
```

UTF-8 is efficient because common ASCII characters only require one byte.

### Important Property

UTF-8 is **backward compatible with ASCII**.

The ASCII range:

```text
U+0000 - U+007F
```

uses exactly the same byte values in UTF-8.

---

## UTF-16

UTF-16 generally uses:

```text
2 or 4 bytes
```

Common characters can fit into 2 bytes.

Some characters, such as many emojis and less common Unicode characters, require 4 bytes.

For example:

```text
A → U+0041
```

uses 2 bytes in UTF-16.

The fire emoji:

```text
🔥 → U+1F525
```

uses two 16-bit units, totaling 4 bytes:

```text
U+D83D U+DD25
```

---

## UTF-32

UTF-32 is simpler but uses more storage.

Every Unicode code point occupies exactly:

```text
4 bytes
```

For example:

```text
A → U+00000041
🔥 → U+0001F525
```

The advantage is that every code point has the same size.

The disadvantage is that it uses more memory than UTF-8 or UTF-16 for many characters.

---

# Task 7: Unicode Examples

Unicode can represent characters from many different languages and systems.

| Character | Unicode Code Point | Meaning                        |
| --------- | ------------------ | ------------------------------ |
| `A`       | `U+0041`           | Latin A                        |
| `Ω`       | `U+03A9`           | Greek Omega                    |
| `あ`       | `U+3042`           | Japanese Hiragana              |
| `龍`       | `U+9F8D`           | Chinese character for "dragon" |
| `😊`      | `U+1F60A`          | Smiling face                   |
| `ت`       | `U+062A`           | Arabic letter Taa              |
| `♞`       | `U+265E`           | Black chess knight             |
| `🔥`      | `U+1F525`          | Fire emoji                     |

The important point is that the computer does not fundamentally "understand" these symbols as pictures or letters.

They are represented using numerical values.

For example:

```text
😊
```

has the Unicode code point:

```text
U+1F60A
```

---

# Task 8: Encoding Emojis

Emojis are also Unicode characters.

For example:

```text
🔥 → U+1F525
😊 → U+1F60A
```

They are encoded into bytes according to the chosen Unicode encoding.

For UTF-32:

```text
🔥 → U+0001F525
```

The binary representation is:

```text
0000 0000 0000 0001 1111 0101 0010 0101
```

Therefore, emojis are not fundamentally different from letters from the computer's perspective.

They are also represented using numerical code points.

---

# Task 9: Why Does Gibberish Happen?

Sometimes text appears as strange symbols such as:

```text
Ã©
�
```

or other unexpected characters.

One common reason is an **encoding mismatch**.

For example:

```text
Data encoded using Encoding A
                ↓
Data decoded using Encoding B
                ↓
Incorrect characters
```

The actual bytes may be correct, but the program interprets those bytes using the wrong encoding.

## Important Idea

Encoding and decoding must agree.

```text
Encode → Store/Transmit → Decode
```

If the encoding used during decoding does not match the original encoding, the result may be corrupted or displayed incorrectly.

---

# Task 10: Conclusion

Data encoding provides a way for computers to represent characters using numerical values.

The main concepts covered are:

* **ASCII:** Early encoding standard for English characters using values from `0-127`.
* **Unicode:** Universal character set capable of representing characters from languages and writing systems around the world.
* **UTF-8:** Variable-length Unicode encoding using 1-4 bytes and widely used on the web.
* **UTF-16:** Unicode encoding using 2 or 4 bytes.
* **UTF-32:** Unicode encoding using exactly 4 bytes per code point.
* **Code Point:** Unique Unicode number assigned to a character.
* **Encoding mismatch:** Can cause text to appear as gibberish or incorrect characters.

The overall process can be viewed as:

```text
Character
    ↓
Unicode / ASCII code
    ↓
Encoded into bytes
    ↓
Stored or transmitted
    ↓
Decoded
    ↓
Character displayed
```

---

# Key Terminology

* **Encoding:** A defined mapping between data values and their meanings.

* **ASCII:** A 7-bit character encoding standard representing values from `0-127`.

* **Unicode:** A universal character set covering characters from many languages and writing systems.

* **Code Point:** The unique number assigned to a Unicode character.

* **UTF-8:** Variable-length Unicode encoding using 1-4 bytes.

* **UTF-16:** Unicode encoding using 2 or 4 bytes.

* **UTF-32:** Unicode encoding using exactly 4 bytes.

* **Garbled Text:** Incorrectly displayed text caused by problems such as encoding mismatches.

* **Byte:** A group of 8 bits used to store encoded data.

---

# Key Takeaways

* Computers store text as **numbers and bytes**, not directly as letters or symbols.

* **Encoding** provides the agreed-upon mapping between numerical values and characters.

* **ASCII** uses 7 bits and supports 128 values, mainly covering English letters, numbers, punctuation, and control characters.

* ASCII is limited because it cannot represent characters from all languages.

* **Unicode** provides a universal system where each character has a unique code point.

* Unicode code points are commonly written in hexadecimal form, such as `U+0041` for `A`.

* **UTF-8, UTF-16, and UTF-32** are different ways of encoding Unicode code points into bytes.

* UTF-8 uses **1-4 bytes**, UTF-16 uses **2 or 4 bytes**, and UTF-32 always uses **4 bytes**.

* UTF-8 is especially important because it is widely used on the **modern web** and is compatible with ASCII.

* Emojis are also represented using Unicode code points, just like letters and symbols.

* Incorrectly interpreting data with the wrong encoding can result in **gibberish or corrupted-looking text**.

* Understanding encoding is important in cybersecurity because analysts frequently encounter raw bytes, hexadecimal data, network traffic, files, logs, URLs, and other data that must be correctly interpreted.

---

## What I Learned

This room helped me understand how computers represent text and characters after learning about binary and hexadecimal in the previous room. I learned that characters are ultimately represented using numbers, and an **encoding** defines the relationship between those numbers and their meanings.

I first learned about **ASCII**, which uses values from `0-127` to represent English letters, numbers, punctuation, and control characters. Seeing how `TryHackMe` can be converted into binary and hexadecimal made it much clearer that a text file is ultimately stored as numerical data.

I also learned why ASCII is not enough for modern computing. It was designed primarily for English, so it cannot represent the huge number of characters needed for languages such as Arabic, Japanese, and Chinese. Different regional encodings tried to solve this problem, but using different encodings could cause the same data to be displayed incorrectly.

This led to **Unicode**, which provides a universal system for assigning unique code points to characters from languages and writing systems around the world. I learned that Unicode itself defines the characters and their code points, while **UTF-8, UTF-16, and UTF-32** define how those code points are encoded into bytes.

The most important thing I took from this room is the difference between a **character, its Unicode code point, and its encoding**. For example, `A` has the Unicode code point `U+0041`, but that code point can be represented using different encoding formats such as UTF-8, UTF-16, or UTF-32.

I also learned why text can sometimes appear as strange or unreadable characters. If data is decoded using a different encoding from the one used to encode it, the bytes may be interpreted incorrectly and produce gibberish.

For cybersecurity, this is an important foundation because I will often encounter data represented as **bytes, hexadecimal values, encoded strings, and raw network or file data**. Understanding how computers convert between characters, numbers, and bytes will make it easier to understand and analyze that data later.
