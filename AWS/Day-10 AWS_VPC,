📘 Day 10 Documentation – Part 1

Amazon VPC Fundamentals

AWS Cloud Practitioner (CLF-C02) Style Notes


---

Module Overview

Amazon Virtual Private Cloud (Amazon VPC) is one of the most important networking services in AWS. Every AWS architect, cloud engineer, and system administrator must understand VPC because almost all AWS resources operate within a network environment.

Amazon VPC provides complete control over networking, routing, connectivity, and security.


---

Learning Objectives

After completing this chapter, you will be able to:

Explain Amazon VPC.

Understand the purpose of VPC.

Differentiate Default VPC and Custom VPC.

Understand VPC components.

Explain how AWS networking works.

Describe benefits of VPC.



---

What is Amazon VPC?

Definition

Amazon Virtual Private Cloud (Amazon VPC) is a logically isolated virtual network within AWS where you can launch and manage AWS resources.

A VPC allows you to define:

IP address ranges

Subnets

Route tables

Gateways

Security controls


while maintaining isolation from other AWS customers.


---

Simple Explanation

Think of Amazon VPC as your own private data center inside AWS.

In a physical company:

Company Building
    ↓
Network
    ↓
Servers
    ↓
Applications

In AWS:

Amazon VPC
    ↓
Subnets
    ↓
EC2 Instances
    ↓
Applications

The VPC acts as the network boundary.


---

Why Do We Need Amazon VPC?

Without a VPC:

No network isolation

No control over IP addresses

No routing control

No subnet separation

No network security architecture


Amazon VPC enables organizations to create secure and scalable cloud networks.


---

Benefits of Amazon VPC

1. Isolation

Every VPC is logically isolated from other AWS customers.

This provides:

Security

Privacy

Network control



---

2. Custom Networking

You can define:

Private IP ranges

Subnets

Route tables

Security policies


according to organizational requirements.


---

3. Scalability

Resources can be added or removed dynamically without redesigning the network.


---

4. Security

VPC integrates with:

Security Groups

Network ACLs

IAM Policies


to provide layered security.


---

5. Hybrid Connectivity

Organizations can connect their on-premises data centers to AWS through:

AWS Site-to-Site VPN

AWS Direct Connect


creating hybrid cloud environments.


---

VPC Components

A VPC contains multiple networking components.

Amazon VPC
│
├── CIDR Block
├── Subnets
├── Route Tables
├── Internet Gateway
├── NAT Gateway
├── Security Groups
├── Network ACLs
├── Elastic IP
└── EC2 Instances

Each component performs a specific networking function.


---

Default VPC

Definition

When an AWS account is created, AWS automatically provides a Default VPC in every AWS Region.

The Default VPC allows users to launch resources immediately without manually configuring networking.


---

Characteristics

Default VPC includes:

CIDR block

Public subnets

Route table

Internet Gateway

Security Group



---

Advantages

Ready to use

Beginner friendly

No manual setup required



---

Limitation

Large organizations rarely use Default VPCs because they need custom networking architectures.


---

Custom VPC

Definition

A Custom VPC is a VPC created and configured by the customer.

Organizations design custom VPCs according to business and security requirements.


---

Why Use Custom VPC?

Organizations require:

Multiple subnets

Public and private separation

Network segmentation

Compliance requirements

Hybrid connectivity


Custom VPCs provide this flexibility.


---

Default VPC vs Custom VPC

Feature	Default VPC	Custom VPC

Created by AWS	Yes	No
Ready to use	Yes	No
Beginner Friendly	Yes	Moderate
Full Network Control	Limited	Complete
Enterprise Usage	Rare	Common



---

Regional Nature of VPC

Amazon VPC is a Regional Service.

Example:

Mumbai Region
      ↓
VPC-A

Ohio Region
      ↓
VPC-B

Each region maintains separate VPC resources.


---

High Availability and VPC

A VPC can span multiple Availability Zones.

Example:

VPC
│
├── Subnet A (AZ-1)
│
└── Subnet B (AZ-2)

Benefits:

High availability

Fault tolerance

Disaster recovery



---

Shared Responsibility Model and VPC

AWS Responsibility:

Physical network infrastructure

Data centers

Hardware

