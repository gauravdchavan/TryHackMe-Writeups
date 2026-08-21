Windows Fundamentals Part 1 — Documentation
1. Introduction to Windows
What is Windows?
Windows is an operating system developed by Microsoft.
It provides a graphical user interface (GUI) for interacting with the computer.
It manages hardware, software, files, users, processes, and system resources.
Important Windows concepts
Operating System (OS)
GUI
Users and Groups
Files and Directories
Processes
Services
System Settings
Security and Permissions
2. Windows Editions

Know the major Windows editions and their general purpose:

Windows Home
Windows Pro
Windows Enterprise
Windows Education

Important: Different editions provide different features, especially regarding administration, security, and enterprise management.

3. The Windows Desktop

Document the main components:

Desktop
Start Menu
Taskbar
Search
Notification Area/System Tray
Recycle Bin
Desktop shortcuts
Important keyboard shortcuts
Shortcut	Function
Win	Open Start Menu
Win + D	Show/Hide Desktop
Win + E	Open File Explorer
Win + R	Open Run
Win + I	Open Settings
Win + L	Lock computer
Alt + Tab	Switch between applications
Ctrl + Shift + Esc	Open Task Manager
Alt + F4	Close active window

⭐ Especially remember: Ctrl + Shift + Esc → Task Manager.

4. Start Menu

Understand:

Applications
Search
Settings
Power options
User account options
Power options
Shut down
Restart
Sleep
5. Taskbar

Important components:

Start button
Search
Pinned applications
Running applications
Notification Area
Clock
Network
Volume
Notification Area

The notification area can contain icons such as:

Network
Volume
Battery
Security notifications
Background applications
6. File Explorer

File Explorer is used to manage files and folders.

Important locations
C:\
C:\Windows
C:\Users
C:\Program Files
C:\Program Files (x86)
Important folders

C:\Users

Contains profiles for users on the computer.

Example:

C:\Users\Sunny

C:\Windows

Contains important Windows operating-system files.

C:\Program Files

Normally contains installed 64-bit applications.

C:\Program Files (x86)

Normally contains 32-bit applications on 64-bit Windows.

7. File and Folder Permissions

Windows uses permissions to control who can access files and folders.

Important permissions include:

Read
Write
Modify
Full Control
Why permissions matter in cybersecurity

Incorrect permissions can allow unauthorized users or malicious programs to:

Read sensitive files
Modify files
Execute programs
Delete important data
8. User Accounts

Windows has different types of users.

Standard User

A standard user has limited privileges and normally cannot make major system changes.

Administrator

An administrator has higher privileges and can perform administrative operations.

Important concept

Least Privilege

Users should have only the permissions required to perform their tasks.

This is an extremely important cybersecurity principle.

9. User Account Control (UAC)
What is UAC?

UAC = User Account Control

UAC is a Windows security feature designed to prevent unauthorized changes to the system.

When an operation requires elevated privileges, Windows can ask the user for confirmation.

Why UAC is important

Suppose malware is running under your user account.

Without proper privilege separation:

User
 ↓
Malware
 ↓
Administrative changes

With UAC:

User
 ↓
Program requests elevation
 ↓
UAC prompt
 ↓
User confirmation
 ↓
Elevated operation
Important point

UAC does not normally apply to the built-in local Administrator account by default.

⭐ Remember this for TryHackMe questions.

10. Task Manager
What is Task Manager?

Task Manager allows you to monitor and manage running processes and system resources.

How to open it
Ctrl + Shift + Esc
Important tabs
Processes
Performance
App history
Startup apps
Users
Details
Services
Processes

Shows applications and background processes currently running.

Performance

Shows resource usage such as:

CPU
Memory
Disk
Network
GPU
Startup Apps

Shows applications that start automatically when Windows starts.

Services

Shows Windows services running on the system.

11. System Information

Windows provides information about the computer's hardware and operating system.

Useful information includes:

Operating System
Processor
RAM
System type
Windows version
Computer name

You can use:

Win + R

and run:

msinfo32

This opens System Information.

12. Resource Monitor

Resource Monitor provides more detailed information about system resources.

You can monitor:

CPU
Memory
Disk
Network

It can be useful when investigating:

High CPU usage
High memory usage
Disk activity
Network connections
13. Control Panel

Control Panel is a traditional Windows interface for managing system settings.

Examples:

User Accounts
Programs
Network settings
System settings
Windows Firewall
Hardware settings

Modern Windows also provides the Settings application.

14. Computer Management

Computer Management provides several administrative tools in one place.

Important components include:

System Tools
Event Viewer
Shared Folders
Local Users and Groups
Performance
Device Manager
Disk Management
Services

⭐ This becomes especially useful later when learning Windows administration and cybersecurity.

15. Run Dialog

Open with:

Win + R

Useful commands:

Command	Opens
cmd	Command Prompt
powershell	PowerShell
msinfo32	System Information
taskmgr	Task Manager
control	Control Panel
services.msc	Services
compmgmt.msc	Computer Management
devmgmt.msc	Device Manager
eventvwr.msc	Event Viewer

⭐ These are worth documenting because you'll use many of them later in cybersecurity.

16. Important Cybersecurity Concepts

Make a separate section for these.

Least Privilege

Give users/programs only the permissions they need.

Privilege Escalation

When a user or program gains higher privileges than originally authorized.

Example:

Standard User
      ↓
Administrator
User Account Control

Helps control administrative elevation.

File Permissions

Control who can access or modify files.

User Accounts

Determine what actions a person can perform.

17. Important TryHackMe Questions & Answers

Keep a separate section at the end:

Question:
What is the keyboard shortcut to open Task Manager?


Answer:
Ctrl + Shift + Esc

Do this for every question you actually solved, rather than filling the document with answers copied from elsewhere.

18. What I Learned

At the end, write a short summary covering:

Windows desktop components
File Explorer and important directories
User accounts
Administrator vs Standard User
UAC
Task Manager
System Information
Resource Monitor
Control Panel
Computer Management
Windows administrative tools
Basic Windows security concepts
