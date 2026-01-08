# AWS Private Subnet & Secure Access Lab

## Overview
This lab focused on designing a production-style AWS network architecture that minimises attack surface by isolating workloads from direct internet exposure. The primary goal was to deploy a compute resource in a private subnet and implement secure, auditable administrative access without relying on SSH or public IP addresses.

The lab builds on foundational cloud security concepts by introducing private networking, managed access patterns, and AWS-native connectivity mechanisms.

---

## Objectives
- Design a VPC with clearly separated public and private subnets  
- Deploy an EC2 instance with **no public IP address**  
- Eliminate SSH access and inbound ports  
- Implement secure administrative access using **AWS Systems Manager (Session Manager)**  
- Enable private connectivity to AWS services using **VPC interface endpoints**  
- Validate isolation and audit access using CloudTrail  

---

## Architecture
The lab environment consisted of:

- A custom **VPC**
- One **public subnet** (network entry point)
- One **private subnet** (protected workload)
- An **EC2 instance** deployed in the private subnet
- An **IAM role** granting Systems Manager access
- **VPC interface endpoints** for:
  - AWS Systems Manager (`ssm`)
  - EC2 messages (`ec2messages`)
  - SSM messages (`ssmmessages`)
- **AWS CloudTrail** for management event logging

The EC2 instance had no public IP address and no inbound security group rules, ensuring it was not reachable from the internet.

---

## Key Implementation Steps

### 1. Network Segmentation
A VPC was created with two subnets:
- **Public subnet** with an internet gateway route
- **Private subnet** with no route to the internet

Routing decisions, not subnet naming, were used to control exposure.

---

### 2. Private EC2 Deployment
An EC2 instance running Amazon Linux was launched in the private subnet with:
- Public IP assignment disabled
- A security group with **no inbound rules**
- An IAM role attached for Systems Manager access

This ensured the instance could not be accessed directly via the network.

---

### 3. Secure Access via Session Manager
Instead of SSH, administrative access was achieved using **AWS Systems Manager (Session Manager)**:
- No SSH keys were generated or stored
- No ports were opened
- Access was controlled entirely through IAM permissions

This approach provides secure, temporary, and fully auditable access.

---

### 4. Private Connectivity Using VPC Endpoints
To allow the private instance to communicate with Systems Manager without internet access, **VPC interface endpoints** were created for the required AWS services.

This enabled:
- Private, AWS-managed connectivity
- No reliance on NAT gateways or public routing
- Reduced attack surface and improved security posture

---

### 5. Validation & Audit Logging
Access to the instance was validated by successfully connecting through Session Manager.

Auditability was confirmed by:
- Reviewing **CloudTrail events** related to:
  - VPC endpoint creation
  - Session Manager access
- Verifying that all access was tied to IAM identities and timestamps

---

## Security Concepts Demonstrated
- Network isolation through private subnets  
- Elimination of public exposure  
- IAM-based access control  
- Secure, managed administrative access  
- Private connectivity to cloud services  
- Centralised audit logging  

---

## Key Takeaways
- Public IP addresses and SSH access are often unnecessary in cloud environments  
- Private subnets significantly reduce attack surface  
- AWS Systems Manager provides a secure alternative to traditional remote access  
- VPC endpoints allow private resources to interact with AWS services securely  
- Cloud-native logging is essential for accountability and investigation  

---

## Cleanup
All resources were terminated and deleted after completion to prevent ongoing costs, including:
- EC2 instance
- VPC interface endpoints
- IAM role (where applicable)
- VPC and associated networking components

---

## Tools & Services Used
- AWS EC2  
- AWS VPC  
- AWS IAM  
- AWS Systems Manager (Session Manager)  
- AWS VPC Interface Endpoints  
- AWS CloudTrail  
- Amazon Linux  

---

## Screenshots
> Identifiers have been redacted for security.

![Private EC2 Instance](screenshots/ec2-private-no-public-ip.png)
![Session Manager Access](screenshots/session-manager-redacted.png)

---

## Next Steps
This lab prepares the foundation for cloud threat detection and response, which is explored in the next lab using **AWS GuardDuty**.
