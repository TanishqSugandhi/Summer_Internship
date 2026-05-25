# 1. Linux Environment Comparison Study

This document contains a comprehensive analysis and side-by-side comparison of the core methods used to host, run, and interact with a Linux operating system ecosystem. 

---

## Environment Evaluation Matrix

The table below breaks down performance metrics, installation difficulty, resource footprints, and primary industry use cases for each deployment strategy.

| Feature | Native Linux | WSL (Windows Subsystem) | Virtual Machine (VM) | Online Platforms |
| :--- | :--- | :--- | :--- | :--- |
| **Performance** | **Maximum** <br>*(Direct hardware access)* | **High** <br>*(Lightweight VM integration)* | **Moderate** <br>*(Hardware emulation overhead)* | **Variable** <br>*(Depends on cloud provider)* |
| **Resource Usage** | Low / Optimized | Low to Moderate | **High** <br>*(Requires dedicated RAM/CPU)* | **None** on local machine |
| **Installation** | **Hard** <br>*(Requires partitioning/Dual-boot)* | **Easy** <br>*(Simple Windows Store command)* | **Medium** <br>*(Requires VirtualBox/VMware)* | **Instant** <br>*(Web browser based)* |
| **Best Used For** | Production servers, primary OS | Windows developers needing Linux tools | Isolated testing, malware analysis | Quick practice, learning syntax |

---

## Key Insights

* **Native Linux** remains the absolute gold standard for production deployment and bare-metal performance, though it carries a high friction cost for local workspace provisioning.
* **WSL 2** offers an exceptional bridge for development pipelines within an active enterprise Windows environment without hurting local hardware availability.
* **Virtual Machines** act as ideal, fully sandbox-isolated environments for testing risky administrative changes, deployment states, or destructive commands.
* **Online Platforms** provide a zero-risk sandboxed ecosystem perfect for quick syntax evaluations, running scripts on the fly, and learning fundamental commands.

# 2. Linux Terminal Commands Practice

## Introduction

Linux provides a powerful command-line interface (CLI) to interact with the operating system.  
This section demonstrates commonly used Linux terminal commands related to file management, users, permissions, networking, processes, and package management.

---

# a. File and Directory Commands

These commands are used to create, manage, copy, move, and delete files and folders.

---

## Display Current Directory

```bash
pwd
```

Displays the current working directory.

---

## List Files and Directories

```bash
ls
```

Lists files and folders in the current directory.

---

## Detailed File Listing

```bash
ls -l
```

Shows detailed file information including permissions and ownership.

---

## Create Directory

```bash
mkdir project
```

Creates a new directory named `project`.

---

## Create File

```bash
touch file.txt
```

Creates an empty file named `file.txt`.

---

## Copy File

```bash
cp file.txt backup.txt
```

Copies `file.txt` into `backup.txt`.

---

## Move/Rename File

```bash
mv file.txt documents/
```

Moves the file into another directory.

---

## Delete File

```bash
rm file.txt
```

Deletes a file.

---

## Delete Directory

```bash
rmdir project
```

Removes an empty directory.

---

# b. User Management Commands

Linux supports multiple users with secure access control.

---

## Display Current User

```bash
whoami
```

Shows the currently logged-in user.

---

## Create New User

```bash
sudo adduser student
```

Creates a new user named `student`.

---

## Change Password

```bash
passwd
```

Changes the password of the current user.

---

## Display User ID Information

```bash
id
```

Displays UID, GID, and group information.

---

## Show User Groups

```bash
groups
```

Displays groups associated with the user.

---

# c. File Permission Commands

Linux uses permissions for system security and access control.

---

## Permission Symbols

| Symbol | Meaning |
|---|---|
| r | Read |
| w | Write |
| x | Execute |

---

## Example Permission Format

```text
rwxr-xr-x
```

---

## Change File Permissions

```bash
chmod 755 script.sh
```

Changes file permissions.

---

## Change File Ownership

```bash
sudo chown user:user file.txt
```

Changes file owner and group.

