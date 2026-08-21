# 🪟 TryHackMe — Windows Fundamentals Part 1

> **Platform:** TryHackMe
> **Room:** Windows Fundamentals Part 1
> **Category:** Windows Fundamentals
> **Difficulty:** Easy
> **Status:** ✅ Completed

---

## 📌 1. Room Overview

This room introduces the fundamentals of the Windows operating system.

It covers the Windows desktop environment, user accounts, file systems, permissions, User Account Control (UAC), Task Manager, and other basic Windows features.

Understanding these fundamentals is important for cybersecurity because Windows is widely used in organizations and is frequently targeted by attackers.

---

## 🎯 2. Learning Objectives

By completing this room, I learned:

* Basic Windows desktop components
* Windows editions
* Start Menu and Taskbar
* File Explorer
* File and folder permissions
* User accounts
* Administrator and Standard User accounts
* User Account Control (UAC)
* Task Manager
* System Information
* Resource Monitor
* Control Panel
* Computer Management
* Useful Windows Run commands
* Important Windows keyboard shortcuts

---

# 🖥️ 3. Windows Desktop

The Windows desktop is the main graphical interface displayed after logging into Windows.

### Important components

```text
Desktop
├── Start Menu
├── Taskbar
├── Search
├── Notification Area
├── System Tray
├── Recycle Bin
└── Desktop Shortcuts
```

---

# 📂 4. File Explorer

**File Explorer** is used to navigate and manage files and folders in Windows.

### Shortcut

```text
Win + E
```

### Important Windows directories

| Directory                | Description                           |
| ------------------------ | ------------------------------------- |
| `C:\`                    | Root directory                        |
| `C:\Windows`             | Windows operating system files        |
| `C:\Users`               | User profiles                         |
| `C:\Program Files`       | Installed applications                |
| `C:\Program Files (x86)` | 32-bit applications on 64-bit Windows |

### Example

```text
C:\Users\Username
```

This directory contains files and folders belonging to a particular user.

---

# 👤 5. Windows User Accounts

Windows supports different types of user accounts.

### Standard User

A Standard User has limited privileges and cannot normally perform operations requiring administrative privileges.

### Administrator

An Administrator has higher privileges and can perform administrative operations such as:

* Installing software
* Changing system settings
* Managing users
* Modifying protected system files

### 🔐 Security Principle

The **Principle of Least Privilege** states that users and programs should receive only the permissions they need.

```text
More Privileges
      ↓
More System Control
      ↓
Greater Security Risk if Compromised
```

---

# 🛡️ 6. User Account Control (UAC)

**UAC = User Account Control**

UAC is a Windows security feature designed to prevent unauthorized changes to the operating system.

When an operation requires elevated privileges, Windows can ask the user to confirm the operation.

### Example

```text
User
  ↓
Program requests administrator privileges
  ↓
UAC Prompt
  ↓
User confirms
  ↓
Elevated privileges granted
```

### Why UAC is important

UAC helps reduce the impact of malware because programs do not automatically receive elevated privileges.

> ⚠️ **Important:** UAC does not apply by default to the built-in local Administrator account.

---

# 📊 7. Task Manager

Task Manager allows users to monitor and manage running applications, processes, services, and system resources.

### Keyboard shortcut

```text
Ctrl + Shift + Esc
```

### Important Task Manager tabs

| Tab          | Purpose                                     |
| ------------ | ------------------------------------------- |
| Processes    | Shows running applications and processes    |
| Performance  | Shows CPU, RAM, Disk, Network and GPU usage |
| App History  | Shows application resource usage            |
| Startup Apps | Shows programs that start with Windows      |
| Users        | Shows logged-in users                       |
| Details      | Provides detailed process information       |
| Services     | Shows Windows services                      |

### Cybersecurity relevance

Task Manager can help identify:

* Suspicious processes
* High CPU usage
* High memory usage
* Unwanted startup applications
* Running services

---

# ⚙️ 8. System Information

Windows provides **System Information** to display detailed information about the computer.

### Open using Run

```text
Win + R
```

Then:

```text
msinfo32
```

### Information available

* Operating System
* Processor
* RAM
* System type
* Hardware information
* Windows version

---

# 📈 9. Resource Monitor

Resource Monitor provides detailed information about system resource usage.

It allows you to monitor:

```text
CPU
Memory
Disk
Network
```

It can be useful for troubleshooting performance problems and investigating unusual resource usage.

---

# ⚙️ 10. Control Panel

**Control Panel** provides access to many Windows configuration options.

Examples include:

* User Accounts
* Programs
* Network settings
* System settings
* Windows Firewall
* Hardware configuration

Modern versions of Windows also provide the **Settings** application.

---

# 🖥️ 11. Computer Management

Computer Management is an administrative console containing several Windows management tools.

Important components include:

```text
System Tools
├── Event Viewer
├── Shared Folders
├── Local Users and Groups
├── Performance
└── Device Manager

