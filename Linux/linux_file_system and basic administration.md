# Day 6 – Linux File System & Basic Administration

## Objective

The objective of this session is to learn the fundamentals of Linux file system management and basic system administration. By the end of this practice, you will be able to:

* Navigate directories and understand the Linux file system structure.
* Create, copy, move, rename, and delete files and directories.
* View and edit file contents.
* Check system information such as CPU, memory, disk, and operating system details.
* Understand and manage file permissions.
* Monitor running processes and basic network information.

---

# Step 1: Connect to AWS EC2

## Start the EC2 Instance

1. Open the AWS Management Console.
2. Navigate to **EC2 Dashboard**.
3. Select your EC2 instance.
4. Click **Start Instance**.

Wait until the instance status shows:

```text
2/2 Status Checks Passed
```

## Connect Using SSH

```bash
cd ~
chmod 400 cloud-key.pem
ssh -i cloud-key.pem ubuntu@YOUR_PUBLIC_IP
```

### Explanation

* `cd ~` → Moves to the home directory.
* `chmod 400 cloud-key.pem` → Secures the private key file.
* `ssh -i cloud-key.pem ubuntu@YOUR_PUBLIC_IP` → Connects to the EC2 instance using SSH.

---

# Step 2: Verify Connection

```bash
pwd
whoami
hostname
```

### Command Explanation

| Command    | What it Shows             | Why It Is Useful                                        |
| ---------- | ------------------------- | ------------------------------------------------------- |
| `pwd`      | Current working directory | Helps identify your current location in the file system |
| `whoami`   | Logged-in username        | Confirms which user account is active                   |
| `hostname` | Server hostname           | Identifies the machine you are connected to             |

---

# Step 3: Navigate Directories

### Show Current Directory

```bash
pwd
```

### List Files and Directories

```bash
ls
```

### Detailed Listing

```bash
ls -la
```

### Move to Root Directory

```bash
cd /
```

### Move to Home Directory

```bash
cd ~
```

### Concept

* `/` represents the root directory.
* `~` represents the current user's home directory.
* `cd` is used to change directories.

---

# Step 4: Create Directories

Create a project directory:

```bash
mkdir CloudEngineering
cd CloudEngineering
```

Create subdirectories:

```bash
mkdir Projects
mkdir Notes
mkdir Practice
```

### Explanation

* `mkdir` creates new directories.
* Organizing files into directories improves project management.

---

# Step 5: View Directory Structure

Install Tree Utility:

```bash
sudo apt update
sudo apt install tree -y
```

Display directory structure:

```bash
tree
```

### Why Use Tree?

The `tree` command displays directories and files in a hierarchical structure, making it easier to understand folder organization.

---

# Step 6: Create Files

```bash
touch day6.txt
touch notes.txt
touch linux.txt
```

Verify:

```bash
ls
```

### Explanation

The `touch` command creates empty files.

---

# Step 7: Write Data into Files

### Overwrite File Content

```bash
echo "Hello Cloud" > day6.txt
```

### Append Content

```bash
echo "Learning AWS" >> day6.txt
```

### View File Content

```bash
cat day6.txt
```

### Explanation

* `>` replaces existing content.
* `>>` adds content without removing existing data.
* `cat` displays file contents.

---

# Step 8: Edit Files Using Nano

```bash
nano notes.txt
```

### Save File

```text
Ctrl + O
Enter
```

### Exit Nano

```text
Ctrl + X
```

### Why Nano?

Nano is a beginner-friendly text editor commonly used in Linux servers.

---

# Step 9: Copy Files

```bash
cp notes.txt backup.txt
```

Verify:

```bash
ls
```

### Explanation

The `cp` command creates a duplicate copy of a file.

---

# Step 10: Rename or Move Files

```bash
mv backup.txt backup_notes.txt
```

### Explanation

The `mv` command is used to:

* Rename files.
* Move files between directories.

---

# Step 11: Delete Files and Directories

Delete a file:

```bash
rm delete_me.txt
```

Delete a directory:

```bash
rm -r temp
```

### Warning

Deleted files cannot be recovered easily. Use the `rm` command carefully.

---

# Step 12: Search Files

Search all text files:

```bash
find . -name "*.txt"
```

Search a specific file:

```bash
find . -name "notes.txt"
```

### Explanation

The `find` command searches for files and directories based on specified criteria.

---

# Step 13: File Permissions

View permissions:

```bash
ls -l
```

Change permissions:

```bash
chmod 644 notes.txt
```

Verify:

```bash
ls -l
```

### Understanding Permission 644

```text
Owner  : Read + Write
Group  : Read
Others : Read
```

### Why Permissions Matter

Permissions protect files from unauthorized access and modifications.

---

# Step 14: Disk Usage

View disk usage:

```bash
df -h
```

View current directory size:

```bash
du -sh .
```

### Explanation

* `df -h` displays available and used disk space.
* `du -sh .` displays the size of the current directory.

---

# Step 15: Memory Usage

```bash
free -h
```

### What It Shows

* Total memory
* Used memory
* Free memory
* Swap memory

### Why Useful?

Helps monitor system resource usage.

---

# Step 16: CPU Information

```bash
lscpu
```

### What It Shows

* CPU architecture
* Number of cores
* Threads
* CPU model

### Why Useful?

Helps understand server hardware capabilities.

---

# Step 17: Operating System Information

```bash
cat /etc/os-release
```

### What It Shows

Information about the installed Linux distribution and version.

---

# Step 18: Network Information

### IP Address

```bash
hostname -I
```

### Network Interfaces

```bash
ip addr
```

### Routing Table

```bash
ip route
```

### Purpose

These commands help diagnose and understand network connectivity.

---

# Step 19: Process Management

### View Running Processes

```bash
ps
```

### View All Processes

```bash
ps aux
```

### Real-Time Process Monitoring

```bash
top
```

Exit:

```text
q
```

### Why Useful?

Process monitoring helps identify running applications and resource usage.

---

# Troubleshooting Guide

## Error: Permission Denied

### Cause

You do not have the required permissions.

### Solution

```bash
ls -l
sudo command
```

---

## Error: No Such File or Directory

### Cause

Incorrect file or directory path.

### Solution

```bash
pwd
ls
```

Verify your current location and file names.

---

## Error: tree: command not found

### Solution

```bash
sudo apt update
sudo apt install tree -y
```

---

## Error: nano: command not found

### Solution

```bash
sudo apt install nano -y
```

---

## Error: Operation Not Permitted

### Cause

Administrative privileges are required.

### Solution

```bash
sudo command
```

---

# Commands Learned

| Command       | Purpose                      |
| ------------- | ---------------------------- |
| `pwd`         | Show current directory       |
| `ls`          | List files and directories   |
| `ls -la`      | Detailed file listing        |
| `cd`          | Change directory             |
| `mkdir`       | Create directory             |
| `touch`       | Create file                  |
| `echo`        | Write text to file           |
| `cat`         | Display file contents        |
| `nano`        | Edit files                   |
| `cp`          | Copy files                   |
| `mv`          | Move or rename files         |
| `rm`          | Delete files                 |
| `find`        | Search files                 |
| `chmod`       | Change permissions           |
| `df -h`       | Display disk usage           |
| `du -sh`      | Display directory size       |
| `free -h`     | Display memory usage         |
| `lscpu`       | Display CPU information      |
| `hostname -I` | Display IP address           |
| `ip addr`     | Display network interfaces   |
| `ip route`    | Display routing table        |
| `ps`          | Show running processes       |
| `ps aux`      | Show all processes           |
| `top`         | Real-time process monitoring |

---

# Key Concepts Learned

* Linux File System Structure
* Root Directory (`/`)
* Home Directory (`~`)
* Absolute and Relative Paths
* Files and Directories
* File Permissions
* Process Management
* CPU Monitoring
* Memory Monitoring
* Disk Monitoring
* Network Configuration

---

# Daily Practice Checklist

Before ending your session:

* Verify all commands have been practiced.
* Save any notes or documentation created.
* Exit the SSH session:

```bash
exit
```

* Stop the EC2 instance from the AWS Console to avoid unnecessary charges.
* Record any new commands, errors, or observations in your learning journal.

## Conclusion

This lab provided hands-on experience with Linux file system navigation, file management, permissions, system monitoring, networking, and process management. These skills form the foundation of Linux administration and are essential for Cloud, DevOps, and AI Cloud Engineering roles.

