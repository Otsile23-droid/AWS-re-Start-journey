# 📡 AWS Networking Notes

## 1. Overview

AWS networking services allow you to securely connect, manage, and scale your applications in the cloud. Core concepts include VPCs, subnets, routing, security, and connectivity options.

---

## 2. Core Networking Services

### A. Amazon VPC (Virtual Private Cloud)

- **Purpose:** Isolated virtual network for AWS resources
- **Key Components:**
  - Subnets (public, private)
  - Route tables
  - Internet Gateway (IGW)
  - NAT Gateway
  - Security Groups
  - Network ACLs
- **Exam Tips:** Every AWS account comes with a default VPC; use custom VPCs for isolation and advanced control.

---

### B. Subnets

- **Public Subnet:** Has route to the internet via IGW
- **Private Subnet:** No direct internet access; use NAT for outbound traffic
- **Exam Tip:** Place databases in private subnets, web servers in public subnets.

---

### C. Route Tables

- **Purpose:** Control traffic routing within a VPC
- **Key Points:**
  - Associate route tables with subnets
  - Routes define destinations and targets (e.g., IGW, NAT)

---

### D. Internet Connectivity

- **Internet Gateway (IGW):** Enables public internet access
- **NAT Gateway / NAT Instance:** Allows private subnet resources to access the internet (outbound only)

---

### E. Security in Networking

1. **Security Groups:** Instance-level firewall, allow inbound/outbound traffic
2. **Network ACLs (NACLs):** Subnet-level firewall, stateless
3. **Exam Tip:** Security groups are stateful (return traffic allowed automatically); NACLs are stateless (must allow return traffic explicitly)

---

### F. DNS & Domain Services

- **Amazon Route 53:** Scalable DNS service
  - Domain registration
  - Routing policies: Simple, Failover, Geolocation, Latency-based
- **Private Hosted Zones:** DNS within a VPC

---

### G. Load Balancing & High Availability

- **Elastic Load Balancing (ELB):**
  - Application Load Balancer (ALB) – HTTP/HTTPS
  - Network Load Balancer (NLB) – TCP/UDP, high performance
  - Gateway Load Balancer (GLB) – integrates virtual appliances
- **Exam Tip:** ALB → web traffic, NLB → low-latency network traffic

---

### H. VPN & Direct Connect

- **VPN:** Secure IPsec connection from on-premise to AWS
- **AWS Direct Connect:** Dedicated private connection for high throughput/low latency
- **Exam Tip:** Use Direct Connect for production environments requiring consistent performance.

---

### I. VPC Peering & Transit Gateway

- **VPC Peering:** Connect two VPCs (same or different accounts) directly
- **Transit Gateway:** Central hub to connect multiple VPCs and on-premises networks
- **Exam Tip:** Transit Gateway simplifies complex VPC-to-VPC connectivity.

---

### J. Monitoring & Troubleshooting

- **VPC Flow Logs:** Capture network traffic for analysis
- **CloudWatch Metrics:** Monitor NAT, IGW, and network throughput
- **CloudTrail:** Audit API calls for networking changes

---

## 3. Exam Tips Summary

| Service/Feature               | Key Purpose                          |
| ----------------------------- | ------------------------------------ |
| VPC                           | Isolated network for AWS resources   |
| Subnet                        | Public/private segmentation          |
| Security Group                | Instance-level firewall              |
| NACL                          | Subnet-level firewall                |
| IGW                           | Internet access                      |
| NAT Gateway                   | Outbound internet for private subnet |
| Route 53                      | DNS & domain routing                 |
| ELB                           | Load balancing                       |
| VPN / Direct Connect          | On-premises connectivity             |
| VPC Peering / Transit Gateway | VPC-to-VPC networking                |

---

### 🔗 References

- [Amazon VPC Documentation](https://aws.amazon.com/vpc/)
- [Amazon Route 53 Documentation](https://aws.amazon.com/route53/)
- [Elastic Load Balancing Documentation](https://aws.amazon.com/elasticloadbalancing/)
- [AWS Direct Connect Documentation](https://aws.amazon.com/directconnect/)
