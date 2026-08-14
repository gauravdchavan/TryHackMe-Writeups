
# TryHackMe — Linux Fundamentals Part 1

## 1. Room Overview

* **Platform:** TryHackMe
* **Room:** Linux Fundamentals Part 1
* **Topic:** Linux fundamentals and command-line basics
* **Difficulty:** Easy
* **Status:** Completed
* **Purpose:** Learn the basic Linux environment, filesystem, terminal, and essential commands.

---

## 2. Learning Objectives

By completing this room, I learned:

* What Linux is
* What the Linux terminal is
* How the Linux filesystem is organized
* How to navigate between directories
* How to create, copy, move, and delete files/directories
* How to search for files
* How to search for text inside files
* How to read command documentation
* How to work with paths
* Basic Linux terminology and commands

---

## 3. What is Linux?

Linux is an open-source operating-system family built around the Linux kernel.

The Linux kernel is the core component that manages hardware and provides essential services to software.

Linux is widely used in:

* Servers
* Cloud computing
* Networking
* Software development
* Embedded systems
* Cybersecurity
* Penetration testing

Examples of Linux distributions include:

* Ubuntu
* Debian
* Kali Linux
* Fedora
* Arch Linux

### Important distinction

Linux itself is technically the **kernel**. A Linux distribution combines the Linux kernel with other software and tools to provide a complete operating system.

---

## 4. Linux Terminal

The terminal is a command-line interface used to interact with the operating system by entering commands.

Instead of using a graphical interface to perform a task, we can use commands such as:

```bash
pwd
ls
cd
mkdir
cat
```

The terminal is very important in cybersecurity because many security tools and administrative tasks are performed from the command line.

---

## 5. Linux Filesystem

Linux organizes files and directories in a hierarchical structure.

The top of the filesystem is called the **root directory**, represented by:

```text
/
```

Example:

```text
/
├── home/
├── etc/
├── var/
├── usr/
├── tmp/
└── ...
```

### Root directory vs root user

Do not confuse:

```text
/       → root directory
root    → root user/account
```

The root directory is the top-level directory of the filesystem.

The root user is a privileged user account.

---

## 6. Important Path Symbols

### `.` — Current Directory

A single dot represents the current directory.

Example:

```bash
cd .
```

This keeps you in the current directory.

---

### `..` — Parent Directory

Two dots represent the parent directory.

Example:

```bash
cd ..
```

If I am currently in:

```text
/home/tryhackme/Documents
```

`cd ..` moves me to:

```text
/home/tryhackme
```

---

### `~` — Home Directory

The tilde represents the current user's home directory.

Example:

```bash
cd ~
```

For a user named `tryhackme`, this could represent:

```text
/home/tryhackme
```

---

### `/` — Root Directory

A single `/` represents the root of the Linux filesystem.

Example:

```bash
cd /
```

moves to the root directory.

---

## 7. Absolute and Relative Paths

### Absolute Path

An absolute path gives the complete location starting from `/`.

Example:

```text
/home/tryhackme/Documents/notes.txt
```

It does not depend on the current directory.

### Relative Path

A relative path specifies a location based on the current directory.

If I am currently in:

```text
/home/tryhackme
```

I can use:

```bash
cd Documents
```

to enter the `Documents` directory.

### Easy difference

```text
Absolute path → complete path from /
Relative path → path from current location
```

---

# 8. Important Linux Commands

## `pwd`

### Meaning

`pwd` = **Print Working Directory**

### Purpose

Shows the path of the directory I am currently in.

### Example

```bash
pwd
```

Possible output:

```text
/home/tryhackme
```

---

## `ls`

### Purpose

Lists files and directories in the current directory.

```bash
ls
```

Example output:

```text
Documents
Downloads
notes.txt
Pictures
```

---

## `ls -l`

Displays files and directories in a detailed/long listing format.

```bash
ls -l
```

It can show information such as:

* File permissions
* Owner
* Group
* File size
* Modification time
* Filename

---

## `ls -a`

Shows all files and directories, including hidden files.

```bash
ls -a
```

Hidden files in Linux commonly begin with:

```text
.
```

For example:

```text
.bashrc
```

---

## `ls -la`

Combines `-l` and `-a`.

```bash
ls -la
```

It provides a detailed listing while also showing hidden files.

### Remember

```text
ls      → list
-l      → long/detailed
-a      → all, including hidden
```

---

## `cd`

### Meaning

`cd` = **Change Directory**

### Purpose

Used to move between directories.

Example:

```bash
cd Documents
```

