# AWS Security Services

## Overview

AWS security services help you protect your cloud resources, detect threats, and ensure compliance. They provide visibility into your environment, enforce least-privilege access, and safeguard data from unauthorized use or attacks.

## Key Services

### 1. **AWS Identity and Access Management (IAM)**

- Manage users, groups, and roles.
- Define permissions using IAM policies (JSON).
- Supports MFA (Multi-Factor Authentication).
- Enforces least privilege.

### 2. **AWS Key Management Service (KMS)**

- Manage encryption keys.
- Integrated with most AWS services (e.g., S3, EBS, RDS).
- Supports customer-managed keys.

### 3. **AWS Shield**

- Managed DDoS protection service.
- **Standard** (free) defends against common network/transport attacks.
- **Advanced** offers enhanced DDoS protection with 24/7 support.

### 4. **Amazon GuardDuty**

- Intelligent threat detection using ML.
- Detects anomalies, compromised credentials, and malicious IPs.
- Provides security findings you can act on.

### 5. **AWS Trusted Advisor (Security Checks)**

- Highlights insecure configurations.
- Examples: exposed IAM keys, overly permissive security groups.

### 6. **AWS CloudTrail**

- Records API calls across AWS services.
- Enables auditing and governance.
- Useful for incident response and compliance.

### 7. **Amazon Inspector**

- Automated vulnerability management.
- Scans EC2 instances and ECR container images for software flaws.
