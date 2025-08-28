# EC2 Lab Example: Launching and Managing Instances

## Objectives

- Launch EC2 instance with termination protection
- Modify security group for HTTP access
- Monitor instance
- Resize instance
- Test termination protection
- Terminate instance

## Steps (Summary)

1. Launched Amazon Linux 2 EC2 instance with termination protection enabled
2. Modified security group → added inbound rule for HTTP (port 80)
3. Verified access via browser
4. Monitored CPU & status checks in CloudWatch
5. Stopped and resized instance type
6. Disabled termination protection, then terminated instance

## Diagram

![EC2 Lab Architecture](compute\EC2-lab architecture.png)

## Key Takeaways

- EC2 instances can be scaled and protected from accidental termination
- Security groups define inbound/outbound rules
- Monitoring is built-in via CloudWatch
- Resize is flexible but requires stopping the instance
