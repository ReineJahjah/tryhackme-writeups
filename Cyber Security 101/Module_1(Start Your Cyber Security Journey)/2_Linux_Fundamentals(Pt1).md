# Linux Basics (Terminal Commands)

**Path:** Cyber Security 101 › Start Your Cyber Security Journey
**Difficulty:** Easy
**Topic:** First steps in the Linux terminal: who you are, moving around, searching, and combining commands

---

## Key Terminologies

| Term | Meaning in one line |
|------|---------------------|
| **Linux** | A lightweight, free operating system used on most servers and security tools |
| **Ubuntu** | A popular Linux distribution (a "flavour" of Linux). The lab machine uses it |
| **Terminal / CLI** | Text window where you type instructions instead of clicking (Command Line Interface) |
| **Command** | One instruction you give the computer (`ls`, `cd`, ...) |
| **Output** | The text the computer prints back after a command |
| **Directory** | Another word for folder |
| **Working directory** | The folder you are currently "standing" in |
| **Home folder** | Your personal folder (e.g. `/home/tryhackme`) |
| **Path** | The address of a file or folder (`/home/tryhackme/access.log`) |
| **Operator** | A special character that combines commands or redirects output (`&&`, `>`) |
| **Redirection** | Sending output to a file instead of the screen |
| **Overwrite vs append** | Replace the file's content vs add to the bottom of it |
| **Log file** | A file where a system or server records events (e.g. web requests) |
| **Flag** | In TryHackMe, a secret text like `THM{...}` that proves you found something |
| **PoS** | Point of Sale: the checkout tills in shops, which often run Linux |

---

## Task 1: Introduction

### The idea in simple words
Linux is an operating system like Windows, but most of your work happens by **typing commands** instead of clicking. It looks scary at first, but you only need a small set of commands to do most things.

### Why it matters in cyber security
- Most **servers**, **hacking tools** and **security tools** run on Linux.
- As a SOC analyst you will search logs, investigate machines and run tools, all from the terminal.
- Linux is also everywhere without you noticing: websites, phones, car dashboards, shop tills, and even traffic light controllers and industrial sensors. This is why attackers and defenders both care about it.

### Lab machine tips
- Press **Start Lab Machine** and the Linux machine opens in your browser.
- The card at the top of the room shows the **IP address** and an **expiry timer**.
- Terminate the machine when you finish, so you don't waste your time quota.

---

## Task 2: Talking to Linux

### The idea in simple words
Using Linux is like a **conversation**: you type an instruction, the machine replies with output.

### Commands

| Command | What it does |
|---------|--------------|
| `whoami` | Shows which user you are right now |
| `echo` | Prints the text you give it |

```bash
whoami
echo TryHackMe
echo "hello world"
```

### Understand it
- **Why `whoami` matters:** your user decides what you are *allowed* to do. A normal user can't change system files, while `root` (the administrator) can do anything. In real work you constantly check which user you are, especially after gaining access to a machine.
- **Why quotes with `echo`:** quotes tell Linux "this whole sentence is one piece of text". They are needed for multiple words.
- **Why `echo` is more important than it looks:** it is the simplest way to **create output**, and later in the room you will send that output into files. That idea (create output, then send it somewhere) is used everywhere in security work.

### Tip
Press the **up arrow** to bring back previous commands instead of retyping them.

---

## Task 3: Finding Your Way Around

### The idea in simple words
Without a mouse, you need four commands to move through the file system.

| Command | Meaning | Think of it as |
|---------|---------|----------------|
| `pwd` | Print working directory | "Where am I?" |
| `ls` | List | "What's in here?" |
| `cd` | Change directory | "Go into this folder" |
| `cat` | Show file contents | "Open and read this file" |

### Workflow to remember
```bash
pwd             # where am I?
ls              # what's here?
cd foldername   # go into a folder
ls              # what's inside it?
cat file.txt    # read the file
```

### Understand it
- **Colours:** in this terminal, folders are shown in **blue**. This is how you tell folders from files at a glance, and it is also the easiest way to count folders in an `ls` output.
- **Working directory:** commands act on the folder you are in. If you `cd` into a folder, `ls` now shows *that* folder's content.
- **Lost?** Run `pwd`. It always tells you exactly where you are.