Availability


Customer Responsibility:

Subnets

Route tables

Security Groups

Network ACLs

Resource configuration


This follows the AWS Shared Responsibility Model.


---

Real-World Example

Suppose a company hosts an online shopping application.

Architecture:

Amazon VPC
│
├── Public Subnet
│     └── Web Server
│
└── Private Subnet
      └── Database Server

Advantages:

Customers access the website.

Database remains protected.

Security improves significantly.



---

AWS Best Practices

AWS recommends:

✅ Use custom VPCs for production environments

✅ Separate public and private resources

✅ Apply least privilege access

✅ Use multiple Availability Zones

✅ Restrict network access whenever possible


---

Interview Questions

1. What is Amazon VPC?

Amazon VPC is a logically isolated virtual network within AWS where customers launch and manage AWS resources.


---

2. Why is Amazon VPC important?

It provides network isolation, security, routing control, and custom networking capabilities.


---

3. What is the difference between a Default VPC and a Custom VPC?

Default VPC is automatically created by AWS and ready to use, whereas a Custom VPC is created and configured by the customer according to specific requirements.


---

4. Is Amazon VPC a Regional Service?

Yes. A VPC exists within a specific AWS Region.


---

5. Can a VPC span multiple Availability Zones?

Yes. A VPC can contain subnets across multiple Availability Zones.

Awesome! 🚀 Let's continue with your AWS Cloud Practitioner (CLF-C02) notes.


---

📘 Day 10 Documentation – Part 2

CIDR Blocks, IP Addressing & Subnets

AWS Cloud Practitioner (CLF-C02) Style Notes


---

Learning Objectives

After completing this chapter, you will be able to:

Explain IPv4 addressing.

Understand CIDR notation.

Differentiate public and private IPv4 addresses.

Explain subnetting in Amazon VPC.

Understand Availability Zones and subnet placement.

Explain how AWS assigns IP addresses to EC2 instances.



---

Chapter 1 – IP Addressing

Definition

An IP (Internet Protocol) address is a unique numerical identifier assigned to a device connected to a network. It enables devices to communicate with one another by identifying the source and destination of network traffic.

AWS primarily uses IPv4 and also supports IPv6.


---

IPv4 Address

An IPv4 address consists of 32 bits divided into four octets separated by periods.

Example:

192.168.1.10

Each octet ranges from 0 to 255.

Examples:

10.0.0.15
172.31.20.45
192.168.100.5


---

Types of IPv4 Addresses

Public IPv4 Address

A public IP address is globally unique and reachable from the Internet.

Characteristics:

Assigned by AWS (unless using Elastic IP).

Internet accessible.

Used by web servers and public-facing applications.

Can change when an EC2 instance is stopped and started (unless an Elastic IP is attached).


Example:

54.210.120.45


---

Private IPv4 Address

A private IP address is used for communication within a VPC.

It is not directly reachable from the public Internet.

Private IP addresses remain associated with the EC2 instance during its lifetime.

Examples:

10.0.1.15
172.31.5.20
192.168.1.50


---

Private IPv4 Address Ranges

According to RFC 1918, the private address ranges are:

Range	CIDR

10.0.0.0 – 10.255.255.255	10.0.0.0/8
172.16.0.0 – 172.31.255.255	172.16.0.0/12
192.168.0.0 – 192.168.255.255	192.168.0.0/16


AWS commonly uses these ranges when creating VPCs.


---

Chapter 2 – CIDR (Classless Inter-Domain Routing)

Definition

CIDR (Classless Inter-Domain Routing) is a method used to allocate IP addresses and define the size of an IP network.

CIDR notation consists of an IP address followed by a slash (/) and a number.

Example:

10.0.0.0/16


---

Understanding CIDR

Example:

10.0.0.0/16

10.0.0.0 = Network address

/16 = Prefix length


A /16 network provides 65,536 IP addresses (including reserved addresses).


---

Common CIDR Blocks

CIDR	Total IP Addresses

/16	65,536
/24	256
/28	16
/32	1



---

CIDR in Amazon VPC

When creating a VPC, you specify a CIDR block.

Example:

VPC CIDR

10.0.0.0/16

This defines the IP address range available within the VPC.


---

