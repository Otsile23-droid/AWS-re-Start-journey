# AWS Storage Services

### Amazon S3 (Simple Storage Service)

- Object storage service offering industry-leading durability (99.999999999%)
- Stores data as objects in buckets with unlimited scalability
- Supports versioning, lifecycle policies, and encryption
- Ideal for: static websites, data lakes, backup/archive, application hosting

### Amazon EBS (Elastic Block Store)

- High-performance block storage volumes for EC2 instances
- Provides persistent storage with automatic replication
- Multiple volume types (gp3, io2, st1, sc1) for different workloads
- Perfect for: databases, enterprise applications, development environments

### Amazon EFS (Elastic File System)

- Fully managed NFS file system for Linux workloads
- Auto-scaling storage with consistent low latency
- Supports thousands of concurrent connections
- Best for: web serving, content management, application development

### Amazon FSx

- Fully managed file systems for enterprise applications
- Options include:
  - FSx for Windows File Server
  - FSx for Lustre (high-performance computing)
  - FSx for NetApp ONTAP
  - FSx for OpenZFS

### Amazon S3 Glacier

- Ultra low-cost archival storage service
- Multiple retrieval options:
  - Glacier Instant Retrieval
  - Glacier Flexible Retrieval
  - Glacier Deep Archive
- Ideal for: long-term backup, digital preservation, compliance data
