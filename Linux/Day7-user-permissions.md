# Linux Users, Groups & Permissions Documentation

## 1. What is a User?

A **user** is an account used to access and work on a Linux system.

Examples:

```text
ubuntu
developer
nithin
```

Check current user:

```bash
whoami
```

or

```bash
id -un
```

Why users exist:

* Security
* Personal workspace
* Access control
* Activity tracking

---

# 2. What is the Root User?

The **root user** is the super administrator of Linux.

Root can:

* Create users
* Delete users
* Install software
* Change permissions
* Access any file
* Stop any process

Check root information:

```bash
id root
```

Switch to root:

```bash
sudo -i
```

Verify:

```bash
whoami
```

Output:

```text
root
```

Exit root:

```bash
exit
```

---

# 3. What is a Group?

A **group** is a collection of users.

Example:

```text
Developers Group

├── Alice
├── Bob
└── Charlie
```

Instead of assigning permissions to each user, Linux can assign permissions to the entire group.

View your groups:

```bash
groups
```

or

```bash
id
```

---

# 4. Owner, Group and Others

Every file and directory belongs to:

```text
Owner
Group
Others
```

Example:

```bash
ls -l
```

Output:

```text
-rw-r--r-- 1 ubuntu ubuntu 0 Jul 11 test.txt
```

Meaning:

```text
Owner = ubuntu
Group = ubuntu
Others = Everyone else
```

---

## Real-World Example

Imagine a company document.

### Owner

Person who created the document.

```text
Nithin
```

### Group

Team members.

```text
Developers Team
```

### Others

Everyone else in the company.

```text
All remaining users
```

---

# 5. Understanding Linux Permissions

View permissions:

```bash
ls -l
```

Example:

```text
-rwxr-xr-x
```

Breakdown:

```text
-
rwx
r-x
r-x
```

Meaning:

```text
File Type
Owner
Group
Others
```

---

## Permission Symbols

| Symbol | Meaning |
| ------ | ------- |
| r      | Read    |
| w      | Write   |
| x      | Execute |

### Read (r)

Allows viewing contents.

```bash
cat file.txt
```

### Write (w)

Allows modifying contents.

```bash
nano file.txt
```

### Execute (x)

Allows running a file.

```bash
./script.sh
```

---

# 6. Numeric Permission Values

Linux uses numbers:

```text
Read = 4
Write = 2
Execute = 1
```

Add them together to form permissions. ([Linux Beginner][1])

---

# 7. Meaning of 755

Command:

```bash
chmod 755 file
```

Breakdown:

```text
7 = 4 + 2 + 1 = rwx
5 = 4 + 0 + 1 = r-x
5 = 4 + 0 + 1 = r-x
```

Result:

```text
Owner  → rwx
Group  → r-x
Others → r-x
```

Visual:

```text
rwxr-xr-x
```

Meaning:

* Owner can read, write, execute
* Group can read and execute
* Others can read and execute

Common use:

* Shell scripts
* Executables
* Directories ([Ubuntu][2])

---

# 8. Meaning of 700

Command:

```bash
chmod 700 file
```

Breakdown:

```text
7 = rwx
0 = ---
0 = ---
```

Result:

```text
rwx------
```

Meaning:

```text
Only Owner can access
Group cannot access
Others cannot access
```

Common use:

* Private directories
* SSH folders
* Sensitive scripts ([Ubuntu][2])

---

# 9. Meaning of 644

Command:

```bash
chmod 644 file
```

Breakdown:

```text
6 = rw-
4 = r--
4 = r--
```

Result:

```text
rw-r--r--
```

Meaning:

```text
Owner  → Read + Write
Group  → Read Only
Others → Read Only
```

Common use:

* Text files
* HTML files
* Configuration files ([Ubuntu][2])

---

# 10. Changing Permissions

### Numeric Method

```bash
chmod 755 script.sh
```

```bash
chmod 700 private.sh
```

```bash
chmod 644 config.txt
```

---

### Symbolic Method

Add execute:

```bash
chmod +x script.sh
```

Remove write:

```bash
chmod -w file.txt
```

Owner only:

```bash
chmod u+rwx file.txt
```

Group read:

```bash
chmod g+r file.txt
```

Others remove read:

```bash
chmod o-r file.txt
```

([Linuxize][3])

---

# 11. File Ownership

Check ownership:

```bash
ls -l
```

Change owner:

```bash
sudo chown developer file.txt
```

Change owner and group:

```bash
sudo chown developer:developer file.txt
```

Change group:

```bash
sudo chgrp developer file.txt
```

([Linux Beginner][1])

---

# 12. Interview Questions

### What is a User?

A user is an account that can log in and use the Linux system.

---

### What is Root User?

Root is the super administrator account with unrestricted access.

---

### What is a Group?

A group is a collection of users used for permission management.

---

### Difference Between Owner, Group and Others?

| Type   | Meaning         |
| ------ | --------------- |
| Owner  | Creator of file |
| Group  | Team of users   |
| Others | Everyone else   |

---

### Difference Between chmod and chown?

| Command | Purpose            |
| ------- | ------------------ |
| chmod   | Change permissions |
| chown   | Change ownership   |

---

### Meaning of 755?

```text
Owner  → Read Write Execute
Group  → Read Execute
Others → Read Execute
```

---

### Meaning of 700?

```text
Only Owner has access
```

---

### Meaning of 644?

```text
Owner → Read Write
Others → Read Only
```

---

# Senior Engineer Memory Trick ⭐