Chapter 3 – Subnets

Definition

A subnet is a range of IP addresses within a VPC.

Subnets allow you to organize and isolate AWS resources.

Each subnet exists in one Availability Zone.


---

Why Do We Need Subnets?

Subnets help:

Separate workloads.

Improve security.

Organize applications.

Support high availability.

Control network routing.



---

Public Subnet

Definition

A public subnet is a subnet that has a route to an Internet Gateway.

Resources in a public subnet can communicate with the Internet (subject to security rules).

Typical resources:

Web servers

Bastion hosts

Load balancers



---

Private Subnet

Definition

A private subnet does not have a direct route to an Internet Gateway.

Resources in a private subnet are not directly accessible from the Internet.

Typical resources:

Databases

Backend services

Internal applications



---

Public vs Private Subnet

Public Subnet	Private Subnet

Internet accessible	No direct Internet access
Hosts web servers	Hosts databases and backend services
Route to Internet Gateway	No direct route to Internet Gateway



---

Availability Zones and Subnets

Each subnet belongs to only one Availability Zone.

Example:

VPC (10.0.0.0/16)

├── Public Subnet (10.0.1.0/24) → AZ-a
├── Private Subnet (10.0.2.0/24) → AZ-a
├── Public Subnet (10.0.3.0/24) → AZ-b
└── Private Subnet (10.0.4.0/24) → AZ-b

Using multiple Availability Zones improves fault tolerance and availability.


---

AWS Reserved IP Addresses

AWS reserves the first 4 IP addresses and the last 1 IP address in every subnet.

For example, in a /24 subnet:

10.0.1.0/24

Reserved:

10.0.1.0

10.0.1.1

10.0.1.2

10.0.1.3

10.0.1.255


These addresses cannot be assigned to EC2 instances.


---

IP Assignment to EC2

When you launch an EC2 instance into a subnet:

AWS assigns a private IPv4 address from the subnet.

If enabled, AWS also assigns a public IPv4 address (for public subnets).


The private IP remains with the instance, while the public IP may change after the instance is stopped and started (unless using an Elastic IP).


---

Best Practices

AWS recommends:

Choose CIDR blocks carefully to allow future growth.

Use private subnets for databases.

Use public subnets only for Internet-facing resources.

Deploy resources across multiple Availability Zones for high availability.

Avoid overlapping CIDR ranges when connecting multiple VPCs.



---

Interview Questions

1. What is an IPv4 address?

An IPv4 address is a 32-bit numerical identifier used to identify devices on a network.


---

2. What is CIDR?

CIDR (Classless Inter-Domain Routing) is a method for defining IP address ranges using prefix notation, such as 10.0.0.0/16.


---

3. What is the difference between a public and a private IP address?

A public IP address is reachable from the Internet, while a private IP address is used only within a private network or VPC.


---

4. What is a subnet?

A subnet is a range of IP addresses within a VPC that allows you to organize and isolate AWS resources.


---

5. Can a subnet span multiple Availability Zones?

No. A subnet exists within a single Availability Zone.


---

6. Why are databases typically placed in private subnets?

Because they should not be directly accessible from the Internet, which improves security.


Excellent, fellow! Let's continue.


---

📘 Day 10 Documentation – Part 3

Internet Gateway, Route Tables & NAT Gateway

AWS Cloud Practitioner (CLF-C02) Style Notes


---

Learning Objectives

After completing this chapter, you will be able to:

Explain an Internet Gateway (IGW).

Understand Route Tables and routing decisions.

Explain the purpose of a NAT Gateway.

Describe how traffic flows between a VPC and the Internet.

Differentiate Internet Gateway and NAT Gateway.



---

Chapter 1 – Internet Gateway (IGW)

Definition

An Internet Gateway (IGW) is a horizontally scaled, redundant, and highly available VPC component that enables communication between resources in a VPC and the internet.

An Internet Gateway supports:

Internet communication

IPv4 traffic

IPv6 traffic

Network Address Translation (NAT) for instances with public IPv4 addresses



---

Why Do We Need an Internet Gateway?

Suppose you launch an EC2 instance with a public IP address.

Without an Internet Gateway:

Users on the internet cannot access the instance.

The instance cannot send traffic to the internet.


