# TryHackMe — Linux Fundamentals

## Task 1 — Introduction

Linux is an open-source operating system widely used in servers, cybersecurity, cloud computing, networking, and penetration testing.

In cybersecurity, Linux is important because many security tools and servers run on Linux. Kali Linux is also a Linux distribution commonly used for penetration testing and security testing.

### Important concepts

* **Linux** — Operating system/kernel family used on many computers and servers.
* **Terminal** — Interface used to interact with Linux using commands.
* **Command** — An instruction given to the operating system.
* **Filesystem** — The way files and directories are organized.
* **Root (`/`)** — The top-level directory of the Linux filesystem.
* **Root user** — The administrator/superuser with extensive privileges.

---

# Task 2 — Accessing Your Linux Machine Using SSH

## What is SSH?

**SSH (Secure Shell)** is a protocol used to securely connect to and control a remote computer through a command-line interface.

The basic syntax is:

```bash
ssh username@IP_ADDRESS
```

Example:

```bash
ssh tryhackme@10.10.10.5
```

Here:

* `ssh` → SSH command
* `tryhackme` → username
* `10.10.10.5` → IP address of the remote machine

After executing the command, the system may ask for the user's password.

### Why SSH is important

SSH allows administrators and security professionals to:

* Access remote Linux machines
* Execute commands remotely
* Manage servers
* Perform security testing
* Troubleshoot systems

### Important SSH port

SSH normally uses:

```text
Port 22
```

---

# Task 3 — Introduction to Flags and Switches

Linux commands can accept **flags/switches** to change their behavior or provide additional information.

For example:

```bash
ls
```

lists files and directories.

Using:

```bash
ls -l
```

provides a detailed/long listing.

Using:

```bash
ls -a
```

also displays hidden files.

Using both:

```bash
ls -la
```

displays hidden files in a detailed format.

### Common examples

| Command       | Purpose                                 |
| ------------- | --------------------------------------- |
| `ls`          | List files/directories                  |
| `ls -l`       | Detailed listing                        |
| `ls -a`       | Show hidden files                       |
| `ls -la`      | Detailed listing including hidden files |
| `man command` | Display the manual for a command        |

### Man pages

The `man` command is used to read documentation about Linux commands.

Example:

```bash
man ls
```

or:

```bash
man su
```

This is useful when you want to understand available options and switches.

---

# Task 4 — Filesystem Interaction Continued

Linux uses a hierarchical filesystem.

The top-level directory is:

```text
/
```

Directories can contain files and other directories.

## `pwd`

`pwd` shows the current working directory.

```bash
pwd
```

Example output:

```text
/home/gaurav
```

This tells us where we currently are.

---

## `ls`

`ls` lists the contents of the current directory.

```bash
ls
```

Detailed listing:

```bash
ls -l
```

Show hidden files:

```bash
ls -a
```

Detailed listing + hidden files:

```bash
ls -la
```

---

## `cd`

`cd` is used to change directories.

Example:

```bash
cd /home
```

Go back to the previous directory:

```bash
cd ..
```

Go to the user's home directory:

```bash
cd ~
```

or simply:

```bash
cd
```

### Important symbols

```text
/   → Root directory
..  → Parent directory
.   → Current directory
~   → Current user's home directory
```

---

## `mkdir`

Creates a new directory.

```bash
mkdir myfolder
```

---

## `touch`

Creates an empty file.

```bash
touch note.txt
```

---

## `cp`

Copies a file or directory.

Example:

```bash
cp note.txt /home/gaurav/
```

---

## `mv`

Moves or renames a file.

Move:

```bash
mv note.txt /home/gaurav/
```

Rename:

```bash
mv old.txt new.txt
```

---

## `rm`

Removes a file.

```bash
rm note.txt
```

Remove a directory and its contents:

```bash
rm -r myfolder
```

Be careful with `rm` because deleted files may not be recoverable through normal means.