```text
755 → Public Script
700 → Private Script
644 → Normal File
600 → Secret File
```

Examples:

```bash
chmod 755 deploy.sh
chmod 700 backup.sh
chmod 644 notes.txt
chmod 600 private.key
```

.

# Linux Users, Groups & Permissions Documentation

## 1. What is a User?

A **user** is an account that can log in to a Linux system and perform tasks.

Every person or application accessing Linux operates as a user.

Examples:

```text
nithin
ubuntu
john
mysql
```

### Why do we need users?

* Security
* Access control
* Accountability
* Resource management

Example:

```bash
whoami
```

Output:

```text
ubuntu
```

This tells you which user is currently logged in.

---

# 2. What is a Root User?

The **root user** is the superuser of Linux.

Root has unlimited permissions and can:

* Create users
* Delete users
* Install software
* Modify system files
* Start/stop services
* Access all files

Example:

```bash
sudo su
```

or

```bash
sudo -i
```

Prompt changes from:

```text
ubuntu@server:~$
```

to

```text
root@server:~#
```

Notice:

```text
$ = Normal User
# = Root User
```

### Why be careful with root?

Root can accidentally damage the system.

Example:

```bash
rm -rf /
```

This can destroy the entire Linux filesystem.

Therefore:

```text
Use root only when necessary.
```

---

# 3. What is a Group?

A **group** is a collection of users.

Instead of giving permissions individually, permissions can be assigned to a group.

Example:

```text
Developers Group
├── Nithin
├── Rahul
└── Arjun
```

All members can share access to common files.

### Check groups

```bash
groups
```

Example output:

```text
ubuntu sudo docker
```

This means the user belongs to:

* ubuntu group
* sudo group
* docker group

---

# Why Groups are Important

Without groups:

```text
File → User1
File → User2
File → User3
```

Need to assign permissions repeatedly.

With groups:

```text
File → Developers Group
```

All members automatically receive access.

---

# 4. Owner, Group and Others

Every file and directory in Linux has:

```text
Owner
Group
Others
```

Example:

```bash
ls -l
```

Output:

```text
-rw-r--r-- 1 ubuntu ubuntu 100 Jul 11 file.txt
```

Let's break it down.

### Owner

The person who created the file.

Example:

```text
Nithin
```

Usually has the highest control.

---

### Group

Users belonging to the file's assigned group.

Example:

```text
Developers Group
```

All group members share specific permissions.

---

### Others

Everyone else on the system.

Example:

```text
Any user not owner and not in group
```

Usually given minimal permissions.

---

# Visual Representation

```text
                file.txt

                   │
      ┌────────────┼────────────┐
      │            │            │
   Owner        Group       Others
   Nithin    Developers     Everyone
```

---

# Linux Permission Types

Linux uses three permissions:

| Symbol | Meaning | Description        |
| ------ | ------- | ------------------ |
| r      | Read    | View file contents |
| w      | Write   | Modify file        |
| x      | Execute | Run file/program   |

---

## Permission Values

| Permission | Value |
| ---------- | ----- |
| r          | 4     |
| w          | 2     |
| x          | 1     |

---

# Understanding 755

```text
755
```

Break it:

```text
7 5 5
│ │ │
│ │ └── Others
│ └──── Group
└────── Owner
```

Calculate:

```text
7 = 4+2+1 = rwx
5 = 4+1 = r-x
5 = 4+1 = r-x
```

Result:

```text
Owner  → rwx
Group  → r-x
Others → r-x
```

Meaning:

* Owner can read, write and execute.
* Group can read and execute.
* Others can read and execute.

Common for:

```text
Directories
Web application folders
Scripts
```

Example:

```bash
chmod 755 myfolder
```

---

# Understanding 700

```text
700
```

Break it:

```text
7 0 0
```

Calculate:

```text
7 = rwx
0 = ---
0 = ---
```

Result:

```text
Owner  → rwx
Group  → ---
Others → ---
```

Meaning:

Only owner can access.

Common for:

```text
SSH Keys
Private Data
Sensitive Files
```

Example:

```bash
chmod 700 .ssh
```

---

# Understanding 644

```text
644
```

Break it:

```text
6 4 4
```

Calculate:

```text
6 = 4+2 = rw-
4 = r--
4 = r--
```

Result:

```text
Owner  → rw-
Group  → r--
Others → r--
```

Meaning:

* Owner can read and modify.
* Group can only read.
* Others can only read.

Common for:

```text
Text files
Configuration files
HTML files
```

Example:

```bash
chmod 644 file.txt
```

---

# Summary Table

| Permission | Owner | Group | Others | Usage                |
| ---------- | ----- | ----- | ------ | -------------------- |
| 755        | rwx   | r-x   | r-x    | Directories, scripts |
| 700        | rwx   | ---   | ---    | Private folders, SSH |
| 644        | rw-   | r--   | r--    | Files, configs       |

---

# Important Commands

### View permissions

```bash
ls -l
```

### Change permissions

```bash
chmod 755 file
chmod 700 folder
chmod 644 file.txt
```

### Change owner

```bash
sudo chown user file
```

### Change group

```bash
sudo chgrp developers file
```

### View current user

```bash
whoami
```

### View groups

```bash
groups
```

---

# Cloud Engineer Interview Question

**What does chmod 755 mean?**

**Answer:**

```text
Owner  → rwx (7)
Group  → r-x (5)
Others → r-x (5)
```

The owner has full control, while group members and others can only read and execute. It is commonly used for directories and executable scripts.
