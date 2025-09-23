# Creating Amazon EC2 Instances

<img src="compute\screenshots\creating_Amazon_EC2_instances.png" alt="EC2 Lab Architecture">

## Lab Overview

AWS provides multiple ways to launch Amazon Elastic Compute Cloud (Amazon EC2) instances. In this lab, you use the **AWS Management Console** to launch an EC2 instance and then use it as a **bastion host** to launch another EC2 instance, which will be a web server. You use **EC2 Instance Connect** to securely connect to the bastion host and use the **AWS Command Line Interface (AWS CLI)** to launch a web server instance.

- **Bastion Host**: A secure gateway instance that provides controlled access to your private infrastructure
- **AWS CLI**: Command-line tool for automating AWS resource provisioning and management
- **EC2 Instance Connect**: Browser-based SSH connection method for secure instance access

This lab demonstrates both manual (console) and automated (CLI) approaches to EC2 instance deployment.

---

## Objectives

By the end of this lab, you will be able to:

- Create an **EC2 instance** using the AWS Management Console
- Configure **security groups, VPCs, and IAM roles** properly
- Connect to instances using **EC2 Instance Connect**
- Launch instances programmatically using the **AWS CLI**
- Implement **automation best practices** for repeatable deployments

---

## Task 1: Launch EC2 Instance via AWS Console

1. Open **AWS Console → EC2 → Launch instance**
2. Configure the bastion host:
   - **Name:** `Bastion host`
   - **AMI:** Amazon Linux 2
   - **Instance type:** `t3.micro`
   - **Key pair:** Proceed without key pair
3. Network settings:
   - **VPC:** `Lab VPC`
   - **Subnet:** `Public Subnet`
   - **Auto-assign public IP:** Enable
4. Security group:
   - **Name:** `Bastion security group`
   - **Description:** `Permit SSH connections`
5. **IAM role:** `Bastion-Role` (for AWS CLI access)
6. **Launch instance** → Confirm creation

---

## Task 2: Connect to Bastion Host

1. **EC2 Console → Instances** → Select bastion host
2. Choose **Connect → EC2 Instance Connect**
3. Click **Connect** → Terminal session opens
4. Verify AWS CLI access:
   ```bash
   aws --version
   ```
   <img src="compute\screenshots\Bastion_Host_connected.png" alt="Bastion Host Connected">

---

## Task 3: Launch Web Server via AWS CLI

### Step 1: Get Latest AMI ID

### Step 2: Get Subnet ID

### Step 3: Get Security Group ID

### Step 4: Download User Data Script

<img src="compute\screenshots\launching_web_server_via_AWS_CLI.png" >

### Step 5: Launch Web Server Instance

```bash
INSTANCE=$(aws ec2 run-instances \
--image-id $AMI \
--subnet-id $SUBNET \
--security-group-ids $SG \
--user-data file:///home/ec2-user/UserData.txt \
--instance-type t3.micro \
--tag-specifications 'ResourceType=instance,Tags=[{Key=Name,Value=Web Server}]' \
--query 'Instances[*].InstanceId' \
--output text)
echo $INSTANCE
```

### Step 6: Monitor Instance Status

```bash
# Check instance state (run until "running")
aws ec2 describe-instances --instance-ids $INSTANCE --query 'Reservations[].Instances[].State.Name' --output text
```

<img src="compute\screenshots\Web_Server_running.png" alt="Web Server Success">

### Step 7: Test Web Server

```bash
# Get public DNS name
aws ec2 describe-instances --instance-ids $INSTANCE --query Reservations[].Instances[].PublicDnsName --output text
```

Copy the DNS name → Open in browser → Verify web application loads

<img src="compute\screenshots\Web_Server_success.png" alt="Web Server Success">

## Summary

This lab demonstrated **multiple approaches to EC2 deployment**:

- **Manual deployment** using AWS Management Console for learning and quick setups
- **Automated deployment** using AWS CLI for repeatable, scalable infrastructure
- **Best practices** for security groups, IAM roles, and resource tagging

## Challenges You Might Encounter

- **Permission Issues**: IAM role not attached or insufficient permissions
- **Network Connectivity**: Security group rules blocking required ports
- **Instance Metadata Service**: IMDS v2 enforcement affecting metadata access
- **User Data Script Failures**: Syntax errors or network timeouts during package installation
- **Environment Variable Loss**: Session disconnection clearing stored values
- **Region Mismatches**: Resources created in different regions than expected