The Internet Gateway provides the connection between your VPC and the public internet.


---

Internet Gateway Characteristics

Regional resource

Attached to only one VPC at a time

Highly available

Managed by AWS

No additional configuration required after attachment



---

Internet Gateway Traffic Flow

User Browser
      │
Internet
      │
Internet Gateway
      │
Route Table
      │
Public Subnet
      │
EC2 Instance


---

Steps for Internet Access

For an EC2 instance to access the internet, all of the following are required:

✔ Internet Gateway attached to the VPC

✔ Route Table contains:

Destination : 0.0.0.0/0
Target      : Internet Gateway

✔ EC2 has a Public IPv4 Address (or Elastic IP)

✔ Security Group allows the required traffic

If any one of these is missing, internet connectivity will fail.


---

Chapter 2 – Route Tables

Definition

A Route Table contains a set of rules, called routes, that determine where network traffic from your subnet or gateway is directed.

Each subnet in a VPC must be associated with a route table.


---

Types of Routes

Local Route

Automatically created by AWS.

Example:

Destination : 10.0.0.0/16

Target : Local

Purpose:

Allows communication between resources within the same VPC.


---

Default Route

Example:

Destination : 0.0.0.0/0

Target : Internet Gateway

Meaning:

Traffic destined for any network outside the VPC is sent to the Internet Gateway.


---

Route Table Example

Destination	Target

10.0.0.0/16	Local
0.0.0.0/0	Internet Gateway



---

How Routing Works

Suppose an EC2 instance wants to reach:

www.amazon.com

The Route Table checks:

Is the destination inside the VPC?

No.

↓

Send traffic to:

Internet Gateway


---

Route Table Association

Every subnet is associated with exactly one Route Table.

Example:

Public Subnet

↓

Public Route Table

↓

Internet Gateway

Private subnets usually use different route tables.


---

Chapter 3 – NAT Gateway

Definition

A NAT (Network Address Translation) Gateway enables instances in a private subnet to connect to the internet or other AWS services while preventing the internet from initiating connections to those instances.


---

Why NAT Gateway?

Suppose a database server is inside a private subnet.

The database needs to:

Download security updates.

Install software packages.

Access AWS services.


But we do not want users on the internet to connect directly to the database.

The NAT Gateway solves this problem.


---

NAT Gateway Traffic Flow

Private EC2
      │
Private Subnet
      │
Route Table
      │
NAT Gateway
      │
Internet Gateway
      │
Internet


---

NAT Gateway Characteristics

Managed AWS service

Highly available within an Availability Zone

Requires an Elastic IP address

Placed in a public subnet

Used by resources in private subnets



---

Internet Gateway vs NAT Gateway

Internet Gateway	NAT Gateway

Connects a VPC to the internet	Allows private subnet resources to access the internet
Used by public subnets	Used by private subnets
Supports inbound and outbound traffic	Supports outbound traffic only
Does not require an Elastic IP	Requires an Elastic IP



---

Real-World Architecture

Internet
      │
Internet Gateway
      │
Public Subnet
      │
NAT Gateway
      │
Private Subnet
      │
Database Server

The database server can download updates, but no one on the internet can directly connect to it.


---

Best Practices

AWS recommends:

Use Internet Gateways only for internet-facing resources.

Place databases in private subnets.

Use NAT Gateways for outbound internet access from private subnets.

Associate the correct Route Table with each subnet.

Keep routing simple and well documented.



---

Interview Questions

1. What is an Internet Gateway?

An Internet Gateway is a VPC component that enables communication between a VPC and the internet.


---

2. What is a Route Table?

A Route Table contains rules that determine where network traffic is directed.


---

3. Why is a Route Table important?

It controls how traffic moves within the VPC and to external networks.


---

4. What is a NAT Gateway?

A NAT Gateway allows instances in private subnets to access the internet without allowing inbound internet connections.


---

5. Can a private subnet access the internet directly?

No. It requires a NAT Gateway (or another NAT solution) for outbound internet access.


---

6. What are the requirements for a public EC2 instance to access the internet?

Internet Gateway attached to the VPC.

Route Table with a default route (0.0.0.0/0) to the Internet Gateway.

Public IP address (or Elastic IP).

