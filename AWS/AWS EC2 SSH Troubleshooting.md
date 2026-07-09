# AWS EC2 SSH Troubleshooting Runbook (Day 5)

---

## Step 1: Check Instance State

### Problem

SSH is not connecting.

### Verify

* EC2 Dashboard → Instance State

### Expected

```
Running
```

### If Stopped

```
Instance State
→ Start Instance
```

---

## Step 2: Verify Public IP

### Problem

Old IP doesn't work.

Every time you Stop → Start an EC2 instance, AWS assigns a new Public IPv4 address unless you use an Elastic IP.

### Verify

```
EC2
→ Public IPv4
```

Use the latest Public IPv4 address.

### Example

```
Old
3.108.xxx.xxx

New
3.110.xxx.xxx
```

Always use the newest Public IP.

---

## Step 3: Verify Security Group

Navigate to:

```
EC2
→ Security
→ Security Group
→ Inbound Rules
```

Ensure it contains:

```
SSH
Port 22
Source: My IP
```

Or temporarily:

```
0.0.0.0/0
```

for testing purposes.

---

## Step 4: Public IP Changed

### Symptoms

```
Connection timed out
```

### Reason

Your ISP may have assigned a new public IP address.

### Check

Search on Google:

```
What is my IP
```

Compare it with:

```
Security Group
→ Source
```

If they differ:

```
Edit Inbound Rule
→ My IP
→ Save
```

---

## Step 5: Verify PEM File

### Check Location

```bash
ls
```

Expected:

```
cloud-key.pem
```

If not found:

```bash
find ~ -name "*.pem"
```

---

## Step 6: Verify File Permission

Run:

```bash
chmod 400 cloud-key.pem
```

Verify:

```bash
ls -l cloud-key.pem
```

Expected:

```
-r--------
```

If you see:

```
Permissions 0555 are too open
```

Fix it with:

```bash
chmod 400 cloud-key.pem
```

---

## Step 7: Connect to EC2

### Command

```bash
ssh -i cloud-key.pem ubuntu@PUBLIC_IP
```

### Example

```bash
ssh -i cloud-key.pem ubuntu@3.110.175.212
```

---

## Step 8: Verify Username

### Ubuntu AMI

```
ubuntu
```

### Amazon Linux AMI

```
ec2-user
```

Using the wrong username results in:

```
Permission denied
```

---

## Step 9: Connection Timed Out

This means the SSH packet never reached the EC2 instance.

### Possible Reasons

* Wrong Security Group
* Wrong Public IP
* Instance Stopped
* Network issue

---

## Step 10: Permission Denied (publickey)

This means SSH successfully reached the EC2 instance, but authentication failed.

### Possible Reasons

* Wrong PEM key
* Wrong username
* Incorrect file permissions

---

## Step 11: Verify Internet Connectivity

Run:

```bash
ping PUBLIC_IP
```

If the ping succeeds, the network path exists.

---

## Step 12: Debug SSH Connection

Run:

```bash
ssh -vvv -i cloud-key.pem ubuntu@PUBLIC_IP
```

This provides detailed SSH debugging information.

---

## Step 13: Stop Instance

To avoid unnecessary charges:

```
EC2
→ Instance State
→ Stop Instance
```

Do not leave instances running when not in use.

---

# Linux Commands Used Today

### Current Directory

```bash
pwd
```

### List Files

```bash
ls
```

### Go to Home Directory

```bash
cd ~
```

### Secure PEM Key

```bash
chmod 400 cloud-key.pem
```

### Test Network

```bash
ping IP
```

### Login to Server

```bash
ssh -i cloud-key.pem ubuntu@IP
```

### Current User

```bash
whoami
```

### Create File

```bash
touch test.txt
```

### View File Permissions

```bash
ls -l
```

---

# Errors We Solved Today

## Error 1: No such file or directory

### Reason

Wrong directory.

### Solution

```bash
pwd
ls
```

Locate the correct folder.

---

## Error 2: Permission denied

### Reason

Wrong PEM key, username, or permissions.

### Solution

Verify:

* PEM key
* Username
* File permissions (`chmod 400`)

---

## Error 3: Permissions 0555 are too open

### Solution

```bash
chmod 400 cloud-key.pem
```

---

## Error 4: Connection timed out

### Reason

Security Group blocked SSH because your public IP changed.

### Solution

Update the SSH source rule to:

```
My IP
```

---

## Error 5: Wrong Public IP

### Reason

Instance was stopped and started.

### Solution

Copy the latest Public IPv4 address from EC2.

---

# Cloud Concepts Learned Today

* EC2 Instance
* AMI (Amazon Machine Image)
* Public IPv4
* Private IPv4
* Security Groups
* Inbound Rules
* Port 22 (SSH)
* Port 80 (HTTP)
* PEM Key Pair
* Public Key Authentication
* Linux Terminal
* WSL (Windows Subsystem for Linux)
* Public DNS
* Default VPC
* SSH Protocol

---

# Chinni's Golden Rules ⭐

1. Always check whether the instance is running.
2. Always use the latest Public IPv4 address.
3. Always verify Security Group inbound rules for Port 22.
4. Always run `chmod 400` on the PEM file before connecting.
5. Always use the correct username (`ubuntu` for Ubuntu AMIs).
6. Read the complete error message before attempting fixes.
7. Change only one thing at a time and test again. This is the foundation of professional troubleshooting.
8. Stop EC2 instances when finished to avoid unnecessary charges.
