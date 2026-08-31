# Room: JavaScript: Simple Demo

**Path:** Pre Security

**Date:** August 2026

**Difficulty:** Easy

---

## Objective

Understand the basic building blocks of **JavaScript programming** by creating a simple interactive **Guess the Number** game. The room introduces variables, constants, user input, output, conditional statements, loops, and running JavaScript outside the browser using **Node.js**.

---

## Key Concepts

* **JavaScript:** A programming language commonly used to make websites interactive. It can run in browsers and on servers using Node.js.

* **Variable:** A value that can change while the program is running. Declared with `let`.

* **Constant:** A value that should not change during program execution. Declared with `const`.

* **Conditional Statement:** Allows a program to make decisions using `if`, `else if`, and `else`.

* **Loop:** Repeats a block of code while a condition remains true.

* **Node.js:** A runtime that allows JavaScript to execute outside a web browser.

* **`console.log()`:** Displays output.

* **`parseInt()`:** Converts text into an integer.

---

# Task 1: Introduction to JavaScript

## What Is JavaScript?

JavaScript is a high-level programming language widely used to make websites interactive.

Originally, JavaScript was mainly designed to run inside **web browsers**. Today, it can also run outside browsers using **Node.js**.

### Where JavaScript Runs

* **Client-side:** Inside web browsers.

* **Server-side:** Using Node.js on servers.

## Guess the Number Game

The room uses a simple game to demonstrate JavaScript programming.

The computer:

1. Generates a secret number between 1 and 20.
2. Asks the user to guess.
3. Checks the guess.
4. Provides a hint.
5. Continues until the correct number is guessed.

### Example Output

```text
I'm thinking of a number between 1 and 20
Take a guess: 10
Too high, try again.
Take a guess: 5
Too low, try again.
Take a guess: 7
You got it in 3 tries!
```

## Why Use the Same Game as Python?

The same project is used in the **Python: Simple Demo** room so that we can compare the syntax of Python and JavaScript while learning the same programming concepts.

---

# Task 2: Variables and Constants

## Variables

A variable stores data that can change while a program is running.

In the game, we need:

* `tries` → Number of attempts
* `guess` → Current user guess

### Declaring Variables

JavaScript uses the `let` keyword:

```javascript
let tries = 0;
let guess = 0;
```

Starting both values at `0` means the user has not made a guess yet.

## Constants

A constant stores a value that should not change.

JavaScript uses the `const` keyword.

### Generating a Secret Number

```javascript
const secret = Math.floor(Math.random() * (20)) + 1;
```

### How It Works

**`Math.random()`**

Generates a random decimal between `0` and less than `1`.

Example:

```text
0.372...
```

**Multiply by 20**

```text
0.372 × 20 = 7.44
```

**`Math.floor()`**

Removes the decimal part:

```text
7.44 → 7
```

**Add 1**

This changes the possible range from:

```text
0–19
```

to:

```text
1–20
```

Therefore, the secret number can be any integer from **1 to 20**.

## Displaying Output

JavaScript uses `console.log()` to display text:

```javascript
console.log("I'm thinking of a number between 1 and 20");
```

## Answers

**Q) What keyword declares a variable?**

A) `let`

**Q) What keyword declares a constant?**

A) `const`

**Q) What method displays text?**

A) `console.log()`

---

# Task 3: User Input

## Getting User Input

When running JavaScript with Node.js, the `readline` module can be used to receive keyboard input.

```javascript
const text = await rl.question("Take a guess: ");
```

The user's input is initially stored as **text**.

For example:

```text
"15"
```

## Converting Text to a Number

Use `parseInt()` to convert the text into an integer:

```javascript
guess = parseInt(text, 10);
```

Therefore:

```text
"15" → 15
```

This is important because we need a number to perform numerical comparisons.

## Readline Module

The program imports the required modules:

```javascript
import * as readline from "node:readline/promises";
import { stdin as input, stdout as output } from "node:process";
```

### Creating the Interface

```javascript
const rl = readline.createInterface({ input, output });
```

This creates a communication interface between:

* **Input** → Keyboard
* **Output** → Screen

## Closing the Interface

When the program finishes, the interface should be closed:

```javascript
rl.close();
```

## Program Flow

At this point, the program can:

1. Create the readline interface.
2. Generate a random secret number.
3. Create variables.
4. Display the game message.
5. Ask the user for a guess.
6. Convert the input to a number.
7. Count the attempt.
8. Close the interface when finished.

## Answer

**Q) Which method converts text into an integer?**

A) `parseInt()`

---

# Task 4: Conditional Statements

## Why Use Conditionals?

The program needs to respond differently depending on the user's guess.

JavaScript uses:

* `if` → First condition
* `else if` → Another condition if the previous one was false
* `else` → Runs when none of the previous conditions are true

## Decision Logic

### Case 1: Out of Range

If:

```text
guess < 1
OR
guess > 20
```

Display:

```text
That number is out of range. Try again.
```

### Case 2: Guess Too Low

If:

```text
guess < secret
```

Display:

```text
Too low, try again.
```

### Case 3: Guess Too High

If:

```text
guess > secret
```

Display:

```text
Too high, try again.
```

### Case 4: Correct Guess

If the guess equals the secret number:

```text
You got it!
```

## JavaScript Implementation

