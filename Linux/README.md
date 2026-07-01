# Linux Fundamentals and Server Administration Documentation

## Introduction

Linux is an open-source, Unix-like operating system widely used in servers, cloud computing, DevOps, cybersecurity, and software development. It provides a command-line interface (CLI) that allows users to efficiently manage files, users, software packages, permissions, and system resources.

---

# 1. Basic Linux Commands

## sudo (Super User Do)

`sudo` allows a normal user to execute commands with administrator (root) privileges.

**Syntax**

```bash
sudo <command>
```

**Example**

```bash
sudo apt update
sudo apt install git
```

---

## Package Management (APT)

APT (Advanced Package Tool) is the package manager used in Debian-based Linux distributions such as Ubuntu.

### Update Package List

```bash
sudo apt update
```

Updates the package repository information.

### Upgrade Installed Packages

```bash
sudo apt upgrade
```

Installs the latest versions of installed packages.

### Full Upgrade

```bash
sudo apt full-upgrade
```

Upgrades packages and resolves dependency changes.

### Install a Package

```bash
sudo apt install <package_name>
```

Example:

```bash
sudo apt install git
```

### Remove a Package

```bash
sudo apt remove <package_name>
```

### Completely Remove a Package

```bash
sudo apt purge <package_name>
```

Removes the package along with its configuration files.

### Remove Unused Packages

```bash
sudo apt autoremove
```

### Display Package Information

```bash
apt show <package_name>
```

### List Installed Packages

```bash
apt list --installed
```

### Clean Downloaded Package Cache

```bash
sudo apt clean
```

---

# 2. User Information Commands

## Display Current User Information

```bash
id
```

Shows:

* User ID (UID)
* Group ID (GID)
* Groups the user belongs to

Example:

```bash
id
```

---

## Display Root User Information

```bash
id root
```

Displays details of the root (superuser) account.

---

## Display Current Username

```bash
id -un
```

Works similarly to:

```bash
whoami
```

---

# 3. Directory Navigation Commands

## Print Current Working Directory

```bash
pwd
```

Displays the current directory.

---

## List Directory Contents

```bash
ls
```

Lists files and folders.

---

## List Home Directory

```bash
ls ~
```

Lists the contents of the user's home directory.

---

## Change Directory

```bash
cd directory_name
```

Examples:

```bash
cd Documents
cd ..
cd ~
```

---

# 4. Creating Files and Directories

## Create a Directory

```bash
mkdir folder_name
```

Example:

```bash
mkdir testdir
```

---

## Create a File

```bash
touch filename.txt
```

Example:

```bash
touch notes.txt
```

---

## Edit a File

Using Nano Editor:

```bash
nano filename.txt
```

---

## Display File Content

```bash
cat filename.txt
```

---

# 5. Listing Files

## Long Listing Format

```bash
ls -l
```

Displays permissions, owner, size, and modification date.

---

## Show Hidden Files

```bash
ls -a
```

---

## Long Listing of a Specific Directory

```bash
ls -l testdir
```

---

## Reverse Sorting

```bash
ls -r
```

Lists files in reverse alphabetical order.

---

## Recursive Listing

```bash
ls -R
```

Displays all files and subdirectories recursively.

### Difference between `-r` and `-R`

| Option | Meaning                                 |
| ------ | --------------------------------------- |
| `-r`   | Reverse sort order                      |
| `-R`   | Recursive listing of all subdirectories |

---

# 6. File Management

## Copy Files

```bash
cp source_file destination_file
```

Example:

```bash
cp file.txt file_copy.txt
```

---

## Move or Rename Files

```bash
mv old_name new_name
```

Example:

```bash
mv file.txt notes.txt
```

---

## Remove Files

```bash
rm filename.txt
```

---

## Remove Directory Recursively

```bash
rm -r directory_name
```

Deletes the directory and all its contents.

---

## Force Delete

```bash
rm -rf directory_name
```

Removes files and directories without confirmation.

### Difference

| Option | Meaning                             |
| ------ | ----------------------------------- |
| `-r`   | Recursive deletion                  |
| `-f`   | Force deletion without confirmation |

---

# 7. Important Linux Paths

### Home Directory

```bash
~
```

Represents the current user's home directory.

---

### ZSH Configuration File

```bash
~/.zshrc
```

A hidden configuration file for the Z shell.

---

### Code Directory

```bash
~/Code
```

A commonly used folder for storing source code.

---

# 8. Linux Server Administration

## Types of Users