---

## Make Script Executable

```bash
chmod +x script.sh
```

Adds execute permission to the script.

---

# d. Networking Commands

Networking commands are used to monitor and troubleshoot networks.

---

## Check Internet Connectivity

```bash
ping google.com
```

Tests network connectivity.

---

## Display Network Configuration

```bash
ifconfig
```

Displays network interface information.

---

## Show IP Address

```bash
ip addr
```

Shows detailed IP configuration.

---

## Download Web Content

```bash
curl https://example.com
```

Retrieves data from a website.

---

## Download Files

```bash
wget https://example.com/file.zip
```

Downloads files from the internet.

---

# e. Process Management Commands

Processes are running programs inside Linux.

---

## Show Running Processes

```bash
ps
```

Displays current processes.

---

## Real-Time Process Monitoring

```bash
top
```

Shows CPU and memory usage in real time.

---

## Interactive Process Viewer

```bash
htop
```

Advanced process monitoring tool.

---

## Kill Process Using PID

```bash
kill PID
```

Terminates a process.

---

## Kill Process by Name

```bash
killall firefox
```

Kills all processes with the given name.

---

# f. Package Installation Commands

Package managers help install and update software.

---

# Ubuntu/Debian Package Commands

## Update Package List

```bash
sudo apt update
```

Updates package information.

---

## Upgrade Packages

```bash
sudo apt upgrade
```

Upgrades installed packages.

---

## Install Software

```bash
sudo apt install gcc
```

Installs GCC compiler.

---

## Remove Software

```bash
sudo apt remove gcc
```

Removes installed package.

---

# Fedora Package Commands

## Install Package

```bash
sudo dnf install gcc
```

Installs software using DNF package manager.

---

# Conclusion

Linux terminal commands provide efficient system management, automation, software installation, and troubleshooting capabilities.


# 3. Basic Shell Scripts in Linux

## Introduction

Shell scripting is used to automate repetitive Linux tasks using Bash commands.  
The following scripts demonstrate basic Linux automation tasks.

---

# a. File Backup Script

## Objective

Create a shell script to back up files or directories from one location to another.

---

## Script: `backup.sh`

```bash
#!/bin/bash

# File Backup Script

SOURCE=$1
DESTINATION=$2

echo "Starting Backup..."

cp -r $SOURCE $DESTINATION

echo "Backup Completed Successfully."
```

---

## Usage

```bash
chmod +x backup.sh
./backup.sh source_folder backup_folder
```

---

## Explanation

| Command | Description |
|---|---|
| `#!/bin/bash` | Specifies Bash shell |
| `cp -r` | Copies directories recursively |
| `$1` | First user argument |
| `$2` | Second user argument |

---

# b. Folder Creation Script

## Objective

Automatically create folders using a shell script.

---

## Script: `create_folder.sh`

```bash
#!/bin/bash

# Folder Creation Script

FOLDER_NAME=$1

mkdir -p $FOLDER_NAME

echo "Folder '$FOLDER_NAME' created successfully."
```

---

## Usage

```bash
chmod +x create_folder.sh
./create_folder.sh Linux_Project
```

---

## Explanation

| Command | Description |
|---|---|
| `mkdir` | Creates directory |
| `-p` | Creates parent directories if needed |
| `$1` | User-provided folder name |

---

# c. System Information Display Script

## Objective

Display important system information such as kernel details, uptime, memory, and disk usage.

---

## Script: `system_info.sh`

```bash
#!/bin/bash

# System Information Script

echo "==============================="
echo " SYSTEM INFORMATION "
echo "==============================="

echo ""
echo "Kernel Information:"
uname -a

echo ""
echo "System Uptime:"
uptime

echo ""
echo "Disk Usage:"
df -h

echo ""
echo "Memory Usage:"
free -m
```

---

## Usage

```bash
chmod +x system_info.sh
./system_info.sh
```

---

## Explanation

| Command | Description |
|---|---|
| `uname -a` | Displays kernel details |
| `uptime` | Shows system uptime |
| `df -h` | Displays disk usage |
| `free -m` | Displays memory usage |