---

## `cat`

Displays the contents of a file.

```bash
cat note.txt
```

Example:

```text
Hello Gaurav
```

---

## `file`

The `file` command identifies the type of a file.

```bash
file note.txt
```

It can help determine whether something is a text file, executable, image, script, etc.

---

# Task 5 — Permissions 101

Linux controls access to files and directories using **permissions**.

There are three main permissions:

| Symbol | Permission | Numeric value |
| ------ | ---------- | ------------: |
| `r`    | Read       |             4 |
| `w`    | Write      |             2 |
| `x`    | Execute    |             1 |

There are also three permission categories:

```text
Owner | Group | Others
```

## Checking permissions

Use:

```bash
ls -l filename
```

Example:

```text
-rwxr-xr--
```

The permission portion can be divided into:

```text
rwx | r-x | r--
 ↓     ↓     ↓
Owner Group Others
```

### Owner

```text
rwx
```

The owner can:

* Read
* Write
* Execute

### Group

```text
r-x
```

The group can:

* Read
* Execute
* Cannot write

### Others

```text
r--
```

Others can:

* Read
* Cannot write
* Cannot execute

---

## Converting permissions to numbers

Remember:

```text
r = 4
w = 2
x = 1
```

Add the values.

### `rwx`

```text
4 + 2 + 1 = 7
```

Therefore:

```text
rwx = 7
```

### `r-x`

```text
4 + 0 + 1 = 5
```

Therefore:

```text
r-x = 5
```

### `r--`

```text
4 + 0 + 0 = 4
```

Therefore:

```text
r-- = 4
```

---

## Example: `755`

```text
rwxr-xr-x
```

Separate it:

```text
rwx | r-x | r-x
 7  |  5  |  5
```

Therefore:

```text
755
```

Meaning:

```text
Owner  → Read + Write + Execute
Group  → Read + Execute
Others → Read + Execute
```

---

## Example: `644`

```text
rw-r--r--
```

Separate it:

```text
rw- | r-- | r--
 6  |  4  |  4
```

Therefore:

```text
644
```

Meaning:

```text
Owner  → Read + Write
Group  → Read only
Others → Read only
```

---

## Example: `700`

```text
rwx------
```

Separate it:

```text
rwx | --- | ---
 7  |  0  |  0
```

Therefore:

```text
700
```

Meaning:

```text
Owner  → Read + Write + Execute
Group  → No permission
Others → No permission
```

---

# Users and Groups

Linux permissions are assigned based on:

```text
User/Owner
Group
Others
```

### User

A user is an individual account.

Example:

```text
gaurav
john
student
```

### Group

A group is a collection of users.

For example:

```text
CyberSecurity
├── Gaurav
├── Rahul
└── Amit
```

A file can belong to one owner and one group, with separate permissions for each.

This allows Linux to provide granular access control.

---

# Switching Between Users

Linux provides the `su` command to switch users.

Basic syntax:

```bash
su username
```

Example:

```bash
su john
```

You normally need the target user's password when switching this way without root privileges.

## Login switch

```bash
su -l username
```

or:

```bash
su --login username
```

The `-l` option starts a login shell and loads more of the target user's login environment.

Remember:

```text
su          → Switch User
su john     → Switch to john
su -l john  → Switch to john with a login environment
```

---

# Task 6 — Common Directories

Linux has a standard filesystem hierarchy. Some directories are especially important for cybersecurity.

## `/`

The root directory and the top of the entire Linux filesystem.

```text
/
├── home
├── root
├── etc
├── var
├── tmp
└── usr
```

---

## `/home`

Contains the home directories of normal users.

Example:

```text
/home/gaurav
/home/student
```

Users commonly store their personal files here.

---

## `/root`

The home directory of the **root user**.

Important distinction:

```text
/      → Root of the filesystem
/root  → Root user's home directory
```

---

## `/etc`

Contains system and application **configuration files**.

