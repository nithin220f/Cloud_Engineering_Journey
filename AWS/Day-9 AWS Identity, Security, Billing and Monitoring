Da-9 Documentation 
AWS Identity, Security, Billing and Monitoring

Course

AWS Certified Cloud Practitioner (CLF-C02)

Module

AWS Identity and Access Management (IAM), AWS Billing and Cost Management, Amazon CloudWatch


---

Learning Objectives

After completing this module, you should be able to:

Explain AWS Identity and Access Management (IAM).

Explain authentication and authorization.

Understand IAM Users, Groups, Roles, and Policies.

Describe the AWS account root user.

Apply the Principle of Least Privilege.

Understand Multi-Factor Authentication (MFA).

Monitor AWS costs using Billing Dashboard and Cost Explorer.

Explain Amazon CloudWatch and its monitoring capabilities.



---

Chapter 1 – Identity and Access Management (IAM)

What is IAM?

According to AWS,

AWS Identity and Access Management (IAM) is a web service that helps you securely control access to AWS resources.

IAM enables you to:

Manage users and groups.

Define permissions.

Control authentication.

Control authorization.

Secure AWS resources.


IAM is available at no additional charge.


---

Authentication vs Authorization

Authentication answers:

> Who are you?



Examples

Username

Password

MFA

Access Key


Authorization answers:

> What are you allowed to do?



Examples

Launch EC2

Read S3 Objects

Delete Buckets

Stop EC2 Instances


Authentication always happens before authorization.


---

Why IAM is Important

Without IAM:

Everyone would use the Root User.

No permission separation.

High security risk.

No auditing.


With IAM:

Every user has unique credentials.

Permissions are controlled.

Security improves.

Activities are traceable.



---

Features of IAM

AWS provides:

Centralized access management

Fine-grained permissions

Temporary credentials

Multi-Factor Authentication

Identity Federation

Access Analyzer

IAM Roles

IAM Policies



---

Chapter 2 – Root User

Definition

The AWS Account Root User is created when an AWS account is first created.

It has complete, unrestricted access to every AWS service and resource.

There is only one Root User for each AWS account.


---

Root User Permissions

The Root User can:

Delete the AWS account.

Change payment information.

Modify support plans.

Close the AWS account.

Restore IAM administrator permissions.

Access every AWS service.



---

AWS Best Practices

AWS recommends:

✔ Enable MFA

✔ Never share Root credentials

✔ Do not create Access Keys

✔ Use Root User only when absolutely necessary

✔ Create IAM Users for daily work


---

Chapter 3 – IAM Users

Definition

An IAM User is an identity created within an AWS account.

Each IAM User represents:

A person

An administrator

A developer

An application


Every IAM User has unique credentials.


---

IAM User Credentials

An IAM User may have:

Console Password

Access Key ID

Secret Access Key


These credentials determine how the user accesses AWS.


---

Why Create IAM Users?

Instead of sharing one Root account,

AWS recommends creating separate IAM Users because:

Better security

Individual accountability

Easier auditing

Better permission management



---

Chapter 4 – IAM Groups

Definition

An IAM Group is a collection of IAM Users.

Groups make permission management easier.

Instead of assigning permissions individually,

Assign permissions once to the group.

Every member inherits those permissions.


---

Example

Company

↓

AWS Account

↓

Developers Group

↓

Alice

Bob

Charlie

If Developers Group receives:

AmazonEC2FullAccess

↓

Every member automatically receives EC2 permissions.


---

Advantages

Simplifies administration

Reduces duplicate work

Easier permission updates

Consistent security



---

Chapter 5 – IAM Policies

Definition

An IAM Policy is a JSON document that defines permissions.

Policies specify:

Which actions are allowed.

Which actions are denied.

Which AWS resources are affected.

Optional conditions.


Policies are attached to:

Users

Groups

Roles



---

Policy Structure

A policy contains:

Effect (Allow or Deny)

Action

Resource

Condition (optional)



---

Types of Policies

AWS Managed Policies

Created by AWS.

Examples

AmazonS3ReadOnlyAccess

AmazonEC2ReadOnlyAccess


---

Customer Managed Policies

Created and maintained by customers.

Useful when custom permissions are required.


---

Inline Policies

Embedded directly into a single IAM identity.

Used for special-purpose permissions.


---

Chapter 6 – IAM Roles

