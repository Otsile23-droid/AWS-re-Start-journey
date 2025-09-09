# Lab: Logging and Monitoring with CloudWatch & SNS

## Overview

In this lab, you implement logging and monitoring on an EC2 instance using Amazon CloudWatch and Amazon Simple Notification Service (SNS). You create a CloudWatch alarm that triggers when CPU utilization crosses a defined threshold. When triggered, the alarm sends an SNS notification email. You also test the alarm by stressing the CPU of the EC2 instance and finally create a CloudWatch dashboard for monitoring.

## Objectives

After completing this lab, you should be able to:

- Create an Amazon SNS topic and subscription for email notifications
- Configure a CloudWatch alarm based on EC2 CPU utilization metrics
- Stress test an EC2 instance to trigger the alarm
- Confirm that an SNS email notification is sent
- Build a CloudWatch dashboard to monitor CPU utilization

## Steps

### Step 1: Create an SNS Topic and Subscription

1. Open **Amazon SNS** in the console.
2. Create a **Standard topic** named `MyCwAlarm`.
3. Create a subscription for the topic with:
   - Protocol: `Email`
   - Endpoint: Your valid email address
4. Confirm the subscription by clicking the link in the email.

<img src= "security\SNS.png" >
✅ At this point, SNS is ready to send notifications.

### Step 2: Create a CloudWatch Alarm

1. In the **CloudWatch console**, go to **Metrics → EC2 → Per-Instance Metrics**.
2. Select **CPUUtilization** for the `Stress Test` EC2 instance.
3. Create a new alarm:
   - Threshold: **Greater than 60%**
   - Period: **1 minute**
   - Action: Send notification to `MyCwAlarm` SNS topic
   - Name: `LabCPUUtilizationAlarm`

<img src= "security\Alarm.png" >
✅ The alarm is now set to trigger when CPU utilization > 60%.

### Step 3: Test the Alarm

1. Connect to the `Stress Test` EC2 instance.
2. Run a CPU stress test
   Return to CloudWatch → Alarms. Within a few minutes, the alarm should switch to In Alarm state.
3. Check your email inbox for a notification from SNS.

<img src= "security\Stress Test.png" >
<img src= "security\SNS Alarm.png" >
✅ The alarm has been successfully tested.

## Step 4: Create a CloudWatch Dashboard

1. In the CloudWatch console, go to Dashboards → Create dashboard.
2. Name it LabEC2Dashboard.
3. Add a Line widget displaying CPUUtilization for the Stress Test instance.
4. Save the dashboard.

<img src= "security\CloudWatch Dashboard.png" >
✅ You now have a quick view of EC2 CPU utilization.

## Challenges You Might Encounter

- Delayed metrics: CloudWatch can take 5–10 minutes to start reporting EC2 metrics after launch.
- Subscription not confirmed: If you miss the SNS confirmation email, no notifications will be delivered.
- Threshold misconfiguration: Setting the wrong threshold (e.g., too high or too low) may cause missed alarms or unnecessary alerts.
- Email delivery issues: Notifications may land in spam/junk folders.
- Dashboard not updating: Forgetting to refresh or save can result in empty widgets.
