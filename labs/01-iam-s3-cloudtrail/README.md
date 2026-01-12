# Lab 1 – AWS Cloud Security Foundations: IAM, Secure Storage & Audit Logging

## Overview

This lab focused on building and securing a **foundational AWS cloud environment** while applying core cloud security principles around **identity management, secure resource access, and audit logging**. The objective was to understand how IAM, storage permissions, and logging work together in a real-world AWS environment, and how misconfigurations can be detected and remediated.

The lab was designed and executed using **AWS Free Tier services**, with an emphasis on secure defaults and cost-aware implementation.

---

## Objectives

* Deploy a basic AWS environment using security best practices
* Enforce **least-privilege access** using IAM roles instead of static credentials
* Secure access to cloud storage resources
* Enable and analyse **AWS CloudTrail** logs for audit visibility
* Simulate and remediate an IAM misconfiguration

---

## Architecture Overview

The lab environment consisted of the following components:

* A custom **Amazon VPC** with a single subnet
* An **EC2 instance** running Amazon Linux
* An **IAM role** attached directly to the EC2 instance
* An **Amazon S3 bucket** used to test controlled access
* **AWS CloudTrail** enabled for management event logging

The EC2 instance accessed AWS services exclusively via an IAM role, eliminating the use of long-lived access keys and reducing the risk of credential exposure.

---

## Key Implementation Steps

### Identity & Access Management

* Created an IAM role with **scoped permissions** for EC2
* Attached the role directly to the EC2 instance
* Verified access to S3 using **role-based credentials**
* Confirmed that no access keys were stored on the instance

This reinforced the importance of avoiding static credentials and relying on AWS-managed identity wherever possible.

---

### Secure Storage Access

* Created an S3 bucket with restricted access controls
* Granted the EC2 IAM role permission to list and read objects
* Validated that access was denied when permissions were removed

This demonstrated how IAM policies directly control access to cloud resources and how overly permissive policies can increase risk.

---

### Audit Logging with CloudTrail

* Enabled AWS CloudTrail for account-level management events
* Observed management activity including:

  * EC2 instance operations
  * IAM role usage
  * S3 access attempts
* Analysed event details such as:

  * Event source
  * Identity context
  * Timestamps and request metadata

CloudTrail provided full visibility into **who performed an action, what action was taken, and when it occurred**, supporting investigation and accountability.

---

### Misconfiguration Simulation & Remediation

* Intentionally applied an **overly permissive IAM policy**
* Verified that excessive permissions were granted
* Detected the change using CloudTrail event history
* Remediated the issue by restoring **least-privilege access**

This step highlighted how easily IAM misconfigurations can introduce security risk and why logging is critical for detection and response.

---

## Security Concepts Demonstrated

* Least-privilege access control
* Role-based authentication
* Secure cloud storage permissions
* Auditability and accountability
* Misconfiguration detection and remediation

---

## Key Takeaways

* IAM roles are significantly more secure than access keys
* CloudTrail is essential for audit visibility and security investigations
* IAM misconfigurations are a common source of cloud security risk
* Secure defaults combined with logging reduce the attack surface

---

## Cleanup

All AWS resources were terminated after completion of the lab to avoid ongoing costs and unnecessary exposure.

---

## Tools & Services Used

* Amazon EC2
* AWS Identity and Access Management (IAM)
* Amazon S3
* AWS CloudTrail
* Amazon Linux

---

## Notes

Sensitive identifiers and account-specific details were redacted from screenshots and documentation to maintain security best practices.

---

## Screenshots

Screenshots captured for this lab include:

* Showing Details of StopInstances Event
![IAM Event Timeline](screenshots/cloudtrail-event-lab1.png)


