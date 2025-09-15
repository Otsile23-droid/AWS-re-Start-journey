# Scaling and Load Balancing Your Architecture

<img src= "compute\scaling_and_load_balancing_lab.md" >

## Lab Overview

In this lab, you use **Elastic Load Balancing (ELB)** and **Amazon EC2 Auto Scaling** to automatically distribute and scale your infrastructure.

- **Elastic Load Balancing (ELB):** Distributes incoming application traffic across multiple EC2 instances for fault tolerance and reliability.
- **Auto Scaling:** Monitors application demand and adjusts EC2 capacity up or down automatically to maintain availability and optimize cost.

This lab demonstrates how to create an AMI, configure a load balancer, set up Auto Scaling, and test scaling under load.

---

## Objectives

By the end of this lab, you will be able to:

- Create an **Amazon Machine Image (AMI)** from an EC2 instance.
- Set up an **Application Load Balancer (ALB)**.
- Build a **launch template** and an **Auto Scaling group**.
- Configure Auto Scaling to operate within **private subnets**.
- Use **Amazon CloudWatch Alarms** to monitor performance.

---

## Task 1: Create an AMI from an EC2 Instance

1. Open **EC2 Console → Instances**.
2. Select the **Web Server 1** instance (running state).
3. Actions → **Image and templates → Create image**.
   - **Image name:** `Web Server AMI`
   - **Description:** `Lab AMI for Web Server`
4. Choose **Create image**.
5. Note the new AMI ID (used later in Auto Scaling).

---

## Task 2: Create a Load Balancer

1. In **EC2 Console → Load Balancers → Create load balancer**.
2. Select **Application Load Balancer**.
   - **Name:** `LabELB`
   - **VPC:** `Lab VPC`
   - Map both AZs → `Public Subnet 1` & `Public Subnet 2`.
   - **Security group:** `Web Security Group` (remove default).
3. Create a **Target Group**:
   - **Type:** Instances
   - **Name:** `lab-target-group`
4. Back in Load Balancer config:
   - **Listener → Forward to:** `lab-target-group`.
5. Create the load balancer and copy its **DNS name** for later testing.
   <img src= "compute\lab_target_group.png" >

---

## Task 3: Create a Launch Template

1. EC2 Console → **Launch Templates → Create launch template**.
   - **Name:** `lab-app-launch-template`
   - **Version description:** `A web server for the load test app`
   - **AMI:** `Web Server AMI`
   - **Instance type:** `t3.micro` (or fallback `t2.micro`).
   - **Security group:** `Web Security Group`.
2. Create template → Confirm success message.
   <img src= "compute\lab_app_launch_template.png" >

---

## Task 4: Create an Auto Scaling Group

1. Select the launch template → Actions → **Create Auto Scaling group**.
   - **Name:** `Lab Auto Scaling Group`.
   - **VPC:** `Lab VPC`.
   - **Subnets:** `Private Subnet 1` and `Private Subnet 2`.
2. Attach load balancer:
   - **Target group:** `lab-target-group | HTTP`.
   - **Health check type:** ELB.
3. Group size & scaling policy:
   - **Desired capacity:** 2
   - **Min:** 2, **Max:** 4
   - **Policy:** Target tracking (Average CPU utilization = 50%).
4. Add tag: `Name = Lab Instance`.
5. Create Auto Scaling group → Instances launch automatically.
   <img src= "compute\lab_target_group.png" >

---

## Task 5: Verify Load Balancing

1. EC2 Console → **Instances**: Confirm two new `Lab Instance` instances.
2. Load Balancer → **Target Groups**: Confirm both instances show **Healthy**.
3. Open the **DNS name** of the load balancer in a browser → Load Test app should appear.
   <img src= "compute\Lab_Instance_Health_status.png" >

---

## Task 6: Test Auto Scaling

1. Open **CloudWatch → Alarms → All alarms**.
   - Two alarms exist: `AlarmHigh` (CPU > 50%) and `AlarmLow`.
2. Generate load: In Load Test app → **Load Test**.
3. Monitor CloudWatch until:
   - `AlarmHigh` → **In alarm** state.
   - Auto Scaling adds new instances.
4. Confirm in EC2 Console: More than 2 instances running.
   <img src= "compute\Lab_Instances_running.png" >

---

## Task 7: Terminate Web Server 1

1. EC2 Console → Select **Web Server 1**.
2. Actions → **Instance state → Terminate instance**.  
   <img src= "compute\Web_Server_terminated.png" >

---

## Summary

This lab demonstrated how to build a **scalable and fault-tolerant architecture** on AWS by combining **Elastic Load Balancing, Auto Scaling, and CloudWatch monitoring**. The system:

- Ensures **high availability** by balancing requests across multiple AZs.
- Adapts to demand with **automatic scaling policies**.
- Reduces costs by **scaling down during low usage**.

## Challenges One Might Encounter

- **AMI Creation Delay**: AMIs can take time before becoming available.
- **Subnet Configuration Errors**: Using wrong subnet (public instead of private) may expose instances.
- **Security Group Misconfiguration**: If HTTP is blocked, load balancer won’t route traffic.
- **Instance Type Availability**: Some regions don’t support `t3.micro` → fallback to `t2.micro`.
- **Scaling Delay**: CloudWatch alarms may take a few minutes to trigger scaling actions, confusing first-time users.
- **DNS Propagation Lag**: Load balancer DNS might not resolve immediately after creation.
