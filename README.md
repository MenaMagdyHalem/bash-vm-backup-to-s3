# Using a Bash Script and Scheduling to Automate Virtual Machine Data Backup & Replication To An Amazon S3 Bucket

## 🧠 Overview
This project demonstrates how to automate data backup and replication from an EC2 instance (or any Linux VM) to Amazon S3, using a Bash script, cron scheduling, and the AWS CLI.
It’s a real-world DevOps-style automation that ensures critical data is securely compressed, logged, and replicated to the cloud.

---

## ⚙️ Key Features

✅ Automated Backups – Schedule periodic backups (daily, weekly, etc.) using cron. <br>
✅ Compression – Use tar and gzip to minimize backup size. <br> 
✅ Logging – Every operation (start, success, error) is logged to logfile.log. <br>
✅ AWS Integration – Upload backup files securely to an Amazon S3 bucket. <br>
✅ Error Handling – Validations for missing directories, AWS CLI, etc. <br>

---

## 🧩 Prerequisites

Before running the script: <br>
An AWS account with: <br> 
IAM user or IAM role with permissions: <br>
`AmazonS3FullAccess` and `AmazonSSMFullAccess` <br>

AWS CLI installed and configured:
```bash
aws configure
```
Linux-based VM (e.g., Ubuntu EC2 instance)

---












