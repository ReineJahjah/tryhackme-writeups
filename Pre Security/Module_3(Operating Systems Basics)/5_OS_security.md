# Room: Operating System Security

**Path:** Operating Systems Basics

**Date:** August 2026

**Difficulty:** Easy

---

## Objective

Understand how operating systems protect personal data, system resources, applications, and user accounts. The room covers the **CIA triad**, common OS security weaknesses such as weak passwords and poor file permissions, the risks posed by malware, and a hands-on Linux exercise involving authentication and privilege escalation.

---

## Key Concepts

* **Operating System (OS):** The software layer between hardware, applications, and users that manages system resources and allows applications to communicate with hardware safely.
* **CIA Triad:** The core security model of Confidentiality, Integrity, and Availability.
* **Authentication:** The process of verifying a user's identity.
* **Principle of Least Privilege:** Users should only have access to the files and resources they truly need.
* **Malware:** Malicious software that can target confidentiality, integrity, or availability.
* **Root Account:** The highest-privilege account on a Linux system.

---

# Task 1: Introduction to Operating System Security

## What Is an Operating System?

An OS is the software layer between hardware, applications, and users. It manages system resources and allows applications to communicate with hardware safely. Without an OS, hardware alone cannot run applications.

### Hardware Examples

CPU, RAM, keyboard, monitor, storage devices.

### Common Operating Systems

* **Desktop & laptop:** Windows, macOS, Linux
* **Mobile:** Android, iOS
* **Server:** Windows Server, IBM AIX, Oracle Solaris, Linux

## Why OS Security Matters

Operating systems store sensitive information such as emails, passwords, photos, banking apps, and confidential documents.

## The CIA Triad

1. **Confidentiality** — Only authorized users should access data.
2. **Integrity** — Data should not be modified without permission.
3. **Availability** — Systems and data should remain accessible when needed.

## Answer

**Q) Which is NOT an operating system?**
A) Thunderbird

---

# Task 2: Common Examples of OS Security

## Authentication & Weak Passwords

Authentication verifies identity using:

* Something you know → password/PIN
* Something you are → fingerprint
* Something you have → phone/device

### Weak Password Examples

Common weak passwords include `123456`, `password`, `qwerty`, and `iloveyou`. Attackers commonly guess these first.

### Strong Password Practices

A strong password should be unique, include uppercase/lowercase letters, include numbers/symbols, and avoid dictionary words.

## Weak File Permissions

### Principle of Least Privilege

Users should only access files they truly need. Weak permissions can lead to unauthorized file access, file tampering, and data leaks.

## Malicious Programs

Malware can target confidentiality, integrity, or availability.

### Ransomware

Ransomware encrypts files, makes data inaccessible, and demands payment for decryption.

## Answer

**Q) Which password is strongest?**
A) LearnM00r

---

# Task 3: Practical Example of OS Security

## Attack Scenario

Goal: gain access to a Linux machine, discover weak passwords, and escalate privileges to root.

## Linux Concepts

**Important accounts:**

* `root` → full administrative access
* Regular users → limited permissions

## Commands Used

| Command | Purpose |
|---|---|
| `whoami` | Display current user |
| `ssh` | Connect to remote machine |
| `ls` | List files |
| `cat` | Display file contents |
| `history` | View previous commands |

## SSH Login

```text
ssh sammie@MACHINE_IP
```

Password discovered: `dragon`

## Verify Current User

```text
whoami
```

Output: `sammie`

## List Files

```text
ls
```

## Read File Contents

```text
cat draft.md
```

## Command History

```text
history
```

Used to discover sensitive information accidentally typed by users.

## Privilege Escalation

Switch to root:

```text
su - root
```

## Answers

**Q) Johnny's password?**
A) `abc123`

**Q) Root password discovered in history?**
A) `happyHack!NG`

**Q) Flag inside root directory?**
A) `THM{YouGotRoot}`

---

# Task 4: Conclusion

Operating system security is essential for protecting devices, accounts, applications, and sensitive data.

---

# Key Terminology

* **Operating System (OS):** Software managing hardware and applications.
* **Confidentiality:** Prevent unauthorized access.
* **Integrity:** Prevent unauthorized modification.
* **Availability:** Ensure systems remain accessible.
* **Authentication:** Verifying user identity.
* **Least Privilege:** Minimal required access only.
* **Malware:** Malicious software targeting systems.
* **Ransomware:** Malware encrypting files for ransom.
* **Root Account:** Highest privilege Linux account.
* **Administrator:** Highest privilege Windows account.

---

# Key Takeaways

* Operating systems protect **confidentiality, integrity, and availability** of systems and data (the CIA triad).
* Weak passwords are one of the easiest ways for attackers to compromise accounts — strength and uniqueness matter.
* The **principle of least privilege** limits the damage that weak file permissions or a compromised account can cause.
* Malware, especially ransomware, can directly threaten all three pillars of the CIA triad.
* On Linux, discovering credentials (e.g. through `history`) and escalating to `root` via `su` demonstrates how small oversights — like leftover command history — can lead to full system compromise.

---

## What I Learned

This room connected the theory of operating system security to a hands-on Linux exercise, which made the concepts much more concrete. I learned the CIA triad — confidentiality, integrity, and availability — as the foundation for thinking about *why* certain security practices matter, rather than just memorizing rules.

The section on weak passwords and least privilege reinforced how much everyday security risk comes down to simple, avoidable mistakes: reusing weak passwords like `123456`, or giving accounts more access than they need. Seeing how ransomware fits into the CIA triad (attacking availability and integrity at once) helped tie the abstract model to a real-world threat.

The practical task was the most valuable part. I practiced logging in over `ssh` with a discovered password, confirming my identity with `whoami`, and using `history` to find leftover credentials a user had typed — which is a great reminder of how command history can unintentionally leak sensitive information. Escalating from a regular user to `root` with `su - root` made the difference between limited and full system privileges very tangible, and showed why protecting the root account is so critical on Linux systems.