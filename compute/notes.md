# ⚡ AWS Compute Services Notes

## 1. Overview

AWS compute services provide scalable processing power in the cloud. They let you run applications, websites, and backend services without managing physical servers. Services vary from virtual servers to serverless functions.

---

## 2. Core Compute Services

### A. Amazon EC2 (Elastic Compute Cloud)

- **Purpose:** Virtual servers in the cloud
- **Key Features:**
  - Wide range of instance types (CPU, memory, GPU optimized)
  - Elastic Load Balancing for traffic distribution
  - Auto Scaling to handle traffic spikes
  - Amazon Machine Images (AMIs) for preconfigured servers
- **Exam Tips:** EC2 is fully customizable but requires server management; choose EC2 for long-running applications.

---

### B. AWS Lambda

- **Purpose:** Serverless compute for event-driven workloads
- **Key Features:**
  - Run code without provisioning servers
  - Pay only for execution time (100ms increments)
  - Integrates with S3, DynamoDB, API Gateway, CloudWatch
  - Scales automatically
- **Use Cases:** Real-time file processing, API backends, automated workflows
- **Exam Tip:** Lambda is serverless; no need to manage OS or instances.

---

### C. Amazon ECS (Elastic Container Service)

- **Purpose:** Managed container orchestration service
- **Key Features:**
  - Runs Docker containers
  - Supports Fargate (serverless containers)
  - Integration with CloudWatch, IAM, ALB/NLB
- **Use Case:** Microservices, containerized applications

### D. Amazon EKS (Elastic Kubernetes Service)

- **Purpose:** Managed Kubernetes for container orchestration
- **Key Features:**
  - Runs Kubernetes clusters without managing control plane
  - Supports Fargate for serverless pods
  - Scales and manages container workloads efficiently
- **Use Case:** Complex microservices, Kubernetes-native applications

---

### E. AWS Batch

- **Purpose:** Managed batch processing service
- **Key Features:**
  - Efficiently run batch computing workloads
  - Dynamically provisions compute resources
  - Supports EC2 and Spot Instances for cost savings
- **Use Case:** Data processing, simulation, machine learning jobs

---

### F. AWS Outposts

- **Purpose:** On-premises extension of AWS
- **Key Features:**
  - Fully managed AWS infrastructure on-prem
  - Runs EC2, EBS, and other AWS services locally
- **Use Case:** Low-latency applications, hybrid cloud

---

### G. Elastic Beanstalk

- **Purpose:** PaaS for deploying web applications
- **Key Features:**
  - Automatically handles provisioning, load balancing, scaling, monitoring
  - Supports multiple languages: Java, Python, Node.js, .NET, PHP
- **Exam Tip:** Best for developers who want managed deployments without manual EC2 setup.

---

## 3. Auto Scaling

- **Purpose:** Automatically adjusts number of EC2 instances
- **Types:**
  - Dynamic scaling (based on CPU/memory, CloudWatch alarms)
  - Scheduled scaling (predefined time-based scaling)
- **Exam Tip:** Use with ELB to handle variable traffic.

---

## 4. Load Balancing

- **Elastic Load Balancing (ELB):**
  - Application Load Balancer (ALB) → HTTP/HTTPS traffic
  - Network Load Balancer (NLB) → TCP/UDP traffic
  - Gateway Load Balancer (GLB) → integrates virtual appliances
- **Purpose:** Distribute traffic across multiple instances to improve availability

---

## 5. Exam Tips Summary

| Service            | Purpose / Use Case                         |
| ------------------ | ------------------------------------------ |
| EC2                | Virtual servers for long-running apps      |
| Lambda             | Serverless, event-driven functions         |
| ECS                | Docker container orchestration             |
| EKS                | Kubernetes-managed container orchestration |
| Elastic Beanstalk  | Managed web app deployment                 |
| AWS Batch          | Batch processing workloads                 |
| Outposts           | On-prem AWS infrastructure                 |
| Auto Scaling & ELB | Scalability & high availability            |

---

### 🔗 References

- [Amazon EC2 Documentation](https://aws.amazon.com/ec2/)
- [AWS Lambda Documentation](https://aws.amazon.com/lambda/)
- [Amazon ECS Documentation](https://aws.amazon.com/ecs/)
- [Amazon EKS Documentation](https://aws.amazon.com/eks/)
- [AWS Elastic Beanstalk Documentation](https://aws.amazon.com/elasticbeanstalk/)
- [AWS Batch Documentation](https://aws.amazon.com/batch/)
