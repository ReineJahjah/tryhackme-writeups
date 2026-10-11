# Linux Fundamentals Part 2

**Path:** Cyber Security 101 › Start Your Cyber Security Journey
**Difficulty:** Easy
**Topic:** Logging in remotely with SSH, using arguments, managing files, important directories, and permissions

---

## Key Terminologies

| Term | Meaning in one line |
|------|---------------------|
| **SSH** | Protocol that lets you log in to another computer over the network, with encrypted traffic |
| **Protocol** | An agreed set of rules two devices follow to talk to each other |
| **Remote machine** | A computer you control from another computer, usually without a desktop |
| **AttackBox** | TryHackMe's machine that acts as *your own computer* (you attack/work from here) |
| **Lab / target machine** | The machine you log in to and practise on |
| **IP address** | The address of a machine on the network |
| **Argument / flag / switch** | An extra option added to a command with `-` (short) or `--` (long) |
| **Hidden file** | A file or folder whose name starts with a dot (`.hiddenfolder`) |
| **man page** | The built-in manual for a command |
| **Relative / full path** | A path from where you are vs. a path from the very top `/` |
| **Root directory `/`** | The top of the whole file system (the "trunk" of the tree) |
| **root user** | The all-powerful administrator account |
| **`/root`** | The home folder of the root user (not the same as `/`) |
| **`/etc`** | System and program configuration files |
| **`/var`** | Data that changes often, like logs (`/var/log`) |
| **`/tmp`** | Temporary files, cleared on restart, writable by every user |
| **Permission** | What you are allowed to do to a file: read, write or execute |
| **Owner / group** | The user who owns a file / a set of users sharing permissions on it |
| **sudo / su** | Run a command as another user / switch to another user |

---

## Task 1 & 2: Introduction and Setting Up

This room extends part 1 in three directions:

1. **Arguments:** getting more power out of commands you already know.
2. **File management:** creating, copying, moving and deleting.
3. **Permissions:** who is allowed to do what on a file.

### Two machines, two different roles
| Machine | Think of it as | Used for |
|---------|----------------|----------|
| **AttackBox** | Your own computer | Where you type commands and run tools |
| **Lab machine** | The computer you are visiting | The remote Linux target you log in to |

This setup copies real life. In real security work you rarely sit in front of the machine. You connect to it from yours.

---

## Task 3: Accessing Linux Remotely (SSH)

### The idea in simple words
**SSH** lets you open a terminal on another computer through the network. Everything you type is **encrypted** while it travels, and only the other machine can read it. Without SSH, anyone between you and the server could read your commands and passwords.

> Note: SSH stands for **Secure Shell**. The room writes "Secure Socket Shell", but "Secure Shell" is the standard name.

### What you need to log in
1. The **IP address** of the remote machine.
2. A **username and password** of an account that exists *on that machine*.

```bash
ssh username@IP_ADDRESS
ssh tryhackme@10.10.x.x
```

Read it as: "log in **as** `tryhackme` **at** this address".

### Things to understand
- **Where your commands run:** after logging in, every command runs on the **remote** machine, not on yours. Check with `whoami` and `pwd` if you are unsure which machine you are on.
- **Invisible password:** when you type a password in the terminal, nothing appears on screen. This is normal and intentional (so nobody can see it over your shoulder, not even the number of characters). Just type it and press Enter.
- **First connection (not covered in the room):** SSH may ask `Are you sure you want to continue connecting?`. It is showing you the server's fingerprint for the first time. Type `yes`.
- **Leaving (not covered in the room):** type `exit` to close the SSH session and come back to your own machine.

### Why Linux uses SSH so much
Many Linux servers have **no desktop at all**, only a command line. SSH is the standard way to manage them.

---

## Task 4: Extending Commands with Arguments

### The idea in simple words
A command on its own does its basic job. **Arguments** (also called **flags** or **switches**) change *how* it does it.

```bash
ls        # lists files, but hides hidden ones
ls -a     # -a = all: now shows hidden files too
```