Storage
└── Disk Management

Services and Applications
└── Services
```

### Open Computer Management

```text
Win + R
```

Then:

```text
compmgmt.msc
```

---

# ⌨️ 12. Important Windows Keyboard Shortcuts

| Shortcut             | Function            |
| -------------------- | ------------------- |
| `Win`                | Open Start Menu     |
| `Win + D`            | Show/Hide Desktop   |
| `Win + E`            | File Explorer       |
| `Win + R`            | Run Dialog          |
| `Win + I`            | Settings            |
| `Win + L`            | Lock Windows        |
| `Alt + Tab`          | Switch applications |
| `Alt + F4`           | Close active window |
| `Ctrl + Shift + Esc` | Task Manager        |

### ⭐ Most Important

```text
Ctrl + Shift + Esc
        ↓
   Task Manager
```

---

# 🏃 13. Important Windows Run Commands

The **Run dialog** can be opened using:

```text
Win + R
```

### Useful commands

| Command        | Opens               |
| -------------- | ------------------- |
| `cmd`          | Command Prompt      |
| `powershell`   | PowerShell          |
| `taskmgr`      | Task Manager        |
| `msinfo32`     | System Information  |
| `control`      | Control Panel       |
| `compmgmt.msc` | Computer Management |
| `devmgmt.msc`  | Device Manager      |
| `eventvwr.msc` | Event Viewer        |
| `services.msc` | Services            |

---

# 🔐 14. Important Cybersecurity Concepts

### Least Privilege

Users and programs should have only the permissions required to perform their tasks.

### Privilege Escalation

Privilege escalation occurs when a user or program obtains higher privileges than originally authorized.

Example:

```text
Standard User
      ↓
Privilege Escalation
      ↓
Administrator
```

### UAC

UAC helps control when applications need elevated privileges.

### File Permissions

Permissions determine who can read, modify, or control files and folders.

### Processes

Running processes can be monitored to identify potentially suspicious activity.

### Services

Windows services run background operations and can be important during security investigations.

---

# 📝 15. TryHackMe Questions & Answers

## Question 1

**What is the keyboard shortcut to open Task Manager?**

### Answer

```text
Ctrl + Shift + Esc
```

---

## Question 2

**What does UAC stand for?**

### Answer

```text
User Account Control
```

---

## Question 3

**Does UAC apply by default to the built-in local Administrator account?**

### Answer

```text
No
```

---

# 💡 16. Key Takeaways

```text
Windows Fundamentals
        │
        ├── Desktop
        ├── File Explorer
        ├── Users & Groups
        ├── Permissions
        ├── UAC
        ├── Task Manager
        ├── System Information
        ├── Resource Monitor
        ├── Control Panel
        ├── Computer Management
        └── Run Commands
```

### What I learned

* How the Windows desktop is organized
* How to navigate files and folders
* Difference between Standard User and Administrator
* Importance of least privilege
* How UAC protects Windows
* How to use Task Manager
* How to view system information
* How to monitor system resources
* How to access Windows administrative tools
* Useful Windows keyboard shortcuts and Run commands

---

# 🔐 17. Cybersecurity Relevance

Windows Fundamentals provides the foundation required for further cybersecurity learning.

These concepts will be useful when learning:

```text
Windows Fundamentals
        ↓
Windows Administration
        ↓
Active Directory
        ↓
Windows Security
        ↓
SOC / Threat Detection
        ↓
Windows Privilege Escalation
        ↓
Penetration Testing
```

Understanding users, permissions, processes, services, and administrative privileges is especially important for cybersecurity professionals.

---

# 📚 18. Conclusion

Windows Fundamentals Part 1 provided an introduction to the Windows operating system and its basic security and administration features.

The most important concepts I learned were **user accounts, permissions, least privilege, UAC, Task Manager, system information, and Windows administrative tools**.

These fundamentals will serve as a foundation for more advanced Windows security and penetration-testing topics.

---

## ✅ Room Status

```text
Windows Fundamentals Part 1
        ↓
       ✅
    COMPLETED
```
