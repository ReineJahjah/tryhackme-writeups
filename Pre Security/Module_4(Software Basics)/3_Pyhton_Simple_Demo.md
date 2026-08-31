# Room: Python: Simple Demo

**Path:** Pre Security

**Date:** August 2026

**Difficulty:** Easy

---

## Objective

Learn the basic building blocks of **Python programming** by creating a simple interactive number-guessing game. The room introduces variables, user input, conditional statements, loops, and basic program flow.

---

## Key Concepts

* **Python:** A high-level, general-purpose programming language that is widely used in software development, automation, data science, and cybersecurity.

* **Variable:** A named container used to store data.

* **Input:** Data provided to a program by the user.

* **Conditional:** A statement that allows a program to make decisions based on whether a condition is true or false.

* **Loop:** A programming structure that repeats a block of code while a condition is satisfied.

* **Function:** A reusable block of code that performs a specific task.

* **`if`:** Executes code when a condition is true.

* **`elif`:** Checks another condition if the previous `if` condition was false.

* **`else`:** Executes when none of the previous conditions are true.

* **`while`:** Repeats code while a condition remains true.

---

# Task 1: Introduction to Python

## What Is Python?

**Python** is a high-level, general-purpose programming language.

### High-Level

A high-level language is designed to be relatively easy for humans to read and write.

For example:

```python
print("Hello")
```

is much easier for humans to understand than machine-level binary instructions.

### General-Purpose

Python can be used for many different types of tasks, including:

* Web development
* Automation
* Data science
* Machine learning
* Scripting
* Cybersecurity

## Example Project: Guess the Number

The room uses a simple **Guess the Number** game to demonstrate basic Python programming.

The game works like this:

1. The computer chooses a secret number between `1` and `20`.
2. The user enters a guess.
3. The program checks the guess.
4. The program tells the user whether the guess is too high or too low.
5. The process repeats until the correct number is guessed.
6. The program displays the number of attempts.

### Example

```text
I'm thinking of a number between 1 and 20
Take a guess: 10
Too high, try again.
Take a guess: 5
Too low, try again.
Take a guess: 7
Too low, try again.
Take a guess: 8
You got it in 4 tries!
```

This simple game demonstrates an important programming concept:

```text
Input → Processing → Decision → Output
```

---

# Task 2: Variables

## What Are Variables?

A **variable** is a named container used to store data.

In the guessing game, we need variables to keep track of important information.

For example:

```python
secret
guess
tries
```

These variables have different purposes:

| Variable | Purpose                             |
| -------- | ----------------------------------- |
| `secret` | Stores the computer's secret number |
| `guess`  | Stores the user's current guess     |
| `tries`  | Stores the number of attempts       |

## Generating a Random Number

Python provides a `random` module that can be used to generate random values.

```python
import random

secret = random.randint(1, 20)
```

The function:

```python
random.randint(1, 20)
```

generates a random integer between `1` and `20`.

The generated value is stored in:

```python
secret
```

## Initial Variables

Before the game starts:

```python
tries = 0
guess = 0
```

We start with:

```text
tries = 0
```

because the user has not guessed yet.

We use:

```text
guess = 0
```

so the initial value cannot accidentally match the secret number, since the valid range is `1-20`.

## Displaying Text

Python uses the `print()` function to display text.

```python
print("I'm thinking of a number between 1 and 20")
```

The output is:

```text
I'm thinking of a number between 1 and 20
```

## Getting User Input

Python uses the `input()` function to receive information from the user.

```python
text = input("Take a guess: ")
```

The user's input is initially treated as **text (a string)**.

For example, if the user enters:

```text
8
```

the program receives `"8"` as text.

We can convert it into an integer using:

```python
guess = int(text)
```

Therefore:

```text
input() → string
int()   → integer
```

## Counting Attempts

Every time the user makes a guess, we increase the attempt counter:

```python
tries = tries + 1
```

For example:

```text
tries = 0
```

After one guess:

```text
tries = 1
```

After another guess:

```text
tries = 2
```

and so on.

## Answer Check

**Q) Which function displays text?**

A) `print()`

**Q) Which function converts a value into an integer?**

A) `int()`

---

# Task 3: Conditional Statements

## What Are Conditionals?

Conditional statements allow a program to **make decisions**.

The program evaluates a condition and executes different code depending on the result.

The main Python conditional keywords are:

```python
if
elif
else
```

## Game Logic

The guessing game needs to make several decisions.

The logic is:

```text
If the guess is outside 1-20
        ↓
Display "out of range"

Otherwise, if the guess is lower than the secret
        ↓
Display "Too low"

Otherwise, if the guess is higher than the secret
        ↓
Display "Too high"

Otherwise
        ↓
The guess is correct
```

## Python Implementation

```python
if guess < 1 or guess > 20:
    print("That number is out of range. Try again.")
elif guess < secret:
    print("Too low, try again.")
elif guess > secret:
    print("Too high, try again.")
else:
    print("You got it in", tries, "tries!")
```

## Understanding the Conditions

### `if`

The first condition is checked:

```python
if guess < 1 or guess > 20:
```

This checks whether the number is outside the valid range.

For example:

```text
guess = 50
```

is invalid because it is greater than `20`.

### `elif`

`elif` means **"else if"**.

```python
elif guess < secret:
```

This condition is checked if the previous `if` condition was false.

### `else`

The `else` block is the fallback case.

If none of the previous conditions were true, the guess must be correct.

```python
else:
    print("You got it in", tries, "tries!")
```

## Conditional Structure

A useful way to remember it is:

```text
if     → First condition
elif   → Another condition
else   → Everything else
```

## Answer Check

**Q) How does Python write "else if"?**

A) `elif`

**Q) What happens if the user enters `50`?**

A)

```text
That number is out of range. Try again.
```

---

# Task 4: Iterations (Loops)

## Why Use Loops?

A loop allows a program to **repeat a block of code**.

In the guessing game, the user needs to keep guessing until the correct number is found.

Instead of writing the guessing code repeatedly, we can place it inside a loop.

## While Loop

Python provides the `while` loop:

```python
while guess != secret:
```

This means:

> Keep executing the code while `guess` is not equal to `secret`.

The loop continues as long as the condition is true.

## Full Loop Logic

```python
while guess != secret:
    text = input("Take a guess: ")
    guess = int(text)

    tries = tries + 1

    if guess < 1 or guess > 20:
        print("That number is out of range. Try again.")
    elif guess < secret:
        print("Too low, try again.")
    elif guess > secret:
        print("Too high, try again.")
    else:
        print("You got it in", tries, "tries!")
```

## Loop Behavior

Suppose the secret number is:

```text
8
```

The user enters:

```text
5
```

The condition:

```python
guess != secret
```

is:

```text
5 != 8
True
```

Therefore, the loop continues.

The user guesses again:

```text
7
```

Still:

```text
7 != 8
True
```

The loop continues.

Finally:

```text
8
```

Now:

```text
8 != 8
False
```

The loop stops.

### Important Concept

A loop continues while its condition is **true** and stops when the condition becomes **false**.

```text
Condition = True
      ↓
Continue loop
      ↓
Condition = True
      ↓
Continue loop
      ↓
Condition = False
      ↓
Stop
```

## Answer Check

**Q) What type of loop is used in the game?**

A) `while`

**Q) What would the output be if the correct number was guessed in 3 tries?**

A)

```text
You got it in 3 tries!
```

---

# Task 5: Conclusion

This room introduced the basic building blocks of Python programming using a simple interactive guessing game.

## Core Programming Concepts

### Variables

Variables store information:

```python
secret = 15
tries = 0
guess = 0
```

### Input and Output

`input()` gets information from the user:

```python
guess = input("Take a guess: ")
```

`print()` displays information:

```python
print("Too high, try again.")
```

### Conditionals

Conditionals allow programs to make decisions:

```python
if
elif
else
```

### Loops

Loops allow programs to repeat instructions:

```python
while
```

## Overall Program Flow

The guessing game combines all these concepts:

```text
Generate secret number
        ↓
Get user input
        ↓
Convert input to integer
        ↓
Increase attempt counter
        ↓
Check the guess
        ↓
Too low / Too high / Invalid
        ↓
Repeat
        ↓
Correct guess
        ↓
End program
```

---

# Key Terminology

* **Python:** A high-level, general-purpose programming language.

* **Variable:** A named container used to store data.

* **Function:** A reusable piece of code that performs a specific task.

* **`print()`:** Displays output to the screen.

* **`input()`:** Gets input from the user.

* **`int()`:** Converts a value into an integer.

* **`if`:** Executes code when a condition is true.

* **`elif`:** Checks another condition when previous conditions are false.

* **`else`:** Executes when none of the previous conditions are true.

* **`while`:** Repeats code while a condition is true.

* **Loop:** A programming structure used to repeat instructions.

* **Conditional:** A programming structure used to make decisions.

---

# Key Takeaways

* **Python** is a high-level, general-purpose programming language widely used for development, automation, data science, and cybersecurity.

* **Variables** allow programs to store and manipulate information.

* `input()` is used to receive information from the user, while `print()` displays output.

* User input is initially treated as text, so `int()` can be used when an integer is required.

* **Conditional statements** allow programs to make decisions using `if`, `elif`, and `else`.

* **Loops** allow programs to repeat instructions without writing the same code multiple times.

* A `while` loop continues executing while its condition is true.

* The guessing game demonstrates how variables, input/output, conditionals, and loops can be combined to create a complete program.

* Programming is essentially about giving a computer **clear instructions and logic** that it can execute step by step.

* Python is particularly useful in cybersecurity for **automation, scripting, data processing, tool development, and security tasks**.

---

## What I Learned

This room introduced me to the basic building blocks of Python programming through a simple number-guessing game. Since I had already learned how computers represent data using binary and how characters are encoded, this room showed me the next step: how we can actually give a computer instructions and make it perform logical operations.

I learned that **variables** are used to store information that a program needs. In the guessing game, variables such as `secret`, `guess`, and `tries` store the secret number, the user's current guess, and the number of attempts.

I also learned how programs communicate with users. The `input()` function allows a program to receive information, while `print()` displays information back to the user. An important detail is that `input()` returns text, so I need to use `int()` when I want to work with the input as an integer.

The conditional statements were another important concept. Using `if`, `elif`, and `else`, the program can make decisions based on the user's input. For example, it can determine whether a number is outside the valid range, too low, too high, or correct.

Finally, I learned how **loops** allow a program to repeat instructions. The `while` loop in the guessing game continues asking for guesses until the user's guess matches the secret number. This helped me understand that a loop continues while its condition is true and stops when the condition becomes false.

The biggest thing I learned from this room is that relatively simple programming concepts can be combined to create useful logic:

```text
Variables + Input/Output + Conditions + Loops
                    ↓
               Program Logic
```

This is also important for cybersecurity because Python can later be used to automate repetitive tasks, process security-related data, interact with systems, and build simple security tools. Learning these fundamentals gives me a foundation for the scripting and automation I will need as I continue learning cybersecurity.
