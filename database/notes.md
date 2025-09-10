# 📚 AWS Database Notes

## 1. Overview

AWS provides fully managed, scalable, and secure database services for different workloads, including relational, non-relational, in-memory, and data warehousing solutions. Choosing the right database depends on your application’s needs.

---

## 2. Database Types

### A. Relational Databases (RDS)

- **Service:** Amazon RDS (Relational Database Service)
- **Purpose:** Managed relational database (SQL-based)
- **Engines Supported:**
  - MySQL
  - PostgreSQL
  - MariaDB
  - Oracle
  - SQL Server
  - Amazon Aurora (high-performance, MySQL/PostgreSQL compatible)
- **Key Features:**
  - Automated backups & snapshots
  - Multi-AZ deployment for high availability
  - Read replicas for scalability
  - Monitoring via CloudWatch
- **Exam Tips:** RDS is managed, supports SQL queries, not for NoSQL workloads.

---

### B. NoSQL Databases

#### 1. Amazon DynamoDB

- **Purpose:** Fully managed, fast, key-value and document database
- **Key Features:**
  - Single-digit millisecond latency
  - Fully serverless
  - Auto-scaling
  - Global tables for multi-region replication
- **Use Case:** Mobile apps, gaming, IoT, real-time applications

#### 2. Amazon DocumentDB

- **Purpose:** Managed document database (MongoDB-compatible)
- **Key Features:**
  - JSON document model
  - Fully managed
  - High availability with Multi-AZ
- **Use Case:** Applications that need MongoDB but want managed service

---

### C. In-Memory Databases

#### Amazon ElastiCache

- **Purpose:** Fully managed in-memory caching
- **Engines:**
  - Redis
  - Memcached
- **Key Features:**
  - Speeds up database queries
  - Low-latency access
  - Supports session storage, caching, real-time analytics

---

### D. Data Warehousing

#### Amazon Redshift

- **Purpose:** Managed petabyte-scale data warehouse
- **Key Features:**
  - Columnar storage for fast analytics
  - Redshift Spectrum for querying S3 directly
  - Concurrency scaling & automatic backups
- **Use Case:** BI, analytics, large datasets

---

### E. Other Specialized Databases

1. **Amazon Neptune** – Graph database (for social networks, recommendation engines)
2. **Amazon QLDB** – Ledger database (immutable, cryptographically verifiable)
3. **Amazon Timestream** – Time-series database (IoT, operational monitoring)

---

## 3. Database Storage Options

- **Amazon EBS:** Block storage for EC2 and RDS
- **Amazon S3:** Object storage, can integrate with Athena, Redshift
- **Amazon FSx:** File storage for Windows/Linux workloads

---

## 4. Security

- **Encryption at rest**: KMS (Key Management Service)
- **Encryption in transit**: SSL/TLS
- **IAM integration**: Control who can access database resources
- **VPC integration**: Secure access within your network

---

## 5. Backup & Recovery

- Automated backups (RDS)
- Snapshots
- Point-in-time recovery (PITR)
- Cross-region replication (for disaster recovery)

---

## 6. Monitoring & Maintenance

- **AWS CloudWatch:** Metrics, alarms
- **Enhanced monitoring:** OS-level metrics
- **RDS Events & Logs:** Track database events, audit logs

---

## 7. Exam Tips

- RDS → SQL workloads
- DynamoDB → NoSQL, key-value/document
- ElastiCache → In-memory caching
- Redshift → Analytics & data warehousing
- Neptune → Graph DB, social/recommendation use cases
- Timestream → IoT/time-series data

---

### 🔗 References

- [AWS RDS Documentation](https://aws.amazon.com/rds/)
- [AWS DynamoDB Documentation](https://aws.amazon.com/dynamodb/)
- [AWS Redshift Documentation](https://aws.amazon.com/redshift/)
- [AWS ElastiCache Documentation](https://aws.amazon.com/elasticache/)
