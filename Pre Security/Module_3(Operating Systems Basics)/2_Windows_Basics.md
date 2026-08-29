# 🪟 Windows Basics

## 📘 Overview

**Windows Basics** introduces the Windows operating system through a hands-on workstation scenario.

The room focuses on everyday Windows administration and security tasks, including:

* Navigating the Windows desktop
* Managing applications
* Using Windows Settings and Control Panel
* Monitoring the system with Task Manager
* Using Windows Security
* Configuring and understanding Windows Defender Firewall

The practical environment uses **Windows Server 2019**.

---

## 🎯 Learning Objectives

After completing this room, you will be able to:

* Navigate the Windows graphical interface
* Use the Desktop, Taskbar, Start Menu, and Search
* Browse and manage files using File Explorer
* Install, update, and uninstall applications
* Use Windows Settings and Control Panel
* Monitor system resources with Task Manager
* Use Windows Security to scan for threats
* Understand basic Windows Firewall profiles and rules

---

## 📌 Prerequisites

Before starting this room, it is recommended to complete:

* Inside a Computer System
* Computer Types
* Operating Systems: Introduction

---

# 🧩 Task 1: Introduction

The room places you in the role of a new employee at **TryHatMe**.

You are given a Windows workstation and need to become familiar with the environment by:

* Exploring the Windows desktop
* Using the Start Menu
* Opening built-in tools
* Navigating company folders
* Creating and managing files
* Checking system settings
* Monitoring system activity
* Reviewing Windows security features

The lab machine used in this room is **Windows Server 2019**.

---

# 🖥️ Task 2: Exploring the Windows Workspace

Windows provides a graphical environment that allows users to interact with applications, files, settings, and system resources.

## 🔐 Logging in and Authentication

Before accessing Windows, the user must authenticate.

Authentication verifies the user's identity and determines what actions they are allowed to perform.

Windows commonly uses three account types:

| Account           | Description                                               |
| ----------------- | --------------------------------------------------------- |
| **Guest**         | Restricted account with minimal permissions               |
| **Standard**      | Everyday account with limited system privileges           |
| **Administrator** | Privileged account with extensive control over the system |

In this lab, the machine automatically logs in using an **Administrator** account.

---

## 🖥️ Windows Desktop

The Windows Desktop is the main workspace presented after logging in.

Two important components are:

### Desktop

The main workspace containing:

* Files
* Folders
* Shortcuts
* Applications

### Taskbar

Provides quick access to:

* Applications
* Start Menu
* Search
* Task View
* Network settings
* Audio settings
* Date and time
* Notifications

---

## ⭐ Important Desktop Components

### Start Menu

The **Start Menu** provides access to:

* Applications
* Settings
* Files
* Folders
* User options
* Power options

You can use it to:

* Log out
* Restart
* Shut down the computer

### Search

Allows you to quickly find:

* Applications
* Files
* Folders
* Settings

### Task View

Allows you to view open windows and switch between them.

### Pinned Applications

Frequently used applications and folders can be pinned to the Taskbar.

---

# 🛠️ Built-in Windows Tools

Windows includes several applications and tools for everyday tasks.

Examples include:

* **File Explorer** → Browse and manage files
* **Notepad** → Edit text files
* **Calculator** → Perform calculations
* **Paint** → Basic image editing

These applications can usually be accessed through the Start Menu or Search.

---

# ⚙️ Getting System Information

Windows provides system information through the **Settings** application.

The **About your PC** section contains information about:

* Device
* Security
* Operating system
* Hardware specifications

In the lab, a shortcut to **About your PC** is available on the Desktop.

### 🔎 Device Information

The workstation information includes:

**Device name:**

```text
TryHatMe
```

**Installed RAM:**

```text
4.00 GB
```

**Windows Server 2019 version:**

```text
1809
```

---

# 📁 File Exploration and Management

Windows uses a **hierarchical file structure**.

Folders can contain:

* Other folders
* Files

Common locations include:

* Desktop
* Documents
* Downloads

## 📂 TryHatMe Onboarding

The lab contains a folder named:

```text
TryHatMe Onboarding
```

Its path is:

```text
C:\Users\Administrator\Desktop\TryHatMe Onboarding
```

You can open the folder directly from the Desktop or through File Explorer.

File Explorer allows you to:

* Browse directories
* Open files
* Create folders
* Move files
* Search for files
* View the current path

---

# ❓ Task 2 Answers

| Question                                        | Answer                                                        |
| ----------------------------------------------- | ------------------------------------------------------------- |
| What is the Device name?                        | `TryHatMe`                                                    |
| How much RAM is installed?                      | `4.00 GB`                                                     |
| Which Windows Server 2019 version is installed? | `1809`                                                        |
| What is the flag in `Welcome.txt`?              | **Check `Welcome.txt` inside the TryHatMe Onboarding folder** |

---

# 🔧 Task 3: Configuring and Securing Windows

Windows applications need to be properly maintained to keep the system functional and secure.

The main areas covered in this task are:

* Updating applications
* Installing applications
* Uninstalling applications
* Windows Settings
* Control Panel
* Task Manager
* Windows Security
* Windows Defender Firewall

---

## 🔄 Updating Applications

Keeping Windows and applications updated is important because updates can include:

* Security patches
* Bug fixes
* Performance improvements

### Windows Update

**Windows Update** is Microsoft's built-in update mechanism.

It can update:

* Windows
* Native applications
* Security features

Updates can be accessed through the **Settings** application.

### Application Updates

Different applications may update differently:

* Built-in applications may update automatically
* Third-party applications may have their own update system
* Some applications notify you when an update is available
* Some require manually downloading a newer installer

---

# 📦 Installing Applications

Applications can be installed through different methods.

### 1. Microsoft Store