### Root User

* Superuser with complete system control
* Can read, write, and delete any file
* Can install software
* Can create users
* Can modify system settings

### Normal User

* Regular user with limited permissions

### System User

* Used internally by Linux services and applications

---

## Example Roles

* Administrator
* Developer
* Tester

---

# 9. User Management

## Create a New User

```bash
sudo adduser developer
```

---

## Switch User

```bash
su -
```

Switches to another user (typically root after entering the password).

---

# 10. Linux File Permissions

Linux permissions determine who can access files and directories.

There are three permission categories:

* Owner (User)
* Group
* Others

Each category can have three permissions.

| Permission | Meaning |
| ---------- | ------- |
| r          | Read    |
| w          | Write   |
| x          | Execute |

---

# 11. Changing Permissions

## Symbolic Method

Owner Read Permission

```bash
chmod u+r filename.txt
```

Group Read Permission

```bash
chmod g+r filename.txt
```

Others Read Permission

```bash
chmod o+r filename.txt
```

Make a File Executable

```bash
chmod +x filename.sh
```

---

# 12. Numeric (Octal) Permissions

Permission values:

| Permission | Value |
| ---------- | ----: |
| Read       |     4 |
| Write      |     2 |
| Execute    |     1 |

The three digits represent:

* Owner
* Group
* Others

### Numeric Permission Table

| Number | Permission |
| -----: | ---------- |
|      7 | rwx        |
|      6 | rw-        |
|      5 | r-x        |
|      4 | r--        |
|      3 | -wx        |
|      2 | -w-        |
|      1 | --x        |
|      0 | ---        |

---

## Example: 755

```
Owner  = 7 = rwx
Group  = 5 = r-x
Others = 5 = r-x
```

---

# 13. Common Permission Values

| Numeric |  Symbolic | Description                                 |
| ------: | :-------: | ------------------------------------------- |
|     777 | rwxrwxrwx | Full access for everyone (not recommended)  |
|     775 | rwxrwxr-x | Owner and group have full access            |
|     755 | rwxr-xr-x | Common for executable files and directories |
|     700 | rwx------ | Only the owner has full access              |
|     666 | rw-rw-rw- | Everyone can read and write                 |
|     644 | rw-r--r-- | Common for text files                       |
|     600 | rw------- | Private file (owner only)                   |
|     444 | r--r--r-- | Read-only for everyone                      |

---

# 14. Ownership Management

## Change File Owner

```bash
chown user filename
```

Example:

```bash
sudo chown developer notes.txt
```

---

## Change File Group

```bash
chgrp group filename
```

Example:

```bash
chgrp developers notes.txt
```

---

## Change Ownership Recursively

```bash
sudo chown -R user:group directory
```

---

# 15. Permission Management Commands

## Set Numeric Permissions

```bash
chmod 755 file
```

---

## Make File Executable

```bash
chmod +x file
```

---

## Grant Owner Read Permission

```bash
chmod u+r file
```

---

## Remove Group Write Permission

```bash
chmod g-w file
```

---

## Change Permissions Recursively

```bash
chmod -R 755 directory
```

---

# 16. Summary of Common Linux Commands

| Command             | Purpose                                        |
| ------------------- | ---------------------------------------------- |
| `sudo`              | Execute commands with administrator privileges |
| `apt update`        | Update package list                            |
| `apt upgrade`       | Upgrade installed packages                     |
| `pwd`               | Display current working directory              |
| `ls`                | List directory contents                        |
| `ls -l`             | Long listing format                            |
| `ls -a`             | Show hidden files                              |
| `ls -R`             | Recursive directory listing                    |
| `mkdir`             | Create a directory                             |
| `touch`             | Create a file                                  |
| `nano`              | Edit a file                                    |
| `cat`               | Display file contents                          |
| `cp`                | Copy files                                     |
| `mv`                | Move or rename files                           |
| `rm`                | Delete files                                   |
| `rm -r`             | Delete directories recursively                 |
| `id`                | Display user information                       |
| `whoami` / `id -un` | Display current username                       |
| `chmod`             | Change file permissions                        |
| `chown`             | Change file owner                              |
| `chgrp`             | Change file group                              |
| `su -`              | Switch to another user                         |

---

# Conclusion

Linux provides a powerful command-line environment for managing files, users, permissions, software packages, and system administration tasks. Understanding these fundamental commands and permission models is essential for careers in Cloud Computing, DevOps, System Administration, Cybersecurity, and Software Development.