### Extra tips (not covered in the room)
| Command | What it does |
|---------|--------------|
| `cd ..` | Go up one folder |
| `cd ~` | Go straight to your home folder |
| `ls -la` | Show **all** files, including hidden ones (names starting with `.`), with details |
| `cat` only works on files | Using it on a folder gives an error |

### Finding a file inside a folder
Folders look empty from the outside. To find which one holds a file, `cd` into each folder and run `ls`, or use `ls` followed by the folder name (e.g. `ls foldername`) to peek inside without moving.

---

## Task 4: Let the Machine Do the Searching

### The idea in simple words
Instead of scrolling through hundreds of lines, let Linux search for you.

| Command | Searches for | Example |
|---------|--------------|---------|
| `find` | **Files by name** | `find -name passwords.txt` |
| `grep` | **Text inside files** | `grep "password123" passwords.txt` |

### `find` vs `grep` (the part people mix up)
- `find` answers **"where is the file?"**. It looks at file *names*.
- `grep` answers **"is this word inside the file?"**. It looks at the file's *contents* and prints every line that matches.

### Why this matters in security
- **Log files** (like `access.log`, a web server's record of every request) can have thousands of lines. Analysts use `grep` to pull out only what they care about: an IP address, a username, an error, a suspicious URL.
- `find` helps locate configuration files, passwords left in files, and other interesting files on a compromised machine.

### Useful variations (not covered in the room)
```bash
find / -name passwords.txt     # search the whole system, not just the current folder
grep -i "thm" access.log       # -i ignores upper/lower case
grep -c "GET" access.log       # -c counts matching lines instead of printing them
```
`find /` may print many "Permission denied" lines. That's normal when you are not root.

### Getting the flag
The room already gives the idea: search the log for the text pattern that all flags start with (`THM`) and copy the full result.

---

## Task 5: Shell Operators

### The idea in simple words
**Operators** are special characters that tell Linux *how* to run commands together or *where* to send output.

### Combining commands

| Operator | Behaviour | Analogy |
|----------|-----------|---------|
| `&` | Starts the command and **doesn't wait**; it runs in the background | Putting a pot on the stove and walking away |
| `&&` | Runs the 2nd command **only after** the 1st finishes (and only if it succeeded) | Dominoes: one falls, then the next |

```bash
sleep 30 &              # runs in the background, you can keep typing
mkdir test && cd test   # create the folder, then enter it
```

**Key point:** if the first command with `&&` fails, the second one never runs. That is a safety feature.

### Redirecting output

| Operator | Behaviour |
|----------|-----------|
| `>` | Sends output to a file and **overwrites** everything already in it |
| `>>` | Sends output to a file and **adds to the bottom**, keeping the old content |

```bash
echo hey > welcome      # creates "welcome" containing: hey
echo hello >> welcome   # now it contains both lines
cat welcome             # verify
```

### Understand it
- **Overwrite vs append:** `>` is dangerous because it deletes what was there. When you want to keep old data (like building a list or a log), use `>>`.
- **Where it's used:** saving the results of a command to a file as evidence (e.g. `grep "THM" access.log > results.txt`) is a very common habit in investigations.
- **Verify with `cat`:** after redirecting, check the file with `cat` to make sure it contains what you expected.

---

## Commands Summary

| Command | What it does |
|---------|--------------|
| `whoami` | Shows the current user |
| `echo "text"` | Prints text |
| `pwd` | Shows the current location |
| `ls` | Lists files and folders |
| `cd <folder>` | Moves into a folder |
| `cat <file>` | Prints a file's contents |
| `find -name <file>` | Searches for a file by name |
| `grep "text" <file>` | Searches for text inside a file |
| `cmd1 & cmd2` | Runs `cmd1` in the background |
| `cmd1 && cmd2` | Runs `cmd2` after `cmd1` finishes |
| `cmd > file` | Saves output, overwriting the file |
| `cmd >> file` | Saves output, appending to the file |