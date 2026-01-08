# Lab 3 – AWS GuardDuty Threat Detection

## Overview

This lab focuses on **cloud-native threat detection** using **Amazon GuardDuty**. Building on previous labs that implemented secure AWS architectures, IAM least privilege, and private network access, this lab demonstrates how AWS detects **malicious activity, misconfigurations, and compromised resources** using managed threat intelligence and anomaly detection.

The goal of this lab is to understand how GuardDuty operates, analyse real security findings, and reason about appropriate **incident response actions** in a production cloud environment.

---

## Objectives

* Enable Amazon GuardDuty in an AWS account
* Understand GuardDuty data sources and detection methods
* Generate and analyse GuardDuty security findings
* Interpret threat severity levels and finding types
* Identify appropriate remediation and incident response actions

---

## AWS Services Used

* **Amazon GuardDuty** – Managed threat detection service
* **AWS CloudTrail** – API and management event logging
* **Amazon EC2** – Monitored compute resources
* **Amazon VPC** – Network traffic monitoring (VPC Flow Logs)

---

## Architecture Summary

* GuardDuty enabled in a single AWS region
* Monitoring of:

  * CloudTrail management events
  * VPC Flow Logs
  * DNS query logs
* Existing EC2 and IAM activity used as monitored resources

No additional infrastructure was deployed for this lab, as GuardDuty operates as a **fully managed, passive monitoring service**.

---

## Lab Steps

### 1. Enable Amazon GuardDuty

* Accessed the AWS Management Console
* Enabled GuardDuty in the selected region
* Verified successful activation via the GuardDuty dashboard

GuardDuty automatically began monitoring supported log sources without manual configuration.

---

### 2. Review GuardDuty Dashboard

* Examined the findings summary
* Reviewed severity classifications:

  * Low
  * Medium
  * High
* Identified threat categories such as:

  * Reconnaissance
  * Credential access
  * Discovery
  * Exfiltration

At initial deployment, no findings were present, which is expected in a newly enabled environment.

---

### 3. Generate Sample Findings

* Used the **Generate sample findings** feature
* Waited for findings to populate in the dashboard
* Verified multiple findings across different severity levels

Sample findings simulate realistic attack scenarios without impacting real resources.

---

### 4. Analyse Security Findings

Each finding was analysed based on:

* **Finding type** (e.g., reconnaissance or credential misuse)
* **Affected resource** (EC2 instance or IAM entity)
* **Threat severity**
* **Remote IP address and threat intelligence source**
* **Observed behaviour** (API calls or network activity)

Example findings included simulated port scanning activity and anomalous API usage.

---

### 5. Incident Response Considerations

For high-severity findings, the following response actions were considered:

* Isolating affected EC2 instances
* Rotating or disabling compromised IAM credentials
* Restricting network access using security groups or NACLs
* Increasing monitoring and alerting for affected resources

This step demonstrates security decision-making rather than automated remediation.

---

## Key Security Concepts Demonstrated

* Cloud-native threat detection
* Behavioural analysis and anomaly detection
* Severity-based incident prioritisation
* Shared responsibility model in AWS security
* Integration of detection into secure cloud architectures

---

## Learning Outcomes

By completing this lab, the following skills were developed:

* Understanding how AWS detects threats at scale
* Interpreting GuardDuty findings and threat metadata
* Analysing cloud security alerts in context
* Applying incident response reasoning in AWS environments

---

## Conclusion

This lab demonstrated how Amazon GuardDuty enhances AWS security by continuously monitoring account activity and detecting suspicious behaviour. When combined with secure architecture, IAM least privilege, and strong logging practices, GuardDuty provides critical visibility into potential compromises and misuse.

This lab complements previous work on secure design and zero-trust access by adding **active threat detection**, forming a key component of a defense-in-depth cloud security strategy.

---

## Cleanup

* Disabled Amazon GuardDuty after completing analysis to avoid unnecessary costs
* Verified no additional billable resources remained active

---