---

# d. CPU and Memory Monitoring Script

## Objective

Monitor CPU usage and memory consumption in Linux.

---

## Script: `monitor.sh`

```bash
#!/bin/bash

# CPU and Memory Monitoring Script

echo "==============================="
echo " CPU USAGE "
echo "==============================="

top -bn1 | head -5

echo ""
echo "==============================="
echo " MEMORY USAGE "
echo "==============================="

free -h
```

---

## Usage

```bash
chmod +x monitor.sh
./monitor.sh
```

---

## Explanation

| Command | Description |
|---|---|
| `top -bn1` | Displays CPU/process information |
| `head -5` | Limits output lines |
| `free -h` | Displays memory in human-readable format |

---

# Advantages of Shell Scripting

- Automation of repetitive tasks
- Faster system administration
- Reduced manual effort
- Improved productivity

---

# Conclusion

Shell scripting is an essential Linux skill used for automation, monitoring, system management, and development workflows.

# 5. Linux Development Tools

## Introduction

Linux provides powerful development tools for compiling, debugging, editing, version control, and memory analysis.  
These tools are widely used in software development, embedded systems, and system programming.

---

# a. GCC (GNU Compiler Collection)

## Objective

Compile and execute C programs using GCC.

---

## Sample C Program

### File: `hello.c`

```c
#include <stdio.h>

int main() {
    printf("Hello, Linux Development Tools!\n");
    return 0;
}
```

---

## Compile Program

```bash
gcc hello.c -o hello
```

---

## Run Program

```bash
./hello
```

---

## Explanation

| Command | Description |
|---|---|
| `gcc` | GNU C Compiler |
| `-o` | Output executable name |
| `./hello` | Executes compiled program |

---

# b. GDB (GNU Debugger)

## Objective

Debug programs and inspect execution flow.

---

## Compile with Debugging Symbols

```bash
gcc -g hello.c -o hello
```

---

## Start GDB

```bash
gdb ./hello
```

---

## Common GDB Commands

```bash
break main
run
next
print variable
quit
```

---

## Explanation

| Command | Description |
|---|---|
| `break main` | Sets breakpoint |
| `run` | Starts program |
| `next` | Executes next line |
| `print` | Displays variable value |
| `quit` | Exits GDB |

---

# c. Make Utility

## Objective

Automate software compilation using Makefiles.

---

## Sample Makefile

### File: `Makefile`

```make
all:
	gcc hello.c -o hello
```

---

## Run Make

```bash
make
```

---

## Clean Build Files

```make
clean:
	rm -f hello
```

---

## Run Clean Command

```bash
make clean
```

---

## Explanation

| Command | Description |
|---|---|
| `make` | Executes Makefile |
| `make clean` | Removes compiled files |

---

# d. Vim and Nano Editors

## Objective

Edit files directly from Linux terminal.

---

# Vim Editor

## Open File in Vim

```bash
vim file.txt
```

---

## Vim Basic Commands

| Command | Description |
|---|---|
| `i` | Insert mode |
| `Esc` | Exit insert mode |
| `:w` | Save file |
| `:q` | Quit |
| `:wq` | Save and quit |

---

# Nano Editor

## Open File in Nano

```bash
nano file.txt
```

---

## Nano Shortcuts

| Shortcut | Description |
|---|---|
| `Ctrl + O` | Save |
| `Ctrl + X` | Exit |
| `Ctrl + K` | Cut line |

---

# Comparison

| Editor | Difficulty |
|---|---|
| Vim | Advanced |
| Nano | Beginner Friendly |

---

# e. Git Version Control

## Objective

Track source code changes using Git.

---

## Initialize Repository

```bash
git init
```

---

## Check Status

```bash
git status
```

---

## Add Files

```bash
git add .
```

---

## Commit Changes

```bash
git commit -m "Initial Commit"
```

---

## Connect Remote Repository

```bash
git remote add origin https://github.com/username/repository.git
```