Security Group allowing the required traffic.


Excellent! You're building a solid AWS networking foundation. Let's continue.


---

📘 Day 10 Documentation – Part 4

Elastic IP, Security Groups & Network ACLs

AWS Certified Cloud Practitioner (CLF-C02) Style Notes


---

Learning Objectives

After completing this chapter, you will be able to:

Explain Elastic IP addresses.

Understand why Elastic IPs are used.

Explain Security Groups.

Configure inbound and outbound rules.

Explain Network ACLs.

Differentiate Security Groups and Network ACLs.

Understand AWS's layered network security model.



---

Chapter 1 – Elastic IP Address (EIP)

Definition

An Elastic IP address (EIP) is a static public IPv4 address designed for dynamic cloud computing.

Unlike an automatically assigned public IPv4 address, an Elastic IP remains associated with your AWS account until you release it.


---

Why Do We Need an Elastic IP?

Normally, an EC2 instance receives a public IPv4 address.

If the instance is stopped and started:

The public IPv4 address may change.


This can cause problems if users or applications depend on a fixed IP address.

An Elastic IP solves this by providing a static public IP.


---

Characteristics of Elastic IP

Static public IPv4 address.

Associated with your AWS account.

Can be remapped to another EC2 instance.

Regional resource.

One Elastic IP can be associated with one resource at a time.



---

Use Cases

Web servers

Bastion hosts

Firewalls

DNS records requiring a fixed IP

Disaster recovery



---

Public IP vs Elastic IP

Public IPv4 Address	Elastic IP

Assigned automatically	Allocated manually
May change after stop/start	Remains the same
Temporary	Static
No manual management	Managed by the customer



---

Best Practices

AWS recommends:

Allocate Elastic IPs only when needed.

Release unused Elastic IPs.

Use DNS names whenever possible instead of depending on IP addresses.



---

Chapter 2 – Security Groups

Definition

A Security Group is a virtual firewall that controls inbound and outbound traffic for AWS resources such as EC2 instances.

Security Groups operate at the instance level.


---

Purpose

Security Groups protect EC2 instances by allowing only authorized network traffic.

Example:

A web server should allow:

HTTP (80)

HTTPS (443)


An administrator should allow:

SSH (22)


All other unwanted traffic should remain blocked.


---

Characteristics

Stateful firewall

Instance level

Supports Allow rules only

Default deny for inbound traffic

Default allow for outbound traffic



---

Inbound Rules

Inbound rules control traffic entering the EC2 instance.

Example:

Type	Protocol	Port	Source

SSH	TCP	22	Your Public IP
HTTP	TCP	80	0.0.0.0/0
HTTPS	TCP	443	0.0.0.0/0



---

Outbound Rules

Outbound rules control traffic leaving the EC2 instance.

By default:

All outbound traffic is allowed.

Example:

Destination	Protocol

0.0.0.0/0	All



---

Stateful Firewall

Security Groups are stateful.

This means:

If inbound traffic is allowed,

↓

The response traffic is automatically allowed.

No separate outbound rule is required for the response.


---

Example

Laptop
   │
SSH (22)
   │
Security Group
   │
EC2 Instance

SSH is allowed because the inbound rule permits it.

The return traffic is automatically allowed because the Security Group is stateful.


---

Security Group Best Practices

AWS recommends:

Allow only required ports.

Restrict SSH to trusted IP addresses.

Avoid allowing all ports.

Use separate Security Groups for different application tiers.

Review rules regularly.



---

Chapter 3 – Network ACL (NACL)

Definition

A Network Access Control List (Network ACL) is an optional layer of security for your VPC that acts as a firewall for controlling traffic into and out of one or more subnets.

Network ACLs operate at the subnet level.


---

Characteristics

Stateless firewall.

Subnet level.

Supports Allow and Deny rules.

Rules evaluated in numerical order.

Separate inbound and outbound rules.



---

Rule Evaluation

Example:

Rule Number	Action

100	Allow SSH
200	Deny All


AWS evaluates rules starting from the lowest rule number.

The first matching rule is applied.


---

Stateless Firewall

Unlike Security Groups,

Network ACLs are stateless.

This means:

If inbound traffic is allowed,

↓

You must also explicitly allow the outbound response.