Provides a curated way to install applications.

However, the Microsoft Store is **not available by default on Windows Server**.

### 2. Downloading From the Internet

Applications can also be downloaded from trusted vendors.

Common installer formats include:

```text
.exe
.msi
```

---

## 🧪 Hands-On Installation

Inside:

```text
Desktop → TryHatMe Onboarding
```

there is an installer called:

```text
TryHatMeWelcome
```

Double-click the installer to begin the installation.

After installation, run the application to obtain the first task's flag.

---

# 🗑️ Uninstalling Applications

Windows provides several ways to remove applications.

You can use:

* Microsoft Store
* Add or remove programs
* Control Panel
* The application's built-in uninstaller

The **Control Panel → Uninstall a program** option is a common legacy method.

---

# ⚙️ Windows Settings vs Control Panel

Windows has two major configuration interfaces.

### Windows Settings

A modern centralized interface for managing:

* System
* Devices
* Personalization
* Accounts
* Applications
* Network
* Security

### Control Panel

A legacy Windows configuration interface that still provides access to certain administrative settings.

---

# 📊 Task Manager

**Task Manager** allows you to monitor the Windows system in real time.

It can show:

* Running applications
* Background processes
* CPU usage
* Memory usage
* Logged-in users
* Services

## 📑 Task Manager Tabs

| Tab             | Purpose                                            |
| --------------- | -------------------------------------------------- |
| **Processes**   | Running applications and background processes      |
| **Performance** | CPU, memory, network and other resource statistics |
| **Users**       | Logged-in users and their resource usage           |
| **Details**     | Detailed process information and PIDs              |
| **Services**    | Windows services and their current status          |

### 💡 Important

The **Users** tab is particularly useful for checking which accounts are currently logged into the machine.

---

# 🛡️ Native Windows Security

Windows includes built-in security features designed to protect the system against:

* Malware
* Unsafe applications
* Unauthorized network access

The main security dashboard is **Windows Security**.

---

## 🔐 Windows Security

Windows Security contains four major sections:

### 🦠 Virus & Threat Protection

Detects and helps remove malicious software.

It supports:

* Real-time protection
* Custom scans
* Other scanning options

### 🌐 Firewall & Network Protection

Controls network traffic and helps prevent unauthorized access.

### 🌍 App & Browser Control

Helps protect against potentially unsafe:

* Applications
* Files
* Websites

### 🔒 Device Security

Provides hardware-based security protections.

---

# 🔍 Running a Custom Scan

To scan the onboarding folder:

1. Open **Windows Security**
2. Select **Virus & Threat Protection**
3. Select **Scan options**
4. Choose **Custom scan**
5. Click **Scan now**
6. Select:

```text
TryHatMe Onboarding
```

The scan will detect a safe test file used by the lab.

The detected file is:

```text
Virus:DOS/EICAR_Test_File
```

Select the detection and choose **See details** to inspect the affected item.

---

# 🔥 Windows Defender Firewall

**Windows Defender Firewall** protects the computer against unauthorized network traffic.

It monitors network connections and applies rules that determine whether traffic should be:

* Allowed
* Denied

## 🌐 Network Profiles

Windows Firewall uses different network profiles.

| Profile     | Purpose                                                |
| ----------- | ------------------------------------------------------ |
| **Domain**  | Used when connected to an organization's domain        |
| **Private** | Used for trusted networks such as home or lab networks |
| **Public**  | Used for untrusted networks such as public Wi-Fi       |

---

## ⚙️ Advanced Firewall Settings

Advanced settings allow you to:

* View inbound rules
* View outbound rules
* View connection rules
* Inspect individual firewall rules
* Create new rules
* Filter existing rules

A rule can contain information such as:

* Rule name
* Group
* Network profile
* Status
* Action

---

# ❓ Task 3 Answers

| Question                                            | Answer                                                |
| --------------------------------------------------- | ----------------------------------------------------- |
| Flag after installing and running `TryHatMeWelcome` | **Run the application in the lab to obtain the flag** |
| Country/region configured in Windows                | **Check Settings → Time & Language**                  |
| Account currently logged in                         | **Check Task Manager → Users**                        |
| File shown under Affected items                     | **Check Virus:DOS/EICAR_Test_File → See details**     |

---

# 🧠 Task 4: Conclusion

Windows provides a complete graphical environment for managing applications, files, users, hardware, and security.

During this room, you learned how to:

* Navigate the Windows Desktop
* Use the Start Menu and Taskbar
* Search for applications and files
* Browse folders with File Explorer
* Check system specifications
* Install and uninstall applications
* Configure Windows through Settings and Control Panel
* Monitor system activity using Task Manager
* Scan files using Windows Security
* Understand Windows Defender Firewall

---

# 🔑 Key Terminology

* **Desktop** → Main Windows workspace
* **Taskbar** → Provides access to applications, tools, and notifications
* **Start Menu** → Access point for applications, settings, and power options
* **Search** → Quickly finds applications, files, folders, and settings
* **File Explorer** → Tool for browsing and managing files
* **Windows Update** → Keeps Windows and supported components updated
* **Windows Settings** → Modern interface for configuring Windows
* **Control Panel** → Legacy system configuration interface
* **Task Manager** → Monitors processes, users, and system resources
* **Windows Security** → Central dashboard for Windows security features
* **Windows Defender Firewall** → Controls network traffic and helps block unauthorized connections

---

# 🚀 What’s Next?

After learning the basics of Windows through the GUI, the next step is to move into the **Command-Line Interface (CLI)**.

The upcoming rooms focus on:

➡️ **Linux CLI Basics**

➡️ **Windows CLI Basics**

These rooms will introduce interacting with operating systems through commands rather than relying only on graphical interfaces.