---

## Push Code to GitHub

```bash
git push -u origin main
```

---

## Explanation

| Command | Description |
|---|---|
| `git init` | Creates repository |
| `git add` | Stages files |
| `git commit` | Saves changes |
| `git push` | Uploads code |

---

# f. Valgrind

## Objective

Detect memory leaks and memory-related errors.

---

## Install Valgrind

```bash
sudo apt install valgrind
```

---

## Run Valgrind

```bash
valgrind ./hello
```

---

## Example Output

```text
==1234== HEAP SUMMARY:
==1234==     in use at exit: 0 bytes in 0 blocks
==1234==   total heap usage: 1 allocs, 1 frees
```

---

## Applications

- Memory leak detection
- Invalid memory access detection
- Performance profiling

---

# Advantages of Linux Development Tools

- Open-source
- Efficient debugging
- Automation support
- Powerful development workflow
- Widely used in industry

---

# Conclusion

Linux development tools simplify software development, debugging, automation, version control, and memory management for developers and system engineers.


# 6. Technical Documentation Assignment

## Objective

Create a properly formatted technical report in PDF format using:

- LaTeX
OR
- Markdown + Pandoc

This assignment demonstrates professional technical documentation practices used in Linux environments.

---

# a. Introduction to Technical Documentation

Technical documentation is used to present information in a structured and professional format.

It is widely used for:
- Project Reports
- Research Papers
- Software Documentation
- System Manuals
- Internship Reports

---

# b. Documentation Using Markdown

Markdown is a lightweight markup language used to create formatted text documents easily.

---

## Advantages of Markdown

- Simple syntax
- Easy to read and write
- Lightweight
- Compatible with GitHub
- Easy PDF conversion using Pandoc

---

# Sample Markdown Report

## File: `report.md`

```markdown
# Linux Internship Assignment Report

## Introduction

This report contains Linux concepts, terminal commands, shell scripting, and development tools studied during the internship.

---

# Topics Covered

- Linux Environments
- Linux Commands
- Shell Scripting
- Development Tools
- Technical Documentation

---

# Conclusion

This internship improved understanding of Linux systems, automation, and software development tools.
```

---

# c. Installing Pandoc

Pandoc is a document converter used to convert Markdown files into PDF and other formats.

---

## Install Pandoc

### Ubuntu/Debian

```bash
sudo apt install pandoc
```

---

## Verify Installation

```bash
pandoc --version
```

---

# d. Convert Markdown to PDF

## Command

```bash
pandoc report.md -o report.pdf
```

---

## Explanation

| Command | Description |
|---|---|
| `pandoc` | Document converter |
| `report.md` | Input Markdown file |
| `-o` | Output file |
| `report.pdf` | Generated PDF report |

---

# e. Documentation Using LaTeX

LaTeX is a professional document preparation system used for scientific and technical reports.

---

# Advantages of LaTeX

- Professional formatting
- Better mathematical support
- Automatic numbering and references
- Widely used in academia

---

# Sample LaTeX Document

## File: `report.tex`

```latex
\documentclass{article}

\title{Linux Internship Assignment Report}
\author{Tanishq Sugandhi}

\begin{document}

\maketitle

\section{Introduction}

This report documents Linux concepts, commands, shell scripting, and development tools.

\section{Conclusion}

The assignment improved understanding of Linux systems and development tools.

\end{document}
```

---

# f. Compile LaTeX File

## Install LaTeX

```bash
sudo apt install texlive-full
```

---

## Generate PDF

```bash
pdflatex report.tex
```

---

# Output Files

| File | Description |
|---|---|
| `report.md` | Markdown source |
| `report.tex` | LaTeX source |
| `report.pdf` | Final PDF report |

---

# Applications of Technical Documentation

- Software Engineering
- Research Publications
- Project Documentation
- Linux System Administration
- Academic Reports

---

# Conclusion

Markdown, Pandoc, and LaTeX provide efficient methods for creating professional technical reports in Linux environments.