Definition

An IAM Role is an AWS identity with specific permissions that can be assumed by trusted entities.

Unlike IAM Users,

Roles do not have:

Password

Permanent Access Keys


AWS automatically provides temporary security credentials.


---

Why IAM Roles?

Suppose:

EC2 needs to access S3.

Option 1

Store AWS Access Keys.

Problem

If someone steals the keys,

They can access AWS.

Option 2

Attach an IAM Role.

AWS automatically provides temporary credentials.

Much safer.

This is AWS Best Practice.


---

Common Uses

EC2 → S3

Lambda → DynamoDB

CloudFormation

Cross Account Access

Amazon ECS

Amazon EKS


---

Chapter 7 – Principle of Least Privilege

Definition

Grant only the permissions required to perform a task.

No additional permissions.


---

Example

Developer only uploads files to S3.

Correct

AmazonS3ReadOnlyAccess

Incorrect

AdministratorAccess


---

Benefits

Reduced attack surface.

Improved security.

Prevents accidental deletion.

Meets compliance requirements.


---

Chapter 8 – Multi-Factor Authentication (MFA)

Definition

MFA provides an extra layer of security.

Users provide:

Something they know

↓

Password

AND

Something they have

↓

Authenticator App

Security Key

OTP


---

AWS Recommendation

Enable MFA for:

Root User

IAM Administrators


---

Benefits

Protection against password theft.

Reduced unauthorized access.

Improved account security.


---

Chapter 9 – AWS Billing and Cost Management

AWS Billing helps monitor:

Current charges.

Service-wise costs.

Credits.

Budgets.

Invoices.

Forecasted spending.


---

Billing Dashboard

Displays:

Current month's charges.

Top services.

Taxes.

Forecast.

Credits.


---

AWS Credits

Credits reduce AWS costs.

Example

Credits Remaining

↓

$99.80

Until exhausted or expired.


---

Cost Explorer

Provides graphs for:

Daily spending.

Monthly spending.

Service-wise costs.

Usage trends.

Forecasts.


---

Free Tier

AWS Free Tier allows eligible customers to use selected AWS services at no cost within defined limits.

Always monitor usage to avoid unexpected charges.


---

Chapter 10 – Amazon CloudWatch

Definition

Amazon CloudWatch is a monitoring and observability service.

It collects operational data from AWS resources.


---

CloudWatch Monitors

EC2

Lambda

RDS

DynamoDB

EBS

Load Balancers

Applications


---

Metrics

Metrics are time-ordered data points.

Examples

CPU Utilization

Disk Read Ops

Disk Write Ops

Network In

Network Out

Status Checks

Memory (custom)


---

Logs

CloudWatch Logs store:

Application logs.

Operating system logs.

Custom logs.


---

Alarms

CloudWatch Alarms monitor metrics.

Example

CPU > 80%

↓

Send SNS Notification

↓

Trigger Auto Scaling


---

Dashboards

Dashboards combine metrics from multiple services into one customizable view for operational monitoring.


---

Root User vs IAM User

Root User	IAM User

One per account	Many users
Full access	Limited permissions
Used rarely	Daily operations
Cannot be restricted	Permissions controlled by IAM



---

IAM User vs IAM Role

IAM User	IAM Role

Permanent identity	Temporary identity
Long-term credentials	Temporary credentials
Represents a person or application	Assumed by users or AWS services



---

IAM Group vs IAM Policy

IAM Group	IAM Policy

Collection of users	Permission document
Organizes users	Defines access rights



---

Security Best Practices

Never use the Root User for everyday tasks.

Enable MFA on the Root User and privileged IAM users.

Apply the Principle of Least Privilege.

Use IAM Roles instead of embedding access keys in applications.

Rotate credentials when necessary.

Regularly review IAM permissions.

Monitor account activity and billing.



---

Interview Questions

1. What is IAM?


2. What is authentication and authorization?


3. Why should you avoid using the Root User daily?


4. What is an IAM User?


5. What is an IAM Group?


6. What is an IAM Policy?


7. What is an IAM Role?


8. Why are IAM Roles preferred over Access Keys?


9. What is the Principle of Least Privilege?


10. Why should MFA be enabled?


11. What is AWS Billing and Cost Management?


12. What is Amazon CloudWatch?


13. What are CloudWatch Metrics, Logs, Alarms, and Dashboards?