---

Default Network ACL

The default Network ACL:

Allows all inbound traffic.

Allows all outbound traffic.



---

Custom Network ACL

A custom Network ACL starts with no rules.

You must configure:

Inbound rules.

Outbound rules.



---

Security Group vs Network ACL

Security Group	Network ACL

Instance level	Subnet level
Stateful	Stateless
Allow rules only	Allow and Deny rules
Evaluates all rules	Evaluates rules in number order
Easier to manage	Provides additional network control



---

Layered Security Model

AWS recommends multiple security layers.

Internet
      │
Internet Gateway
      │
Network ACL
      │
Subnet
      │
Security Group
      │
EC2 Instance

Even if unwanted traffic reaches the subnet,

↓

The Security Group still protects the EC2 instance.

This approach is known as defense in depth.


---

Real-World Example

Imagine an e-commerce application.

Public Subnet:

Load Balancer

Web Server


Private Subnet:

Application Server

Database


Security:

Network ACL protects the subnet.

Security Group protects each EC2 instance.



---

AWS Best Practices

AWS recommends:

Use Security Groups as the primary firewall.

Use Network ACLs for additional subnet-level security.

Follow the Principle of Least Privilege.

Restrict SSH access to trusted IP addresses.

Review security rules regularly.



---

Interview Questions

1. What is an Elastic IP?

An Elastic IP is a static public IPv4 address that remains associated with your AWS account until released.


---

2. Why use an Elastic IP?

To provide a fixed public IP address that does not change when an EC2 instance is stopped and started.


---

3. What is a Security Group?

A Security Group is a stateful virtual firewall that controls inbound and outbound traffic for EC2 instances.


---

4. What is a Network ACL?

A Network ACL is a stateless firewall that controls traffic entering and leaving subnets.


---

5. What is the difference between a stateful and a stateless firewall?

A stateful firewall automatically allows return traffic for an allowed request.

A stateless firewall requires separate rules for inbound and outbound traffic.


---

6. Which is more commonly used, Security Groups or Network ACLs?

Security Groups are the primary security mechanism for EC2 instances, while Network ACLs provide an additional layer of protection at the subnet level.


Excellent, fellow! 🔥 You've now reached the final and most important part of Day 10. This is where all the networking concepts come together.


---

📘 Day 10 Documentation – Part 5

End-to-End VPC Architecture, Packet Flow, Best Practices & Interview Guide

AWS Certified Cloud Practitioner (CLF-C02) Style Notes


---

Learning Objectives

After completing this chapter, you will be able to:

Explain how network traffic flows inside an Amazon VPC.

Design a secure three-tier application architecture.

Apply AWS networking best practices.

Troubleshoot common VPC networking issues.

Answer Cloud Practitioner networking interview questions confidently.



---

Chapter 1 – End-to-End Packet Flow

One of the most important networking concepts is understanding how a user request travels through AWS.

Suppose a user opens a browser and enters:

http://54.xx.xx.xx

The request travels through the following components.

User
 │
Browser
 │
Internet
 │
Internet Gateway (IGW)
 │
Route Table
 │
Public Subnet
 │
Security Group
 │
EC2 Instance
 │
Web Server (Apache/Nginx)
 │
Application
 │
Response
 │
Browser


---

Step-by-Step Traffic Flow

Step 1 – User Request

The user enters the public IP or domain name in the browser.

Example:

http://54.210.120.25

The browser creates an HTTP request.


---

Step 2 – Internet

The request travels across the public Internet toward AWS.


---

Step 3 – Internet Gateway

The Internet Gateway receives the request and forwards it into the VPC.

Without an Internet Gateway:

Internet communication is impossible.



---

Step 4 – Route Table

The Route Table checks where the packet should go.

Example:

Destination	Target

10.0.0.0/16	Local
0.0.0.0/0	Internet Gateway


The request is forwarded to the correct subnet.


---

Step 5 – Public Subnet

The packet reaches the public subnet where the EC2 instance is located.


---

Step 6 – Security Group

The Security Group examines the incoming traffic.

Example:

Port	Status

22	Allow
80	Allow
443	Allow


If the requested port is allowed,

↓

Traffic proceeds.

Otherwise,

↓

