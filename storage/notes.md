# 💾 AWS Storage Services Notes

## 1. Overview

AWS storage services provide secure, scalable, and durable storage solutions for different workloads, from simple file storage to large-scale data lakes. Choosing the right storage depends on access patterns, performance, and cost.

---

## 2. Core Storage Services

### A. Amazon S3 (Simple Storage Service)

- **Purpose:** Object storage for any type of data
- **Key Features:**
  - Scalable and durable (11 9’s durability)
  - Storage classes: Standard, Intelligent-Tiering, Infrequent Access, Glacier, Glacier Deep Archive
  - Versioning, replication, lifecycle policies
- **Use Case:** Backup, archival, static website hosting, data lakes
- **Exam Tip:** Object-level storage; not a file system.

---

### B. Amazon EBS (Elastic Block Store)

- **Purpose:** Block storage for EC2 instances
- **Key Features:**
  - Persistent storage attached to EC2
  - Snapshots for backup
  - Volume types: General Purpose SSD, Provisioned IOPS SSD, Magnetic
- **Use Case:** Databases, applications requiring low-latency block storage
- **Exam Tip:** Must be attached to EC2; different from S3 object storage.

---

### C. Amazon EFS (Elastic File System)

- **Purpose:** Fully managed scalable file storage
- **Key Features:**
  - NFS protocol support
  - Automatically scales as files are added/removed
  - Multi-AZ availability
- **Use Case:** Shared file storage for multiple EC2 instances

---

### D. Amazon FSx

- **Purpose:** Fully managed file storage for specific workloads
- **Types:**
  - **FSx for Windows File Server:** SMB protocol, Active Directory integration
  - **FSx for Lustre:** High-performance computing workloads
  - **FSx for NetApp ONTAP:** Enterprise-grade storage
- **Use Case:** Windows applications, HPC workloads

---

### E. AWS Snow Family

- **Purpose:** Physical devices for transferring large amounts of data to/from AWS
- **Services/Devices:**
  - **Snowcone:** Small, portable edge device (2TB)
  - **Snowball:** Rugged, medium-scale data transfer (up to 80TB per device)
  - **Snowmobile:** Exabyte-scale data transfer (truck-sized for massive migrations)
- **Key Features:**
  - Secure, offline data transfer
  - Encryption at rest and in transit
  - Integration with S3
- **Use Case:** Large-scale migrations, edge computing, disaster recovery
- **Exam Tip:** Use Snow Family when network transfer is impractical due to size or bandwidth.

---

### F. AWS Backup

- **Purpose:** Centralized backup service for AWS resources
- **Key Features:**
  - Automates backup for EBS, RDS, DynamoDB, EFS, FSx
  - Policy-based backup scheduling
  - Cross-region backup support
- **Exam Tip:** Use to meet compliance and disaster recovery requirements.

---

### G. Storage Gateway

- **Purpose:** Hybrid cloud storage solution
- **Types:**
  - **File Gateway:** NFS/SMB access to S3
  - **Volume Gateway:** Block storage backup to S3
  - **Tape Gateway:** Backup to virtual tapes in S3/Glacier
- **Use Case:** Connect on-premises storage to AWS

---

## 3. Storage Security & Access

- **Encryption:** At rest (S3, EBS, EFS, Snow Family) and in transit (SSL/TLS)
- **Access Control:** IAM policies, bucket policies, ACLs
- **Versioning & MFA Delete:** Protects against accidental deletion

---

## 4. Exam Tips Summary

| Service         | Type / Purpose                                              |
| --------------- | ----------------------------------------------------------- |
| S3              | Object storage, data lakes, backups                         |
| EBS             | Block storage for EC2                                       |
| EFS             | Shared file storage for EC2                                 |
| FSx             | Managed file system for Windows/HPC                         |
| Snow Family     | Offline/edge data transfer (Snowcone, Snowball, Snowmobile) |
| AWS Backup      | Centralized backup management                               |
| Storage Gateway | Hybrid cloud storage for on-premises integration            |

---

### 🔗 References

- [Amazon S3 Documentation](https://aws.amazon.com/s3/)
- [Amazon EBS Documentation](https://aws.amazon.com/ebs/)
- [Amazon EFS Documentation](https://aws.amazon.com/efs/)
- [Amazon FSx Documentation](https://aws.amazon.com/fsx/)
- [AWS Snow Family Documentation](https://aws.amazon.com/snow/)
- [AWS Backup Documentation](https://aws.amazon.com/backup/)
- [AWS Storage Gateway Documentation](https://aws.amazon.com/storagegateway/)