### Short vs long form
Most options come in two styles that do the same thing:

| Short | Long |
|-------|------|
| `-a` | `--all` |

Short flags are quicker to type. Long ones are easier to read in scripts.

### Hidden files
Any file or folder whose name **starts with a dot** is hidden. Hidden does not mean secret or protected, it only means `ls` doesn't show it by default. Attackers and defenders both check them, because configuration files and leftovers are often stored there.

### Useful `ls` options

| Command | What it does |
|---------|--------------|
| `ls -a` | Show hidden files too |
| `ls -l` | **Long format**: one line per file, with permissions, owner, size, date |
| `ls -lh` | Same, but sizes are **human-readable** (`4.0K`, `2.3M` instead of bytes) |
| `ls -la` | Long format **and** hidden files (flags can be combined) |

### How to learn what a command can do
You never need to memorise every flag. There are two built-in helpers:

| Helper | Use | Output |
|--------|-----|--------|
| `command --help` | Quick summary | Short list of options, printed in the terminal |
| `man command` | Full manual | Detailed page you can scroll through |

Inside a man page: arrow keys to scroll, `/word` to search, and `q` to quit. The room says Ctrl + C, and that often works too, but `q` is the normal way.

---

## Task 5: Managing Files on Linux

### The five commands

| Command | Stands for | Purpose | Example |
|---------|-----------|---------|---------|
| `touch` | touch | Create an **empty** file | `touch recipe` |
| `mkdir` | make directory | Create a folder | `mkdir mydirectory` |
| `cp` | copy | Copy a file | `cp recipe recipe2` |
| `mv` | move | Move **or rename** | `mv recipe recipe2` |
| `rm` | remove | Delete | `rm recipe` |

### How each one works

**`touch`** only creates a blank file. To put content in it, use `echo "text" > file` (from room 2) or a text editor (next room).

**`mkdir`** creates folders. You can create several at once, and with `-p` you can create folders inside folders that don't exist yet:
```bash
mkdir Documents/Homework/Assignment1      # works only if Documents/Homework already exists
mkdir -p Documents/Homework/Assignment1   # creates the whole chain
```

**`cp`** takes two things: **source** then **destination**.
```bash
cp recipe recipe2          # copy a file to a new name
cp note Documents/         # copy a file into a folder (keeps the name "note")
cp -r folder1 folder2      # copying a whole FOLDER needs -r (recursive)
```
After copying, you have **two** files. The original is still there.

**`mv`** also takes **source** then **destination**, but nothing is duplicated:
- If the destination is a **new name**, it **renames**: `mv recipe recipe2` means "recipe" no longer exists, and "recipe2" has the same content.
- If the destination is a **folder**, it **moves** the file there: `mv recipe Documents/`.

**`rm`** deletes. For folders you need `-R` (or `-r`):
```bash
rm recipe            # delete a file
rm -R mydirectory    # delete a folder and everything inside it
```

### Common confusion and warnings
- **`cp` vs `mv`:** `cp` = the file now exists twice. `mv` = the file only exists in its new place or under its new name.
- **`rm` has no recycle bin.** Deleted means gone. Be careful, especially with `-R`, because it removes everything inside the folder without asking.
- **Why `-R`?** It means *recursive*: go into the folder, delete what's inside, then delete the folder itself. Without it, `rm` refuses to delete a folder.
- **Full paths work everywhere:** instead of `cd`-ing around, you can write `cp /home/tryhackme/note /home/tryhackme/Documents`.
- **How to be sure it worked:** run `ls` (or `ls Documents`) after the command to check.

---

## Task 6: Common Directories

### The idea in simple words
The Linux file system is shaped like a **tree**:
- The trunk is `/` (called **root**).
- The branches are main folders like `/etc`, `/var`, `/home`.
- The leaves are the files and sub-folders inside them.

### The ones you must know