```javascript
if (guess < 1 || guess > 20) {
    console.log("That number is out of range. Try again.");
} else if (guess < secret) {
    console.log("Too low, try again.");
} else if (guess > secret) {
    console.log("Too high, try again.");
} else {
    console.log("You got it in", tries, "tries!");
}
```

## Important Operators

| Operator | Meaning      |
| -------- | ------------ |
| `<`      | Less than    |
| `>`      | Greater than |
| `\|\|`   | OR           |

For example:

```javascript
guess < 1 || guess > 20
```

means:

```text
guess is less than 1 OR guess is greater than 20
```

## Answers

**Q) Secret = 10, Guess = 15**

A) `Too high, try again.`

**Q) Secret = 10, Guess = 35**

A) `That number is out of range. Try again.`

---

# Task 5: Iterations

## Why Use Loops?

The current version only allows the user to make one guess.

A loop allows the program to repeatedly ask for guesses until the correct number is found.

## While Loop

JavaScript uses a `while` loop to repeat code while a condition is true.

```javascript
while (guess !== secret) {
    // repeat code
}
```

## What Does `!==` Mean?

The operator:

```text
!==
```

means **not equal to**.

Therefore:

```javascript
guess !== secret
```

means:

```text
guess is not equal to secret
```

As long as this condition is true, the loop continues.

Once:

```text
guess === secret
```

the condition becomes false and the loop stops.

## Full Loop

```javascript
while (guess !== secret) {
    const text = await rl.question("Take a guess: ");
    guess = parseInt(text, 10);

    tries = tries + 1;

    if (guess < 1 || guess > 20) {
        console.log("That number is out of range. Try again.");
    } else if (guess < secret) {
        console.log("Too low, try again.");
    } else if (guess > secret) {
        console.log("Too high, try again.");
    } else {
        console.log("You got it in", tries, "tries!");
    }
}
```

## Loop Behavior

The loop repeatedly:

1. Asks the user for input.
2. Converts the input into a number.
3. Increments `tries`.
4. Checks the guess.
5. Displays an appropriate message.
6. Repeats if the guess is incorrect.
7. Stops when the guess equals the secret number.

### Example Session

```text
I'm thinking of a number between 1 and 20
Take a guess: 10
Too low, try again.
Take a guess: 15
Too high, try again.
Take a guess: 13
Too low, try again.
Take a guess: 14
You got it in 4 tries!
```

## Answers

**Q) What type of loop was used?**

A) `while`

**Q) Which variable tracks the number of attempts?**

A) `tries`

**Q) How is "not equal" written in JavaScript?**

A) `!==`

---

# Task 6: Conclusion

This room introduced the basic building blocks of JavaScript programming by creating a simple interactive game.

## Key Concepts

* **`let`** → Declares variables whose values can change.
* **`const`** → Declares constants whose values should not change.
* **`console.log()`** → Displays output.
* **`parseInt()`** → Converts text into an integer.
* **`if / else if / else`** → Makes decisions.
* **`while`** → Repeats code while a condition is true.
* **Node.js** → Allows JavaScript to run outside the browser.

## Benefits of JavaScript

* Runs directly in web browsers.
* Can run on servers using Node.js.
* Used to build interactive web applications.
* Has a large developer ecosystem.
* Supports both frontend and backend development.

---

# Key Terminology

* **JavaScript:** A programming language commonly used for interactive web applications.

* **Variable:** A named storage location whose value can change.

* **Constant:** A named value that should not change during execution.

* **`let`:** JavaScript keyword used to declare a variable.

* **`const`:** JavaScript keyword used to declare a constant.

* **`console.log()`:** Displays output in the console.

* **`parseInt()`:** Converts a string into an integer.

* **Conditional:** A statement that allows a program to make decisions.

* **Loop:** Repeats a block of code while a condition is true.

* **`while`:** A loop that continues while its condition is true.

* **Node.js:** A JavaScript runtime that allows JavaScript to run outside a browser.

---

# Key Takeaways

* JavaScript can run both **inside web browsers** and **outside browsers using Node.js**.

* Variables declared with `let` can change during program execution, while `const` is used for values that should remain fixed.

* User input received through Node.js is text, so `parseInt()` can be used when an integer is required.

* **Conditional statements** allow programs to make decisions based on different conditions.

* The `while` loop allows a program to repeatedly execute instructions until a condition becomes false.

* Operators such as `<`, `>`, `||`, and `!==` are important for controlling program logic.

* Programming concepts such as **variables, conditions, and loops** are not limited to one language. The same concepts appear in Python, JavaScript, and many other programming languages.

---

# What I Learned

This room helped me understand the basic structure of JavaScript by building the same **Guess the Number** game that I previously saw in Python. This made it easier to recognize that the underlying programming logic is often the same even when the syntax changes.

I learned how to declare variables with `let` and constants with `const`, generate random numbers using `Math.random()` and `Math.floor()`, display information using `console.log()`, and receive and convert user input using Node.js and `parseInt()`.

The conditional statements showed me how JavaScript can make decisions based on different conditions using `if`, `else if`, and `else`. I also learned how the `while` loop can repeatedly execute code until the user's guess matches the secret number.

The most important lesson is that **variables store information, conditionals make decisions, and loops repeat actions**. These are fundamental programming concepts that can be applied across different programming languages, not just JavaScript.
