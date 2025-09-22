# Creating a Website on S3

## Lab Overview

In this lab, you practice using **AWS Command Line Interface (AWS CLI)** commands from an Amazon Elastic Compute Cloud (Amazon EC2) instance to:

- Create an **Amazon Simple Storage Service (Amazon S3)** bucket
- Create a new **AWS Identity and Access Management (IAM)** user with full S3 access
- Upload files to Amazon S3 to host a simple website for the **Café & Bakery**
- Create a **batch file** for automated website updates

This lab demonstrates how to deploy static websites using S3, configure proper permissions, and automate deployment processes using AWS CLI.

---

<img src= "https://github.com/Otsile23-droid/AWS-re-Start-journey/blob/63b68a78a2d60748eda4f4bd5305b992cf580541/storage/screenshots/architecture.png" >

## Objectives

By the end of this lab, you will be able to:

- Run **AWS CLI commands** that use IAM and Amazon S3 services
- Deploy a **static website** to an S3 bucket
- Create a **script** that uses AWS CLI to copy files from local directory to Amazon S3
- Configure **S3 bucket permissions** for public website hosting
- Implement **automation** for repeatable deployments

---

## Task 1: Connect to Amazon Linux EC2 Instance

1. Choose the **Details** button at the top, then choose **Show**
2. Copy the **InstanceSessionUrl** value and paste into a new browser tab
3. A console connection is made using **AWS Systems Manager Session Manager**
4. Run the following commands to switch user and verify home directory:

---

## Task 2: Configure the AWS CLI

Amazon Linux instances come with AWS CLI pre-installed.

1. Run the configure command to update AWS CLI with credentials:
2. Configure the following at the prompts:
   - **AWS Access Key ID**: [Copy from lab credentials]
   - **AWS Secret Access Key**: [Copy from lab credentials]
   - **Default region name**: `us-west-2`
   - **Default output format**: `json`

---

## Task 3: Create an S3 Bucket Using AWS CLI

1. Create a uniquely named S3 bucket (example: `otkeem232`):
2. **Success response** (JSON format):

**Note**: The bucket name must be globally unique. Use your initials + random numbers.

 <img src= "https://github.com/Otsile23-droid/AWS-re-Start-journey/blob/63b68a78a2d60748eda4f4bd5305b992cf580541/storage/screenshots/creating_an_S3_bucket_using_AWS%20CLI.png" >

## Task 4: Create New IAM User with Full S3 Access

1. Create a new IAM user:

```bash
aws iam create-user --user-name awsS3user
```

2. Create login profile with password:

```bash
aws iam create-login-profile --user-name awsS3user --password Training123!
```

3. Find the AWS managed policy for S3 full access:

```bash
aws iam list-policies --query "Policies[?contains(PolicyName,'S3')]"
```

4. Attach the **AmazonS3FullAccess** policy to the user:
   <img src= "https://github.com/Otsile23-droid/AWS-re-Start-journey/blob/63b68a78a2d60748eda4f4bd5305b992cf580541/storage/screenshots/attaching_policy_to_the_user.png" >
5. **Test the new user**:
   - Copy the 12-digit Account ID from AWS Console
   - Sign out of current session
   - Log in as **IAM user** with Account ID, username `awsS3user`, and password `Training123!`

---

## Task 5: Adjust S3 Bucket Permissions

1. In **S3 Console → Your Bucket → Permissions**:
   - **Block public access**: Edit → **Uncheck** "Block all public access" → Save
   - **Object Ownership**: Edit → Choose **ACLs enabled** → Acknowledge → Save

---

## Task 6: Extract Website Files

1. Navigate to the lab files directory:
2. **Expected files**: `index.html`, `css/` directory, `images/` directory

<img src= "https://github.com/Otsile23-droid/AWS-re-Start-journey/blob/63b68a78a2d60748eda4f4bd5305b992cf580541/storage/screenshots/extracting_web_files.png" >

## Task 7: Upload Files and Configure Website Hosting

1. Configure bucket for static website hosting:
2. Upload website files with public read access:
3. Verify upload

<img src= "https://github.com/Otsile23-droid/AWS-re-Start-journey/blob/63b68a78a2d60748eda4f4bd5305b992cf580541/storage/screenshots/uploading_files.png" >

4. **Test the website**:
   - Go to S3 Console → Your Bucket → Properties → Static website hosting
   - Click the **Bucket website endpoint URL**
   - **Result**: Café & Bakery website should display

<img src= "https://github.com/Otsile23-droid/AWS-re-Start-journey/blob/63b68a78a2d60748eda4f4bd5305b992cf580541/storage/screenshots/cafe_%26_bakery_website.png" >

---

## Task 8: Create Automated Deployment Script

1. View command history to find the upload command:
2. Create the automation script:
3. Add the following content (press `i` to edit):
4. Save and exit: `Esc` → `:wq` → `Enter`
5. Make executable

<img src= "https://github.com/Otsile23-droid/AWS-re-Start-journey/blob/63b68a78a2d60748eda4f4bd5305b992cf580541/storage/screenshots/automated_deployment_script.png" >

---

## Task 9: Test Website Updates

1. Edit the website styling:

```bash
vi sysops-activity-files/static-website/index.html
```

2. Make the following changes (press `i` to edit):

   - Change `bgcolor="aquamarine"` to `bgcolor="gainsboro"`
   - Change `bgcolor="orange"` to `bgcolor="cornsilk"`

3. Save changes: `Esc` → `:wq` → `Enter`

4. **Deploy updates** using your script:

```bash
./update-website.sh
```

5. **Verify changes**: Refresh the Café & Bakery website to see updated colors

<img src= "https://github.com/Otsile23-droid/AWS-re-Start-journey/blob/63b68a78a2d60748eda4f4bd5305b992cf580541/storage/screenshots/updated_website.png" >

---

## Summary

This lab demonstrated how to build a **complete static website deployment pipeline** on AWS by combining **S3, IAM, and AWS CLI automation**. The system provides:

- **Cost-effective hosting** for static websites
- **Automated deployment** through custom scripts
- **Proper security configuration** with IAM users and policies
- **Public accessibility** with appropriate permissions

## Challenges One Might Encounter

- **Bucket Naming Conflicts**: S3 bucket names must be globally unique across all AWS accounts
- **Permission Errors**: Forgetting to set `--acl public-read` results in access denied errors
- **IAM Policy Delays**: New IAM permissions may take a few minutes to propagate
- **Website Endpoint Confusion**: Using S3 object URL instead of website endpoint URL leads to file downloads instead of webpage display
- **File Path Issues**: Incorrect local file paths in upload commands cause "file not found" errors
- **Static Website Setting**: Forgetting to enable static website hosting prevents proper webpage rendering