| Directory | What it holds | Why it matters in security |
|-----------|---------------|----------------------------|
| `/etc` | System and program configuration (short for *etcetera*). Example: `/etc/sudoers` lists who may use `sudo` | Misconfigurations and credentials are often found here |
| `/var` | Data that changes often. `/var/log` holds **log files**, plus things like databases | **Logs are where SOC analysts investigate.** This is the first place to look after an incident |
| `/root` | Home folder of the `root` user | A prime target for attackers, since root's files are the most valuable |
| `/tmp` | Temporary files. Cleared when the machine restarts. **Any user can write here** | Attackers love it, because they can drop files there even with low access |
| `/home` | Home folders of normal users (`/home/tryhackme`) | User files and personal configuration |

### The three meanings of "root" (the biggest confusion here)
| Word | Meaning |
|------|---------|
| `/` | The **top of the file system** |
| `root` (user) | The **administrator account** |
| `/root` | The **home folder** of that administrator |

The root user's home is `/root`, **not** `/home/root`. Normal users are in `/home/<name>`, but root is treated differently.

---

## Task 7: Permissions: Users and Groups

### The idea in simple words
Every file answers three questions:
1. **Who owns it?** (one owner)
2. **Which group is linked to it?** (a group of users)
3. **What is each of them allowed to do?**

### The three permissions

| Permission | Letter | On a file | On a folder |
|------------|--------|-----------|-------------|
| **Read** | `r` | Open and view it | List what's inside |
| **Write** | `w` | Change it | Create/delete files inside |
| **Execute** | `x` | Run it (script/program) | Enter it with `cd` |

### Reading `ls -l`
```
-rw-r--r-- 1 tryhackme tryhackme 0 Feb 19 10:37 file1
```
The room says to focus on three columns. These are:

| Part | In this example | Meaning |
|------|-----------------|---------|
| Permissions | `-rw-r--r--` | Who can do what |
| Owner | `tryhackme` | The user who owns the file |
| Group | `tryhackme` | The group linked to the file |

(The number `1` between them is the link count. You can ignore it for now.)

### Decoding the permissions string (not covered in the room)
```
-  rw-  r--  r--
│   │    │    └── others (everyone else): read only
│   │    └─────── group: read only
│   └──────────── owner: read + write
└──────────────── type: "-" = file, "d" = directory
```
So `-rw-r--r--` means: a normal file, the owner can read and write, the group and everybody else can only read. A `-` in a position means that permission is **not** given.

### Why users **and** groups?
It allows precise control without changing the owner. Example from the room: the school's IT staff need full control of a machine, but students should only have limited accounts, so they can't touch other students' files or the whole system. Groups let you give a *set* of people their own level of access.

### Switching users with `su`
```bash
su user2          # switch to user2 (asks for user2's password)
su -l user2       # -l = login shell, behaves like user2 really logged in
```

What you need: the **username** and that user's **password** (unless you are already root, or use `sudo`). The room's wording on this is a bit incomplete, so remember these two.

**Why `-l` matters:** a plain `su` switches the user but keeps much of your old environment (like your current folder). With `-l` you get the new user's environment, their home folder and settings, as if they logged in themselves.

### Why this matters in security
- Finding a file you **can't** read usually means you need a different user. This is the idea behind **privilege escalation**: moving from a low-privilege account to a higher one.
- Always check who you are (`whoami`) and what you can access (`ls -l`) before and after switching.
- To go back to your previous user, type `exit`.

---

## Commands Summary

| Command | What it does |
|---------|--------------|
| `ssh user@IP` | Log in to a remote machine |
| `exit` | Leave the SSH session or switched user |
| `ls -a` | List files, including hidden ones |
| `ls -l` / `ls -lh` | Detailed list (permissions, owner, size) |
| `command --help` | Short list of a command's options |
| `man command` | Full manual for a command |
| `touch file` | Create an empty file |
| `mkdir folder` | Create a folder |
| `cp source dest` | Copy a file (`-r` for folders) |
| `mv source dest` | Move or rename |
| `rm file` / `rm -R folder` | Delete a file / a folder |
| `su -l user` | Switch to another user with their full environment |