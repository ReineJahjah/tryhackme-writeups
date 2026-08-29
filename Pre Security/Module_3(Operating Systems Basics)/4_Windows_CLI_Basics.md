# Room: Windows CLI Basics

**Path:** Operating Systems Basics

**Date:** August 2026

**Difficulty:** Easy

---

## Objective

Learn how to interact with Windows systems using the **Command Prompt (CMD)** instead of the graphical interface. The room covers navigating the file system, searching for and reading files, and gathering system and network information — all through text-based commands.

---

## Key Concepts

* **CLI (Command-Line Interface):** A text-based way of interacting with an operating system by typing commands instead of clicking through menus.
* **Command Prompt (CMD):** The default command-line interpreter on Windows.
* **Hidden Files:** Files that Windows does not display by default, but which are not necessarily secret or malicious.
* **System Information:** Details about a machine such as the logged-in user, hostname, OS version, and network configuration.

---

# The Windows Command Line

The **Command Prompt (CMD)** is a text-based interface used to interact with Windows. Instead of clicking through folders and menus, commands are typed directly and executed by the system.

### Why Use the CLI?

* Faster than GUI navigation
* Greater control over the system
* Essential for cybersecurity tasks
* Many security tools require terminal usage

---

# Task 1: Introduction

## Scenario

Day 2 of an internship: the supervisor leaves tasks that require using the Windows command line independently, without relying on the GUI.

---

# Task 2: Navigating Files and Finding Your First File

## Terminal Basics

The terminal allows direct interaction with the Windows operating system. Cybersecurity professionals use it daily for investigation, troubleshooting, automation, and file analysis.

## Step 1: Check Current Directory

```text
cd
```

Displays the current working directory.

## Step 2: List Files and Folders

```text
dir
```

Lists files and folders in the current directory.

## Step 3: Show Hidden Files

```text
dir /a
```

Displays all files, including hidden items.

> Hidden files are not necessarily secret — Windows simply hides them by default.

## Step 4: Move Between Directories

```text
cd Documents
cd ..
```

`cd <folder>` moves into a folder; `cd ..` moves back one level.

## Step 5: Search for a File

```text
dir /s task_brief.txt
```

Searches all subfolders for the file.

## Step 6: Navigate to the File

Use the discovered path with `cd <path>`, then confirm with `dir`.

## Step 7: Read File Contents

```text
type task_brief.txt
```

Displays the file contents directly in the terminal.

## Answers

**Q) Full path of task_brief.txt?**
A) `C:\Users\Administrator\Documents\Notes\research_yn6\exports_imv\screenshots\notes_wi6`

**Q) Message and flag inside task_brief.txt?**
A) `TASK-BRIEF-FOUND`

---

# Task 3: Gathering System Information on Windows

## Overview

Security analysts often need quick information about a system, such as who is logged in, what machine it is, which Windows version is running, and its network configuration.

## Step 1: Identify Current User

```text
whoami
```

Shows the currently logged-in user account.

## Step 2: Get Computer Name

```text
hostname
```

Displays the computer name.

## Step 3: View System Information

```text
systeminfo
```

Displays detailed operating system information.

**Important fields:** OS Name, OS Version, System Type

## Step 4: View Network Information

```text
ipconfig
```

Displays network configuration details.

**Important fields:** IPv4 Address, Default Gateway

## Answers

**Q) Computer name shown by hostname?**
A) `thmlab`

**Q) Windows version from systeminfo?**
A) `10.0.17763 N/A Build 17763`

---

# Task 4: Conclusion

## Key Skills Learned

* Navigating folders using CMD
* Listing files and hidden directories
* Searching for files
* Reading files through the terminal
* Gathering system information
* Viewing network configuration

## Why This Matters

In real-world environments, important files may be hidden and GUI access may not always be available. Analysts need fast system visibility, and CLI tools are easier to automate. The Windows command line is a foundational skill for both IT professionals and cybersecurity analysts.

---

# Key Terminology

* **CMD (Command Prompt):** Windows' text-based command-line interpreter.
* **`dir`:** Lists files and folders in the current directory.
* **`dir /a`:** Lists all files, including hidden ones.
* **`dir /s`:** Searches subfolders for a specified file.
* **`type`:** Displays the contents of a file in the terminal.
* **`whoami`:** Displays the currently logged-in user.
* **`hostname`:** Displays the computer's name.
* **`systeminfo`:** Displays detailed OS and system information.
* **`ipconfig`:** Displays network configuration details.

---

# Key Takeaways

* The **Command Prompt** allows direct, text-based interaction with Windows.
* Files can be navigated, searched for, and read entirely from the CLI, even without knowing their exact location in advance.
* Hidden files can be revealed with `dir /a` and are not inherently malicious.
* Commands like `whoami`, `hostname`, `systeminfo`, and `ipconfig` quickly reveal key details about a system's identity and network setup.
* CLI proficiency is a foundational skill for IT and cybersecurity work, since GUI access is not always available and many security tools are terminal-based.

---

## What I Learned

This room gave me hands-on practice using the Windows Command Prompt instead of relying on the GUI. Before this room, I mostly associated Windows administration with clicking through File Explorer and Settings menus — but I learned how much faster and more precise it is to navigate, search for, and read files directly from the command line.

I practiced moving between directories with `cd`, listing contents (including hidden files) with `dir` and `dir /a`, and locating a specific file across subfolders with `dir /s`. I also learned how to read a file's contents directly in the terminal using `type`, without ever opening it in a GUI application.

The second half of the room focused on gathering system information — using `whoami`, `hostname`, `systeminfo`, and `ipconfig` to quickly identify the current user, machine name, OS version, and network configuration. This reinforced why the CLI is so valuable in cybersecurity: it lets an analyst gather critical system details quickly, without depending on graphical tools that may not always be available.