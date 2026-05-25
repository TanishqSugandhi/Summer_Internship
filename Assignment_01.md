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

# 4. Networking Commands

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

# d. Process Management Commands

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

# e. Package Installation Commands

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
