
# TryHackMe – Linux Fundamentals Part 3

**Platform:** TryHackMe
**Module:** Linux Fundamentals
**Room:** Linux Fundamentals Part 3
**Difficulty:** Beginner / Easy
**Status:** Completed ✅

---

# 1. Introduction

Linux Fundamentals Part 3 is the final room of the Linux Fundamentals series.

The room builds on the concepts learned in Parts 1 and 2 and introduces practical Linux administration and cybersecurity skills.

## Main Topics

* Terminal text editors
* File downloading and transfer
* Python HTTP server
* Process management
* Signals
* Services and `systemctl`
* Foreground and background processes
* Cron jobs and automation
* Package management with APT
* Software repositories
* GPG keys
* Linux logs
* Apache web server logs

These concepts are particularly useful for:

* Linux administration
* SOC analysis
* Incident response
* Penetration testing
* Privilege escalation
* Troubleshooting
* System monitoring

---

# 2. Deploy Your Linux Machine

The room provides a Linux machine that can be accessed through SSH.

Basic SSH syntax:

```bash
ssh username@MACHINE_IP
```

Example:

```bash
ssh tryhackme@10.48.129.97
```

The IP address is different for each deployed machine.

## Important Concept

The **AttackBox** and the **deployed Linux machine** are two separate systems.

For example:

```text
AttackBox
    |
    | SSH
    ↓
Linux Target Machine
```

You may need to open multiple terminals because some tasks require one terminal to keep a server/process running while another terminal is used to interact with it.

---

# 3. Terminal Text Editors

Linux provides several terminal-based text editors.

The room introduces:

* Nano
* Vim

---

## 3.1 Nano

Nano is a simple and beginner-friendly terminal text editor.

### Open/Create a file

```bash
nano filename
```

Example:

```bash
nano notes.txt
```

If the file doesn't exist, Nano creates it.

If the file already exists, Nano opens it for editing.

---

## Important Nano Shortcuts

| Shortcut   | Function                     |
| ---------- | ---------------------------- |
| `Ctrl + X` | Exit                         |
| `Ctrl + O` | Save/write file              |
| `Ctrl + W` | Search                       |
| `Ctrl + K` | Cut line                     |
| `Ctrl + U` | Paste                        |
| `Ctrl + C` | Show cursor/line information |
| `Ctrl + _` | Go to line                   |

Nano represents `Ctrl` shortcuts using `^`.

For example:

```text
^X = Ctrl + X
```

---

## TryHackMe Task

The task asked us to edit:

```text
task3
```

located in the `tryhackme` user's home directory.

Command:

```bash
nano task3
```

### Flag

```text
THM{TEXT_EDITORS}
```

---

# 4. Vim

Vim is a more powerful terminal text editor.

It is commonly found on Linux servers, especially when a graphical environment is unavailable.

## Why learn Vim?

* Powerful editing features
* Syntax highlighting
* Highly customizable
* Works in terminal environments
* Often installed on Linux servers

---

## Basic Vim Modes

### Normal Mode

Used for navigation and commands.

### Insert Mode

Used for typing/editing.

Enter insert mode:

```text
i
```

Return to normal mode:

```text
Esc
```

---

## Important Vim Commands

Save and exit:

```text
:wq
```

Exit without saving:

```text
:q!
```

Save:

```text
:w
```

---

# 5. General / Useful Utilities

This section introduces methods of transferring files between machines.

The major tools are:

* `wget`
* `scp`
* Python HTTP Server
* `curl`

These are extremely useful in cybersecurity labs.

---

# 6. wget

`wget` is a command-line utility used to download files from web servers.

Basic syntax:

```bash
wget URL
```

Example:

```bash
wget https://example.com/file.txt
```

The downloaded file normally appears in the current directory.

---

## Why wget is useful in cybersecurity

You may use `wget` to download:

* Scripts
* Payloads in authorized labs
* Configuration files
* Wordlists
* Tools
* Evidence/files during investigations

Example:

```bash
wget http://MACHINE_IP:8000/file.txt
```

---

# 7. SCP – Secure Copy

`scp` means **Secure Copy**.

It transfers files between computers using SSH.

Unlike normal `cp`, which works on the same system, `scp` can transfer files between machines.

## Remote → Local

```bash
scp username@REMOTE_IP:/path/to/file .
```

Example:

```bash
scp ubuntu@192.168.1.30:/home/ubuntu/document.txt .
```

The `.` means:

```text
current directory
```

---

## Local → Remote

