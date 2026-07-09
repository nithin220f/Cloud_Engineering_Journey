Day 6 - Linux File System & Basic Administration
Objective

Learn how to:

Navigate directories
Create, copy, move, and delete files
View file contents
Check system information
Understand file permissions
Step 1: Connect to AWS EC2
Start the instance

AWS Console → EC2 → Select Instance → Start

Wait until:

2/2 Status Checks Passed
Connect using SSH
cd ~
chmod 400 cloud-key.pem
ssh -i cloud-key.pem ubuntu@YOUR_PUBLIC_IP
Step 2: Verify Connection
pwd
whoami
hostname

Purpose:

pwd → Current directory
whoami → Logged-in user
hostname → Server name
Step 3: Navigate Directories

Current directory

pwd

List files

ls

Detailed listing

ls -la

Go to root

cd /

Go to home

cd ~
Step 4: Create Directories
mkdir CloudEngineering
cd CloudEngineering

Create subdirectories

mkdir Projects
mkdir Notes
mkdir Practice
Step 5: View Directory Structure

If Tree isn't installed

sudo apt update
sudo apt install tree -y

View structure

tree
Step 6: Create Files
touch day6.txt
touch notes.txt
touch linux.txt

Verify

ls
Step 7: Write into Files

Overwrite

echo "Hello Cloud" > day6.txt

Append

echo "Learning AWS" >> day6.txt

View

cat day6.txt
Step 8: Edit File
nano notes.txt

Save

Ctrl + O
Enter

Exit

Ctrl + X
Step 9: Copy File
cp notes.txt backup.txt

Verify

ls
Step 10: Rename File
mv backup.txt backup_notes.txt
Step 11: Delete File
rm delete_me.txt

Delete directory

rm -r temp
Step 12: Search Files

Search all text files

find . -name "*.txt"

Search one file

find . -name "notes.txt"
Step 13: File Permissions

View permissions

ls -l

Change permissions

chmod 644 notes.txt

Verify

ls -l
Step 14: Disk Usage
df -h

Current directory size

du -sh .
Step 15: Memory Usage
free -h
Step 16: CPU Information
lscpu
Step 17: Operating System
cat /etc/os-release
Step 18: Network Information

IP Address

hostname -I

Network interfaces

ip addr

Routing table

ip route
Step 19: Process Management

Running processes

ps

All processes

ps aux

Live monitoring

top

Exit

q
Troubleshooting Guide
Error 1
Permission denied

Reason:

No permission to access file or directory.

Solution:

ls -l
sudo command
Error 2
No such file or directory

Reason:

Wrong path.

Solution

pwd
ls

Navigate correctly.

Error 3
tree: command not found

Solution

sudo apt update
sudo apt install tree -y
Error 4
nano: command not found

Solution

sudo apt install nano -y
Error 5
Operation not permitted

Reason:

Insufficient privileges.

Solution

sudo command
Commands Learned
Command	Purpose
pwd	Show current directory
ls	List files
ls -la	Detailed file listing
cd	Change directory
mkdir	Create directory
touch	Create file
echo	Write text into file
cat	View file contents
nano	Edit files
cp	Copy files
mv	Move/Rename files
rm	Delete files
find	Search files
chmod	Change permissions
df -h	Disk usage
du -sh	Folder size
free -h	Memory usage
lscpu	CPU details
hostname -I	IP address
ip addr	Network interfaces
ip route	Routing table
ps	Running processes
top	Live process monitor
Key Concepts Learned
Linux File System
Root (/) vs Home (~)
Files and Directories
Absolute vs Relative Paths
File Permissions
Linux Processes
CPU Information
Memory Monitoring
Disk Monitoring
Network Information
