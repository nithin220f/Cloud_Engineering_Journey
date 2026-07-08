

☁️ Day 5 - AWS EC2 Master Notes

1. What is EC2?

EC2 (Elastic Compute Cloud) is a virtual computer (virtual machine) provided by AWS.

Instead of buying a physical server, AWS lets you rent one on demand.

Example:

Physical Computer → Your Laptop

Virtual Computer → EC2 Instance



---

2. What is an AMI?

AMI (Amazon Machine Image) is a template used to launch an EC2 instance.

It contains:

Operating System (Ubuntu, Amazon Linux, Windows)

Default software

Configuration


Think of it as an OS installation image.


---

3. Instance Type

Instance type defines the server's hardware.

It specifies:

CPU

RAM

Network performance


Examples:

t2.micro

t3.micro

t3.large


For learning:

✅ t2.micro (Free Tier)

✅ t3.micro (depending on account)



---

4. Key Pair

A Key Pair consists of:

Public Key (stored by AWS)

Private Key (.pem file stored by you)


Purpose:

Secure SSH authentication.


Never share your .pem file.


---

5. Security Group

Think of a Security Group as a virtual firewall.

Rules we created:

SSH

Port: 22

Source: My IP


HTTP

Port: 80

Source: Anywhere



---

6. Public IP vs Private IP

Public IP

Used from Internet.

Example:

Laptop
     ↓
Internet
     ↓
54.xxx.xxx.xxx

Private IP

Used inside AWS network.

Example:

EC2 A
   ↓
172.xxx.xxx.xxx
   ↓
EC2 B


---

7. SSH

SSH = Secure Shell

Purpose:

Remote login

Secure communication

Remote server management


Default Port:

22


---

8. Why chmod 400?

SSH refuses to use a key that everyone can read.

chmod 400 cloud-key.pem

Meaning:

Owner:

Read ✔

Group:

No permission

Others:

No permission

Security reason: Only the owner should access the private key.


---

9. Stop vs Reboot vs Terminate

Stop

Server shuts down.

Can start again.

Public IP usually changes.


Reboot

Restart.

Public IP usually stays the same.


Terminate

Deletes the server permanently.



---

10. Why Public IP disappeared?

Because AWS releases temporary public IPs when an instance is stopped.

To keep the same IP:

Use Elastic IP.



---

Commands You Used

Navigation

pwd

Current directory

ls

List files

cd

Change directory


---

Permissions

chmod 400 cloud-key.pem

Secure the key

ls -l

View permissions


---

Copy

cp

Copy files


---

SSH

ssh -i cloud-key.pem ubuntu@PUBLIC_IP

Connect to EC2


---

Information

whoami
hostname
pwd
free -h
df -h
uptime


---

Troubleshooting Flow

Problem 1

No such directory

Solution:

pwd
ls


---

Problem 2

Permission denied (publickey)

Check:

✔ Correct username

Ubuntu → ubuntu

✔ Correct key pair

✔ Correct Public IP

✔ chmod 400

✔ Key filename


---

Problem 3

Permissions 0555 are too open

Solution:

chmod 400 cloud-key.pem


---

Problem 4

cd: too many arguments

Reason:

Used multiple paths in one command.

Correct:

cd Downloads

Not

cd Downloads folder file


---

Problem 5

No such file or directory

Check:

pwd
ls
find

Never guess the path.


---

Debugging Strategy (Remember This Forever)

When a command fails:

1. Read the error.

Don't panic.

2. Verify location

pwd

3. Verify files

ls

4. Verify permissions

ls -l

5. Verify configuration

Ask:

Correct username?

Correct key?

Correct IP?

Correct folder?


6. Change only ONE thing at a time.

Don't change five things together.


---

Common Interview Questions

1. What is EC2?


2. Difference between Public IP and Private IP.


3. Why SSH uses Port 22?


4. Why do we use .pem files?


5. What is an AMI?


6. Difference between Security Group and NACL (we'll cover NACL later).


7. Difference between Stop, Reboot, and Terminate.


8. Why did the Public IP change after stopping the instance?


9. What happens if port 22 is blocked?


10. Why is SSH restricted to "My IP" while HTTP is open to "Anywhere"?




