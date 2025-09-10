# 🔒 AWS Security Services Notes

## 1. Overview

AWS provides a comprehensive set of security services to protect cloud workloads, data, and applications. Security is shared between AWS (infrastructure) and the customer (data, access, configurations).

---

## 2. Identity & Access Management

### A. AWS IAM (Identity and Access Management)

- **Purpose:** Manage users, groups, roles, and permissions
- **Key Features:**
  - Fine-grained access control with policies
  - Roles for EC2, Lambda, and other services
  - Multi-Factor Authentication (MFA)
- **Exam Tip:** IAM is global, not tied to regions; use least-privilege principle.

### B. AWS Organizations

- **Purpose:** Centralized account management for multiple AWS accounts
- **Key Features:**
  - Service Control Policies (SCPs) to enforce permissions
  - Consolidated billing
- **Use Case:** Large enterprises managing multiple accounts

---

## 3. Threat Detection & Monitoring

### A. AWS GuardDuty

- **Purpose:** Threat detection service for AWS accounts
- **Key Features:**
  - Detects unusual activity using ML and threat intelligence
  - Monitors CloudTrail, VPC Flow Logs, DNS logs
- **Exam Tip:** Always enabled per account/region; does not prevent attacks, only detects.

### B. AWS Inspector

- **Purpose:** Automated vulnerability assessment for EC2
- **Key Features:**
  - Checks OS, network configurations, and application security
  - Generates findings for remediation

### C. AWS Macie

- **Purpose:** Data security & privacy for sensitive data
- **Key Features:**
  - Detects PII (Personally Identifiable Information) in S3
  - Uses ML to classify and protect data

---

## 4. Network & Application Security

### A. AWS Shield

- **Purpose:** DDoS protection for AWS workloads
- **Tiers:**
  - Standard → automatic protection for all AWS customers
  - Advanced → extra protection and attack reporting
- **Use Case:** Protect websites and applications from denial-of-service attacks

### B. AWS WAF (Web Application Firewall)

- **Purpose:** Protects web applications from common exploits
- **Key Features:**
  - Blocks SQL injection, XSS, and other attack types
  - Works with CloudFront, ALB, and API Gateway

### C. AWS Firewall Manager

- **Purpose:** Centralized management for WAF, Shield Advanced, and security groups
- **Use Case:** Apply security policies across multiple accounts/VPCs

---

## 5. Data Protection & Encryption

### A. AWS KMS (Key Management Service)

- **Purpose:** Manage encryption keys
- **Key Features:**
  - Create and control encryption keys for AWS services
  - Integrates with S3, EBS, RDS, Lambda, and more
- **Exam Tip:** KMS encrypts data at rest; customer can manage keys or use AWS-managed keys.

### B. AWS Secrets Manager

- **Purpose:** Securely store and rotate secrets (passwords, API keys)
- **Key Features:**
  - Automatic secret rotation
  - Fine-grained access control via IAM

### C. AWS Certificate Manager (ACM)

- **Purpose:** Provision, manage, and deploy SSL/TLS certificates
- **Use Case:** Secure websites and APIs

---

## 6. Compliance & Governance

### A. AWS CloudTrail

- **Purpose:** Track API calls and account activity
- **Key Features:**
  - Audit AWS account activity
  - Store logs securely in S3

### B. AWS Config

- **Purpose:** Track resource configurations and compliance
- **Key Features:**
  - Monitor configuration changes
  - Evaluate against compliance rules

---

## 7. Exam Tips Summary

| Service                   | Purpose / Use Case                           |
| ------------------------- | -------------------------------------------- |
| IAM                       | Manage users, roles, permissions             |
| Organizations             | Multi-account management                     |
| GuardDuty                 | Threat detection                             |
| Inspector                 | Vulnerability assessment                     |
| Macie                     | Sensitive data discovery (PII)               |
| Shield                    | DDoS protection                              |
| WAF                       | Protect web apps from attacks                |
| Firewall Manager          | Centralized security policy management       |
| KMS                       | Encryption key management                    |
| Secrets Manager           | Secure secrets storage & rotation            |
| Certificate Manager (ACM) | SSL/TLS certificates                         |
| CloudTrail                | Audit API calls                              |
| Config                    | Resource configuration tracking & compliance |

---

### 🔗 References

- [AWS IAM Documentation](https://aws.amazon.com/iam/)
- [AWS GuardDuty Documentation](https://aws.amazon.com/guardduty/)
- [AWS Shield Documentation](https://aws.amazon.com/shield/)
- [AWS WAF Documentation](https://aws.amazon.com/waf/)
- [AWS KMS Documentation](https://aws.amazon.com/kms/)
- [AWS Secrets Manager Documentation](https://aws.amazon.com/secrets-manager/)