```bash
scp file.txt username@REMOTE_IP:/path/
```

Example:

```bash
scp notes.txt tryhackme@10.10.10.10:/home/tryhackme/
```

---

## Why SCP is important

SCP uses SSH, so it provides:

* Authentication
* Encryption
* Secure file transfer

This makes it very useful when working with remote Linux machines.

---

# 8. Python HTTP Server

Python 3 contains a simple HTTP server module.

Command:

```bash
python3 -m http.server
```

By default, it starts a web server on:

```text
Port 8000
```

You will normally see:

```text
Serving HTTP on 0.0.0.0 port 8000
```

---

## How it works

Suppose we have:

```text
/home/tryhackme/
├── file.txt
├── notes.txt
└── .flag.txt
```

If we execute:

```bash
cd /home/tryhackme
python3 -m http.server
```

Python serves files from that directory.

Another machine can download them using:

```bash
wget http://MACHINE_IP:8000/file.txt
```

---

# 9. Important Lab Concept – Two Terminals

When you execute:

```bash
python3 -m http.server
```

the terminal remains occupied by the server.

Therefore:

### Terminal 1

```bash
python3 -m http.server
```

### Terminal 2

```bash
wget http://MACHINE_IP:8000/.flag.txt
```

This is an important practical concept when working with Linux servers.

Stop the HTTP server using:

```text
Ctrl + C
```

---

# 10. TryHackMe File Transfer Task

The room asked us to download:

```text
http://MACHINE_IP:8000/.flag.txt
```

using the TryHackMe AttackBox.

Command:

```bash
wget http://MACHINE_IP:8000/.flag.txt
```

The flag was:

```text
THM{WGET_WEBSERVER}
```

### Important observation

The filename starts with:

```text
.
```

Therefore it is a **hidden file**.

A normal:

```bash
ls
```

may not display it.

Use:

```bash
ls -la
```

to show hidden files.

---

# 11. Processes 101

A **process** is a running instance of a program or command.

For example, when you execute:

```bash
nano
```

Linux creates a process for Nano.

Each process has a unique identifier called a:

```text
PID = Process ID
```

---

# 12. Viewing Processes – ps

The basic command is:

```bash
ps
```

It shows processes associated with the current terminal/session.

For a more detailed list:

```bash
ps aux
```

`ps aux` is extremely important.

It displays processes belonging to different users, including system processes.

---

## Understanding ps aux

Typical columns include:

```text
USER
PID
%CPU
%MEM
VSZ
RSS
TTY
STAT
START
TIME
COMMAND
```

Important columns:

### USER

The user who owns the process.

### PID

Process ID.

### %CPU

CPU usage.

### %MEM

Memory usage.

### COMMAND

The command/program being executed.

---

# 13. Searching Processes

You can combine `ps` with `grep`.

Example:

```bash
ps aux | grep apache
```

This searches the process list for `apache`.

Another useful example:

```bash
ps aux | grep THM
```

This was useful in the TryHackMe task for locating the suspicious process containing the flag.

---

# 14. top

`top` provides a live view of running processes.

Command:

```bash
top
```

Unlike `ps`, which gives a snapshot, `top` continuously updates process information.

It can help monitor:

* CPU usage
* Memory usage
* Running processes
* Process IDs
* System load

Exit:

```text
Ctrl + C
```

---

# 15. Process IDs

Every running process has a PID.

If the previous process ID was:

```text
300
```

the next process ID in the room's question would be:

```text
301
```

### Answer

```text
301
```

Note: In real Linux systems, PID assignment can involve reuse and system-specific behavior, so don't assume PIDs always increase perfectly forever.

---

# 16. Process Signals

Linux uses **signals** to communicate with processes.

Important signals:

| Signal    | Meaning                    |
| --------- | -------------------------- |
| `SIGTERM` | Terminate gracefully       |
| `SIGKILL` | Forcefully terminate       |
| `SIGSTOP` | Stop/suspend process       |
| `SIGCONT` | Continue a stopped process |

---

## SIGTERM

```text
SIGTERM
```

asks a process to terminate and gives it an opportunity to clean up.

Example:

```bash
kill PID
```

This normally sends `SIGTERM`.

### TryHackMe Answer

```text
SIGTERM
```

---

## SIGKILL

```text
SIGKILL
```

forcefully terminates a process.

Example:

```bash
kill -9 PID
```

This should generally be used when a process doesn't respond to a graceful termination request.

---

## SIGSTOP

Suspends a process:

```bash
kill -STOP PID
```

---

## SIGCONT