Traffic is dropped.


---

Step 7 – EC2 Instance

The operating system receives the request.

Example:

Ubuntu

↓

Apache

↓

HTML Page

↓

Response


---

Step 8 – Response

The web server generates a response.

Because Security Groups are stateful,

Return traffic is automatically permitted.

The response reaches the user's browser.


---

Chapter 2 – Three-Tier Architecture

AWS recommends separating applications into multiple tiers.

Web Tier

Located in:

Public Subnet

Contains:

Load Balancer

Web Server


Purpose:

Receive requests from users.


---

Application Tier

Located in:

Private Subnet

Contains:

Application Server

APIs

Business Logic


Purpose:

Process application requests.


---

Database Tier

Located in:

Private Subnet

Contains:

Amazon RDS

MySQL

PostgreSQL


Purpose:

Store application data securely.


---

Three-Tier Architecture Diagram

Internet
                       │
               Internet Gateway
                       │
          ┌─────────────────────────┐
          │        Amazon VPC       │
          └─────────────────────────┘
                 │
         Public Subnet
                 │
        Application Load Balancer
                 │
              Web Server
                 │
         Private Subnet
                 │
        Application Server
                 │
         Private Subnet
                 │
          Amazon RDS Database


---

Why Use Three Tiers?

Advantages:

Better security.

Easier scaling.

High availability.

Fault isolation.

Easier maintenance.



---

Chapter 3 – High Availability

AWS recommends deploying resources across multiple Availability Zones.

Example:

VPC
 │
 ├── Public Subnet (AZ-1)
 │      └── Web Server
 │
 ├── Public Subnet (AZ-2)
 │      └── Web Server
 │
 ├── Private Subnet (AZ-1)
 │      └── Application Server
 │
 └── Private Subnet (AZ-2)
        └── Application Server

Benefits:

Improved fault tolerance.

Continuous service during failures.

Better reliability.



---

Chapter 4 – AWS Networking Best Practices

AWS recommends:

VPC

Create custom VPCs for production.

Plan CIDR ranges carefully.



---

Subnets

Keep databases in private subnets.

Keep web servers in public subnets.



---

Security Groups

Allow only required ports.

Restrict SSH access to trusted IPs.

Remove unused rules.



---

Route Tables

Keep routing simple.

Avoid unnecessary routes.



---

Internet Gateway

Attach only one IGW per VPC.

Use only for public resources.



---

NAT Gateway

Place NAT Gateway in a public subnet.

Use it for outbound internet access from private subnets.



---

Chapter 5 – Common Troubleshooting

Problem

Cannot SSH into EC2.

Possible causes:

Port 22 blocked.

Wrong key pair.

Missing public IP.

Route Table issue.

Internet Gateway not attached.

Security Group misconfiguration.



---

Problem

Website not loading.

Check:

EC2 running.

Web server running.

Port 80 open.

Internet Gateway attached.

Route Table configured.

Security Group allows HTTP.



---

Problem

Private EC2 cannot access the Internet.

Check:

NAT Gateway exists.

NAT Gateway is in a public subnet.

Private subnet Route Table points to the NAT Gateway.



---

Chapter 6 – Cloud Practitioner Interview Questions

1. What is Amazon VPC?


2. Why is Amazon VPC required?


3. What is CIDR notation?


4. Difference between public and private IP?


5. What is a subnet?


6. Difference between public and private subnet?


7. What is an Internet Gateway?


8. What is a Route Table?


9. What is a NAT Gateway?


10. Why is a NAT Gateway placed in a public subnet?


11. What is an Elastic IP?


12. Difference between Public IP and Elastic IP?


13. What is a Security Group?


14. Why is a Security Group stateful?


15. What is a Network ACL?


16. Difference between Security Group and Network ACL?


17. Why should databases be in private subnets?


18. What is a three-tier architecture?


19. What is high availability?


20. Explain the path of an HTTP request from a browser to an EC2 instance.




---

Chapter 7 – Day 10 Hands-on Summary

Today you explored:

Amazon VPC

CIDR Blocks

Public and Private Subnets

Internet Gateway

Route Tables

NAT Gateway

Elastic IP

Security Groups

Network ACLs

End-to-End Traffic Flow



