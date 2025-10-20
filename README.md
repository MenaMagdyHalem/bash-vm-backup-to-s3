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

## Steps
## 1️⃣ Create Sample Files and Directories
```bash
mkdir ~/bash
touch ~/bash/file{1..10}

mkdir ~/backup
touch ~/backup/logfile.log
```

## 2️⃣ Create the Backup Script

Create a file named `backup-script.sh`

Make it executable:
```bash
chmod +x backup-script.sh
```

## 3️⃣ Test the Script

Run manually:
```bash
./backup-script.sh
```

Expected output:
```bash
Backup completed successfully. Backup file: /home/ubuntu/backup/file-backup-09-18-23_15_22_20.tar.gz
upload: backup/file-backup-09-18-23_15_22_20.tar.gz to s3://s3-new-bash-course/...
File uploaded successfully to S3 bucket: s3-new-bash-course
```

## 4️⃣ Automate with Cron

Edit crontab:
```bash
sudo vim /etc/crontab
```

Add this line to run every 2 minutes:
```bash
*/2 * * * * root /home/ubuntu/backup-script.sh
```

Now the script will run automatically every 2 minutes, backup your data, and upload it to S3.

## 5️⃣ Verify the Backup

List backups locally:
```bash
ls /home/ubuntu/backup
```

List backups on S3:
```bash
aws s3 ls s3://s3-new-bash-course/
```

View the log file:
```bash
cat /home/ubuntu/backup/logfile.log
```
--- 

## 🧰 Tools Used

* Bash scripting
* AWS CLI
* Amazon S3
* cron (Linux scheduling)
* tar + gzip

---

## 📘 Learning Outcomes

By completing this project, you’ll learn how to:
* Automate tasks with Bash and cron
* Integrate AWS CLI with Linux automation
* Manage and upload compressed backups to S3
* Implement logging and error handling in scripts


## 🧑‍💻 Author
Mena Halem <br>
DevOps Instructor | Cloud & Linux Specialist