Move to the parent directory:

```bash
cd ..
```

Go to the home directory:

```bash
cd ~
```

Go to the root directory:

```bash
cd /
```

---

## `cat`

### Purpose

Displays the contents of a file.

Example:

```bash
cat notes.txt
```

If the file contains:

```text
Hello World!
```

`cat` displays:

```text
Hello World!
```

---

## `mkdir`

### Meaning

`mkdir` = **Make Directory**

### Purpose

Creates a new directory.

Example:

```bash
mkdir test
```

Creates:

```text
test/
```

---

## `rmdir`

### Purpose

Removes an **empty directory**.

Example:

```bash
rmdir test
```

If the directory contains files, `rmdir` will not normally remove it.

---

## `touch`

### Purpose

Commonly used to create a new empty file.

Example:

```bash
touch notes.txt
```

Creates:

```text
notes.txt
```

If the file already exists, `touch` can update its modification timestamp.

---

## `cp`

### Meaning

`cp` = **Copy**

### Purpose

Copies files or directories.

Example:

```bash
cp notes.txt backup.txt
```

This creates a copy called `backup.txt`.

The original `notes.txt` remains.

```text
notes.txt      → original
backup.txt     → copy
```

---

## `mv`

### Meaning

`mv` = **Move**

### Purpose

Moves a file or directory to another location.

Example:

```bash
mv notes.txt Documents/
```

The file is moved into the `Documents` directory.

The original is no longer in the current directory.

### `mv` can also rename files

```bash
mv old.txt new.txt
```

This renames:

```text
old.txt
```

to:

```text
new.txt
```

The file remains in the same directory.

---

## `rm`

### Meaning

`rm` = **Remove**

### Purpose

Deletes files.

Example:

```bash
rm notes.txt
```

This removes `notes.txt`.

Be careful with `rm` because deleted files may not be recoverable through a normal recycle-bin mechanism.

---

## `grep`

### Purpose

Searches for text or patterns inside files or command output.

Example:

```bash
grep "password" notes.txt
```

This searches `notes.txt` for lines containing `password`.

### Easy way to remember

```text
grep → search for text
```

---

## `find`

### Purpose

Searches for files and directories.

Example:

```bash
find /home -name "notes.txt"
```

This searches under `/home` for an item named `notes.txt`.

Another example:

```bash
find . -name "*.txt"
```

This searches from the current directory for files whose names end in `.txt`.

### Difference between `find` and `grep`

```text
find → searches for files/directories
grep → searches for text inside files
```

---

## `man`

### Meaning

`man` = **Manual**

### Purpose

Displays the manual/documentation for a Linux command.

Example:

```bash
man ls
```

This displays information about the `ls` command and its available options.

Other examples:

```bash
man cp
man mv
man find
man grep
```

If I forget how a command works, I can use its manual page.

---

# 9. File Extensions

A file extension indicates the type or format of a file.

Examples:

| Extension | Common file type   |
| --------- | ------------------ |
| `.txt`    | Text file          |
| `.jpg`    | Image              |
| `.png`    | Image              |
| `.pdf`    | PDF document       |
| `.exe`    | Windows executable |
| `.mp3`    | Audio              |
| `.mp4`    | Video              |
| `.zip`    | Compressed archive |

Example:

```text
notes.txt
```

Here:

```text
notes → filename
.txt   → file extension
```

### Important

The extension itself does not guarantee that a file is safe or actually contains the expected type of content. It is mainly an indicator of the file format/type.

---

# 10. Common Command Examples

### Navigate to a directory

```bash
cd Documents
```

### Go one directory up

```bash
cd ..
```

### Show current location

```bash
pwd
```

### List files

```bash
ls
```

### Show hidden files

```bash
ls -a
```

### Detailed listing

```bash
ls -l
```

### Create a directory

```bash
mkdir test
```

### Create an empty file

```bash
touch notes.txt
```

### Display a file

```bash
cat notes.txt
```

### Copy a file

```bash
cp notes.txt backup.txt
```

### Move a file

```bash
mv notes.txt Documents/
```

### Rename a file

```bash
mv old.txt new.txt
```

### Delete a file

```bash
rm notes.txt
```

### Remove an empty directory

```bash
rmdir test
```

### Search for text

```bash
grep "password" notes.txt
```

### Search for a file

```bash
find . -name "notes.txt"
```

### Read command documentation

```bash
man ls
```

---

# 11. Basic File and Directory Workflow

A simple workflow can look like this:

```bash
mkdir test
cd test
touch notes.txt
ls
cat notes.txt
cd ..
rmdir test
```

