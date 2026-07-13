

☁️ Day 8 Documentation – AWS Storage & Networking Fundamentals

Course: Cloud Engineering Roadmap

Module: AWS Core Services

Topic: Amazon S3, Amazon EBS, VPC Basics & Networking

Objective: Understand AWS storage services, networking components, and how a client request reaches an EC2 instance.


---

Learning Outcomes

After completing this lab, you should be able to:

Explain Amazon EBS and Amazon S3.

Differentiate Block Storage and Object Storage.

Create and manage an Amazon S3 bucket.

Understand VPC networking concepts.

Explain the function of Internet Gateway, Route Tables, and Subnets.

Differentiate Security Groups and Network ACLs.

Trace the path of an HTTP request to an EC2 instance.



---

Part 1 – Amazon EBS (Elastic Block Store)

Definition

Amazon EBS (Elastic Block Store) is a block storage service designed for use with Amazon EC2 instances.

An EBS volume behaves like a physical hard disk attached to a virtual server.


---

Features

Persistent storage

High availability within an Availability Zone

Low latency

Bootable storage for operating systems

Supports snapshots

Can be resized



---

Common Use Cases

Operating systems (Ubuntu, Amazon Linux, Windows)

Databases

Enterprise applications

File systems

Boot volumes



---

Root Volume

The Root Volume contains:

Operating System

Boot Loader

System Files

Installed Packages

User Configuration


Example:

Device Name : /dev/sda1
Volume Type : gp3
Size : 8 GiB


---

Volume Types

gp3 – General Purpose SSD (recommended)

gp2 – Previous generation SSD

io1/io2 – Provisioned IOPS SSD

st1 – Throughput Optimized HDD

sc1 – Cold HDD



---

Snapshots

An EBS Snapshot is a backup of an EBS volume stored in Amazon S3.

Benefits:

Disaster recovery

Data backup

Volume restoration

Create new EBS volumes



---

Part 2 – Amazon S3 (Simple Storage Service)

Definition

Amazon S3 is a highly durable, scalable object storage service used to store and retrieve data from anywhere.


---

S3 Terminology

Bucket

A logical container that stores objects.

Bucket names must be globally unique.


---

Object

Any file stored inside a bucket.

Examples:

Images

Videos

PDFs

ZIP files

Backups



---

Key

The unique identifier of an object inside a bucket.

Example:

photos/profile.jpg


---

Storage Classes

Standard

Intelligent-Tiering

Standard-IA

One Zone-IA

Glacier Instant Retrieval

Glacier Flexible Retrieval

Glacier Deep Archive



---

Features

99.999999999% (11 nines) durability

Unlimited storage capacity

High availability

Versioning

Lifecycle management

Encryption

Access control



---

Hands-on Lab Performed

Completed:

Created General Purpose Bucket

Uploaded Image

Downloaded Image

Deleted Object

Deleted Bucket



---

Best Practices

Enable Block Public Access

Use IAM permissions

Enable Versioning when required

Encrypt sensitive data

Delete unused buckets



---

Part 3 – Amazon EBS vs Amazon S3

Amazon EBS	Amazon S3

Block Storage	Object Storage
Attached to EC2	Independent Service
Stores Operating System	Stores Files and Objects
Low Latency	Highly Scalable
Bootable	Not Bootable
Single AZ	Multi-AZ design



---

Why Ubuntu Cannot Be Installed on S3

Ubuntu requires:

Block Storage

File System

Boot Device

Continuous Read/Write Access


Amazon EBS provides these capabilities.

Amazon S3 stores data as objects and cannot serve as a boot disk for an EC2 instance.


---

Part 4 – Amazon VPC

Definition

Amazon Virtual Private Cloud (VPC) is a logically isolated virtual network where AWS resources are deployed.

A VPC enables complete control over networking.


---

Components

CIDR Block

Subnets

Route Tables

Internet Gateway

NAT Gateway

Security Groups

Network ACLs



---

Public Subnet

A subnet that has access to the Internet through an Internet Gateway.

Typical resources:

EC2 Web Server

Bastion Host

Load Balancer



---

Private Subnet

A subnet without direct Internet access.

Typical resources:

Databases

Backend Servers

Internal Applications



---

Internet Gateway (IGW)

An Internet Gateway connects a VPC to the public Internet.

Without an IGW:

Public IPs cannot communicate with the Internet.



---

Route Table

A Route Table determines where network traffic is directed.

Example:

Destination	Target

10.0.0.0/16	Local
0.0.0.0/0	Internet Gateway



---

Part 5 – Security Groups

Definition

A Security Group is a stateful virtual firewall attached to an EC2 instance.

It controls:

Inbound Traffic

Outbound Traffic



---

Example Rules

SSH

Port 22

HTTP

Port 80

HTTPS

Port 443


---

Characteristics

Instance level

Stateful

Allow rules only



---

Part 6 – Network ACL

Network ACL (Access Control List) is a subnet-level firewall.

Characteristics:

Stateless

Allow Rules

Deny Rules

Evaluated in order



---

Security Group vs Network ACL

Security Group	Network ACL

Stateful	Stateless
Instance Level	Subnet Level
Allow Only	Allow & Deny
Easier to Manage	More Granular Control



---

Part 7 – Request Flow

When a user enters:

http://Public-IP

The request flows as follows:

Browser
↓
Internet
↓
AWS Edge Network
↓
Internet Gateway
↓
Route Table
↓
Public Subnet
↓
Security Group
↓
EC2 Instance
↓
Apache/Nginx
↓
Application
↓
Response Returned
↓
Browser


---

Part 8 – Best Practices

Storage

Use EBS for operating systems.

Use S3 for files and backups.

Take regular EBS snapshots.


Networking

Allow only required ports.

Restrict SSH access to trusted IPs.

Use private subnets for databases.

Keep Security Groups as restrictive as possible.



---

Interview Questions

1. What is Amazon EBS?


2. What is Amazon S3?


3. Difference between Block Storage and Object Storage?


4. Why is Ubuntu installed on EBS instead of S3?


5. What is a VPC?


6. Difference between Public and Private Subnets?


7. What is an Internet Gateway?


8. What is a Route Table?


9. Difference between Security Group and Network ACL?


10. Explain the journey of an HTTP request from your browser to an EC2 instance.




---

Commands/Actions Performed

Navigated to the EC2 console and identified the root EBS volume.

Verified volume size, type (gp3), and device name.

Created an Amazon S3 General Purpose bucket.

Uploaded an image object.

Downloaded the image successfully.

Deleted the object.

Deleted the S3 bucket.

Reviewed VPC, Route Tables, Security Groups, and Internet Gateway concepts.