Examples:

```text
/etc/passwd
/etc/shadow
/etc/hosts
/etc/ssh/
```

For cybersecurity, `/etc` is very important during enumeration.

---

## `/var`

Contains data that changes frequently.

One particularly important directory is:

```text
/var/log
```

This contains system/application logs.

Logs can help security professionals investigate system activity and authentication events.

---

## `/tmp`

Contains temporary files.

```text
/tmp
```

Applications commonly use this directory for temporary data.

From a security perspective, unusual files or scripts in `/tmp` can be worth investigating.

---

## `/usr`

Contains many programs, libraries, documentation, and other resources.

Common locations include:

```text
/usr/bin
/usr/sbin
/usr/lib
/usr/share
```

---

## `/bin`

Traditionally contains essential executable commands.

Examples include commands such as:

```text
ls
cp
mv
cat
```

Modern Linux distributions may merge `/bin` with `/usr/bin`.

---

## `/sbin`

Traditionally contains system administration commands.

Modern distributions may merge `/sbin` with `/usr/sbin`.

---

## `/opt`

Commonly used for optional or third-party software.

Example:

```text
/opt/application/
```

---

## `/dev`

Contains device files.

Examples:

```text
/dev/sda
/dev/null
/dev/tty
```

Linux represents many hardware and virtual devices through files in `/dev`.

---

## `/proc`

A special virtual filesystem containing information about:

* Running processes
* CPU
* Memory
* Kernel
* System information

Examples:

```text
/proc/cpuinfo
/proc/meminfo
```

Process IDs can also appear as directories:

```text
/proc/1234
```

---

## `/boot`

Contains files required for the Linux boot process, including kernel and boot-related files.

```text
/boot
```

---

## `/lib`

Contains important system libraries used by programs.

Modern systems may also use:

```text
/usr/lib
```

---

## `/mnt`

Commonly used as a temporary mount point for filesystems.

Example:

```text
/mnt/mydisk
```

---

## `/media`

Commonly used for mounted removable media such as USB drives.

Example:

```text
/media/gaurav/USB
```

---

# 🔥 Important Commands Learned

```bash
ssh username@IP
ls
ls -l
ls -a
ls -la
pwd
cd
cd ..
cd ~
mkdir
touch
cp
mv
rm
cat
file
man
su
su -l username
```

# 🧠 Key Things to Remember

### Filesystem

```text
/      → Root of filesystem
/home  → Normal users
/root  → Root user's home
/etc   → Configuration
/var   → Changing data
/tmp   → Temporary files
/usr   → Programs/supporting files
/dev   → Devices
/proc  → Processes/system information
/boot  → Boot files
```

### Permissions

```text
r = 4 = Read
w = 2 = Write
x = 1 = Execute
```

### Permission groups

```text
Owner | Group | Others
```

### Common numeric permissions

```text
755 → rwxr-xr-x
644 → rw-r--r--
700 → rwx------
```

### Most important commands

```bash
ls -l filename
```

→ Check file permissions.

```bash
pwd
```

→ Show current directory.

```bash
cd directory
```

→ Change directory.

```bash
cat filename
```

→ Read file contents.

```bash
file filename
```

→ Identify file type.

```bash
su username
```

→ Switch user.

```bash
man command
```

→ Read command documentation.

---

# 🎯 What I Learned From This Room

* Linux uses a hierarchical filesystem.
* SSH can be used to access a remote Linux machine.
* Flags and switches modify the behavior of commands.
* `ls -l` can be used to inspect file permissions.
* Linux permissions use Read, Write, and Execute.
* Permissions are assigned to the Owner, Group, and Others.
* Symbolic permissions can be converted into numeric permissions.
* Linux uses users and groups to control access.
* `su` can be used to switch between users.
* Important Linux directories such as `/etc`, `/home`, `/root`, `/var`, `/tmp`, and `/proc` are useful during cybersecurity enumeration.