Continues a stopped process:

```bash
kill -CONT PID
```

---

# 17. Finding a Process

The room contained a process with a TryHackMe flag.

Useful command:

```bash
ps aux
```

You could also narrow the output:

```bash
ps aux | grep THM
```

### Flag

```text
THM{PROCESSES}
```

This demonstrates an important cybersecurity skill:

> Don't blindly look at processes. Filter and investigate suspicious process names/commands.

---

# 18. systemd and systemctl

Modern Linux systems commonly use **systemd** to manage services.

`systemctl` is the command used to interact with systemd.

Basic structure:

```bash
systemctl OPTION SERVICE
```

---

## Start a service

```bash
systemctl start service
```

Example:

```bash
systemctl start apache2
```

---

## Stop a service

```bash
systemctl stop service
```

TryHackMe question:

```text
What command would we use to stop myservice?
```

Answer:

```bash
systemctl stop myservice
```

---

## Enable a service at boot

```bash
systemctl enable service
```

TryHackMe answer:

```bash
systemctl enable myservice
```

This means systemd should start the service automatically during boot.

---

## Disable a service at boot

```bash
systemctl disable service
```

---

## Check service status

```bash
systemctl status service
```

Example:

```bash
systemctl status apache2
```

---

## Restart a service

```bash
systemctl restart service
```

---

# 19. Background and Foreground Processes

A process can run in:

```text
Foreground
```

or:

```text
Background
```

---

## Run a command in the background

Add:

```bash
&
```

Example:

```bash
sleep 100 &
```

The command continues running while you get your terminal back.

---

## Suspend a running process

Press:

```text
Ctrl + Z
```

This suspends the current process.

---

## View background jobs

```bash
jobs
```

---

## Bring process to foreground

```bash
fg
```

TryHackMe answer:

```bash
fg
```

---

# 20. Automation – Cron

Cron is used to automatically execute commands at scheduled times.

Examples:

* Backups
* Maintenance
* Scripts
* Cleanup tasks
* Automated jobs
* Scheduled monitoring

The service responsible for running scheduled jobs is commonly called `cron`.

---

# 21. Crontab

A user's scheduled cron jobs can be viewed/edited using:

```bash
crontab -e
```

List cron jobs:

```bash
crontab -l
```

---

# 22. Cron Syntax

Traditional cron entries use:

```text
MINUTE HOUR DAY MONTH WEEKDAY COMMAND
```

Example:

```text
0 0 * * * /home/user/backup.sh
```

Meaning:

```text
At 00:00 every day
```

The five scheduling fields are:

```text
Minute
Hour
Day of Month
Month
Day of Week
```

---

# 23. Special Cron Keyword – @reboot

The room contained a cron entry using:

```text
@reboot
```

`@reboot` means:

> Run the specified command when the system starts/reboots.

### TryHackMe Answer

```text
@reboot
```

This concept is particularly important in cybersecurity because scheduled tasks can sometimes be abused for **persistence**.

---

# 24. Package Management

Linux software is commonly distributed as packages.

Ubuntu/Debian-based systems commonly use:

```text
APT
```

APT helps manage:

* Installation
* Removal
* Updates
* Software repositories
* Dependencies

---

# 25. APT

Basic commands:

### Update repository information

```bash
apt update
```

This refreshes the information about available packages.

### Install software

```bash
apt install package-name
```

Example:

```bash
apt install sublime-text
```

### Remove software

```bash
apt remove package-name
```

Example:

```bash
apt remove sublime-text
```

---

# 26. Software Repositories

A repository is a location containing software packages.

Ubuntu has official repositories, but additional third-party repositories can also be added.

One command used to add a repository is:

```bash
add-apt-repository
```

Repository configuration can also be stored under:

```text
/etc/apt/sources.list.d/
```

---

# 27. GPG Keys

GPG stands for:

```text
GNU Privacy Guard
```

GPG keys can be used to verify the authenticity/integrity of software packages and repositories.

The basic idea is:

```text
Software Repository
        ↓
GPG verification
        ↓
Trusted software
        ↓
Installation
```

This helps protect users from installing software from an untrusted or tampered source.

---

# 28. Adding a Third-Party Repository

The room demonstrates adding a third-party repository using Sublime Text as an example.

General process:

### Step 1 – Trust the developer's GPG key

```bash
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
```

### Step 2 – Add repository information

A repository file can be created under:

```text
/etc/apt/sources.list.d/
```

For example:

```text
sublime-text.list
```

### Step 3 – Update APT