The commands:

1. Create a directory
2. Enter the directory
3. Create a file
4. List its contents
5. Display the file
6. Go back to the parent directory
7. Remove the directory

Note: `rmdir test` will only work after the directory is empty. If `notes.txt` is still inside it, the file must be removed first.

---

# 12. Important Concepts I Need to Remember

### Linux

Linux is based on the Linux kernel and is used across servers, desktops, networking, development, cloud, and cybersecurity.

### Terminal

The terminal allows me to interact with Linux using commands.

### Filesystem

Linux organizes files and directories in a hierarchical filesystem starting at `/`.

### Paths

```text
.   → current directory
..  → parent directory
~   → home directory
/   → root directory
```

### File operations

```text
touch  → create empty file
cp     → copy
mv     → move/rename
rm     → remove file
```

### Searching

```text
find → search for files/directories
grep → search for text
```

### Documentation

```text
man → command manual
```

---

# 13. Problems / Mistakes I Made

During revision, I initially forgot or confused:

* The purpose of `ls -la`
* The difference between `cp` and `mv`
* The purpose of `find`
* The purpose of `man`
* The meanings of `.`, `..`, `~`, and `/`
* Common file extensions such as `.txt`, `.jpg`, and `.exe`
* The difference between searching for files and searching for text

### What I learned

Instead of memorizing commands individually, I should understand their purpose and practice using them.

---

# 14. Key Takeaways

* Linux is widely used in cybersecurity and many other fields.
* The terminal allows users to interact with Linux through commands.
* `/` represents the root directory.
* `~` represents the current user's home directory.
* `.` represents the current directory.
* `..` represents the parent directory.
* Absolute paths start from `/`.
* Relative paths are based on the current directory.
* `ls` is used to list files and directories.
* `cd` is used to change directories.
* `pwd` shows the current working directory.
* `cat` displays file contents.
* `mkdir` creates directories.
* `touch` creates empty files.
* `cp` copies files.
* `mv` moves or renames files.
* `rm` removes files.
* `rmdir` removes empty directories.
* `grep` searches for text.
* `find` searches for files/directories.
* `man` provides command documentation.

---

# 15. Interview Questions

### 1. What is Linux?

Linux is an open-source operating-system family built around the Linux kernel.

### 2. What is the Linux terminal?

It is a command-line interface that allows users to interact with the operating system using commands.

### 3. What does `pwd` do?

It displays the current working directory.

### 4. What does `ls` do?

It lists files and directories.

### 5. What is the difference between `ls -l` and `ls -a`?

`ls -l` provides a detailed listing, while `ls -a` includes hidden files and directories.

### 6. What does `cd` do?

It changes the current directory.

### 7. What does `cd ..` do?

It moves to the parent directory.

### 8. What is the difference between `/` and `~`?

`/` is the root directory, while `~` represents the current user's home directory.

### 9. What does `mkdir` do?

It creates a directory.

### 10. What does `touch` do?

It commonly creates an empty file.

### 11. What is the difference between `cp` and `mv`?

`cp` creates a copy while keeping the original, whereas `mv` moves the original or can rename it.

### 12. What does `rm` do?

It removes files.

### 13. What does `grep` do?

It searches for text or patterns inside files or command output.

### 14. What does `find` do?

It searches for files and directories.

### 15. What does `man` do?

It displays the manual/documentation for a command.

### 16. What is an absolute path?

A complete path that starts from the root directory `/`.

### 17. What is a relative path?

A path that is interpreted relative to the current directory.

---

# 16. Things I Need to Revise

* [ ] Linux filesystem structure
* [ ] Absolute vs relative paths
* [ ] `ls` options
* [ ] File permissions
* [ ] More Linux commands
* [ ] Command-line navigation
* [ ] Searching with `find`
* [ ] Searching text with `grep`
* [ ] Using `man` pages

---

# 17. Final Summary

Linux Fundamentals Part 1 introduced me to the Linux command line and basic filesystem operations. I learned how to navigate directories, create and manage files, search for files and text, understand Linux paths, and use manual pages to learn commands.

These fundamentals are important for cybersecurity because Linux is widely used in servers, security tools, penetration testing environments, and security operations.

## Main Commands to Remember

```text
pwd     → current directory
ls      → list files/directories
cd      → change directory
cat     → display file contents
mkdir   → create directory
rmdir   → remove empty directory
touch   → create empty file
cp      → copy
mv      → move/rename
rm      → remove file
grep    → search text
find    → search files/directories
man     → command manual
```