```bash
apt update
```

### Step 4 – Install software

```bash
apt install sublime-text
```

---

# 29. Removing a Repository

A repository can be removed using:

```bash
add-apt-repository --remove ppa:PPA_Name/ppa
```

Alternatively, its repository configuration file can be removed from:

```text
/etc/apt/sources.list.d/
```

Then the package itself can be removed:

```bash
apt remove package-name
```

### Important TryHackMe Note

The deployed TryHackMe machines used for this task do not have Internet access, so the repository installation portion was mainly for understanding rather than performing it on the lab machine.

---

# 30. Linux Logs

Linux logs are extremely important for system administration and cybersecurity.

Most traditional Linux log files are located under:

```text
/var/log
```

Check the directory:

```bash
ls /var/log
```

Detailed listing:

```bash
ls -la /var/log
```

---

# 31. Why Logs Matter

Logs can tell us:

* Who accessed a service
* When something happened
* What service generated an event
* Which IP address made a request
* What file was requested
* Authentication attempts
* Errors
* Service activity
* Potential attacker activity

This makes logs extremely valuable for:

* SOC analysts
* Incident responders
* System administrators
* Forensic investigators

---

# 32. Log Rotation

Logs can become very large.

Linux systems therefore use **log rotation** to manage log files.

You may see files such as:

```text
access.log
access.log.1
access.log.2.gz
```

The older logs are rotated so that the current log does not grow indefinitely.

---

# 33. Apache2 Logs

Apache is a web server.

Its logs on the TryHackMe machine were located in:

```text
/var/log/apache2
```

Navigate:

```bash
cd /var/log/apache2
```

List files:

```bash
ls -la
```

---

# 34. Apache Access Log

An **access log** records requests made to the web server.

It can contain information such as:

```text
IP address
Date/time
HTTP method
Requested resource
HTTP status code
User-Agent
```

For example:

```text
10.9.232.111 - - [date] "GET /catsanddogs.jpg HTTP/1.1" 200 ...
```

From this we can identify:

```text
IP → 10.9.232.111
Requested file → catsanddogs.jpg
```

---

# 35. Apache Error Log

The error log contains errors and problems encountered by Apache.

Typical uses:

* Troubleshooting
* Finding failed requests
* Investigating server problems
* Detecting suspicious activity

---

# 36. TryHackMe Log Investigation

The room asked us to find the Apache logs.

Location:

```bash
/var/log/apache2
```

A relevant rotated access log was:

```text
access.log.1
```

Read it using:

```bash
cat /var/log/apache2/access.log.1
```

or:

```bash
cd /var/log/apache2
cat access.log.1
```

---

## Question 1

**What is the IP address of the user who visited the site?**

Answer:

```text
10.9.232.111
```

---

## Question 2

**What file did they access?**

Answer:

```text
catsanddogs.jpg
```

---

# 37. Security Importance of Web Logs

Suppose an attacker requests:

```text
/admin
```

or:

```text
/login
```

or:

```text
/wp-admin
```

The web server may record the request.

A security analyst can investigate:

```text
Source IP
     ↓
Timestamp
     ↓
Requested URL
     ↓
HTTP status
     ↓
User-Agent
     ↓
Other related logs
```

This can help reconstruct what happened during an incident.

---

# 38. Important Commands From This Room

## Text Editing

```bash
nano filename
vim filename
```

## File Download

```bash
wget URL
```

## Secure File Transfer

```bash
scp user@IP:/path/file .
scp file user@IP:/path/
```

## Python Web Server

```bash
python3 -m http.server
```

## Process Management

```bash
ps
ps aux
top
kill PID
kill -9 PID
```

## Background/Foreground

```bash
command &
jobs
fg
```

## Services

```bash
systemctl start service
systemctl stop service
systemctl restart service
systemctl status service
systemctl enable service
systemctl disable service
```

## Cron

```bash
crontab -e
crontab -l
```

## Package Management

```bash
apt update
apt install package
apt remove package
add-apt-repository
```

## Logs

```bash
ls /var/log
cd /var/log/apache2
cat access.log.1
```

---

# 39. TryHackMe Answers – Quick Revision

| Task   | Question                      | Answer                       |
| ------ | ----------------------------- | ---------------------------- |
| Task 3 | Edit `task3` using Nano       | `THM{TEXT_EDITORS}`          |
| Task 4 | Download `.flag.txt`          | `THM{WGET_WEBSERVER}`        |
| Task 5 | Previous PID = 300, next PID? | `301`                        |
| Task 5 | Cleanly kill process          | `SIGTERM`                    |
| Task 5 | Process flag                  | `THM{PROCESSES}`             |
| Task 5 | Stop `myservice`              | `systemctl stop myservice`   |
| Task 5 | Start `myservice` at boot     | `systemctl enable myservice` |
| Task 5 | Background → foreground       | `fg`                         |
| Task 6 | Cron execution time           | `@reboot`                    |
| Task 8 | Visitor IP                    | `10.9.232.111`               |
| Task 8 | Accessed file                 | `catsanddogs.jpg`            |

---

# 40. Cybersecurity Takeaways

This room is especially important for cybersecurity because these Linux skills appear repeatedly in later rooms.

## 1. Process Enumeration

Use:

```bash
ps aux
top
```

to identify suspicious processes.

## 2. Process Investigation

Use:

```bash
ps aux | grep process
```

to search for specific processes.

## 3. Persistence

Cron jobs and services can be configured to execute automatically.

Important locations/commands:

```bash
crontab -e
systemctl enable service
```

## 4. File Transfer

Useful during penetration testing and lab environments:

```bash
wget
scp
python3 -m http.server
```

## 5. Log Analysis

Logs can reveal attacker activity.

Important directory:

```text
/var/log
```

Important example:

```text
/var/log/apache2/access.log
```

## 6. Service Management

Knowing `systemctl` is essential for understanding Linux services:

```bash
systemctl status
systemctl start
systemctl stop
systemctl enable
```

---

# 41. Final Mental Map

Think of Linux Fundamentals Part 3 like this:

```text
             Linux Fundamentals Part 3
                       |
       ┌───────────────┼────────────────┐
       ↓               ↓                ↓
  Text Editors    File Transfer     Processes
       |               |                |
   nano / vim      wget / scp       ps / top
                       |                |
                Python HTTP Server    kill
                                        |
                                    systemctl
                                        |
                         ┌──────────────┴─────────────┐
                         ↓                            ↓
                      Cron                         Logs
                         |                            |
                    crontab -e                    /var/log
                         |                            |
                     @reboot                    Apache logs
                                                      |
                                                access.log
                                                      |
                                             IP + requested file
```

---

# 42. What I Learned

After completing Linux Fundamentals Part 3, I can:

* Use Nano to create and edit files.
* Understand the basic purpose of Vim.
* Download files using `wget`.
* Transfer files using `scp`.
* Start a temporary Python HTTP server.
* Understand ports used by a simple HTTP server.
* Identify running processes using `ps`.
* Monitor processes using `top`.
* Understand PIDs.
* Send signals to processes using `kill`.
* Understand `SIGTERM`, `SIGKILL`, and `SIGSTOP`.
* Manage Linux services using `systemctl`.
* Move processes between foreground and background.
* Understand cron jobs and `@reboot`.
* Understand Linux package management using APT.
* Understand repositories and GPG verification.
* Locate Linux logs under `/var/log`.
* Read Apache access logs.
* Extract useful information such as source IP addresses and requested files.
* Understand why logs are important in cybersecurity investigations.

---

# 43. Most Important Commands to Memorize

If you don't want to memorize everything immediately, start with these:

```bash
nano file
```

```bash
wget URL
```

```bash
scp user@IP:/path/file .
```

```bash
python3 -m http.server
```

```bash
ps aux
```

```bash
top
```

```bash
kill PID
```

```bash
systemctl status service
```

```bash
systemctl stop service
```

```bash
systemctl enable service
```

```bash
fg
```

```bash
crontab -e
```

```bash
apt update
```

```bash
apt install package
```

```bash
apt remove package
```

```bash
ls -la /var/log
```

```bash
cat /var/log/apache2/access.log.1
```

---

# 44. Final Conclusion

Linux Fundamentals Part 3 completes the Linux Fundamentals series.

The most important progression is:

```text
Part 1
Linux basics
   ↓
Part 2
Filesystem + permissions + SSH
   ↓
Part 3
Processes + services + automation
+ package management + logs
```

The most cybersecurity-relevant concepts from this room are:

```text
ps aux
   ↓
Process Enumeration

systemctl
   ↓
Service Management

crontab
   ↓
Automation / Persistence

wget / scp / HTTP Server
   ↓
File Transfer

/var/log
   ↓
Log Analysis / Investigation
```

These concepts will appear again and again in Linux privilege escalation, SOC, incident response, penetration testing, and TryHackMe rooms.

**Linux Fundamentals Part 3 — COMPLETED ✅**
