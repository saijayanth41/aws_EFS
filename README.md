# 🌐 Ansible + Terraform Project: Web Server Deployment on AWS

## 📋 Overview

This project automates the provisioning and configuration of an Apache Web Server on an AWS EC2 instance using **Terraform**. It integrates services like **Amazon EFS**, **S3**, and **CloudFront**, and utilizes **Ansible-style provisioning** through Terraform `remote-exec` to install required software and customize the server.

---

## 🛠️ Key Features

- ✅ Provision EC2 instance with Apache and Git pre-installed
- ✅ Create and apply Security Group with HTTP/SSH access
- ✅ Mount and use Amazon EFS as web root (`/var/www/html`)
- ✅ Clone a GitHub repo directly into the web root
- ✅ Upload an image to an S3 bucket and serve it via CloudFront CDN
- ✅ Auto-generate an HTML snippet with CloudFront URL
- ✅ Output webpage using curl via `local-exec`

---

## 🔧 Technologies Used

- **Terraform** (Infrastructure as Code)
- **AWS EC2, EFS, S3, CloudFront**
- **Provisioners** (remote-exec, local-exec)
- **Amazon Linux 2 AMI**
- **Bash scripting inside Terraform blocks**

---

## 📦 Infrastructure Components

| Resource                | Details                                      |
|------------------------|----------------------------------------------|
| **VPC**                | Uses existing VPC ID                         |
| **EC2 Instance**       | t2.micro with key pair `saikey`             |
| **Security Group**     | Allows inbound HTTP (80) and SSH (22)       |
| **EFS**                | Mounted to `/var/www/html`                  |
| **S3 Bucket**          | Public-read, image upload included          |
| **CloudFront**         | Delivers S3 image globally                  |

---

## 📁 Project Structure

```bash
.
├── main.tf                 # Main Terraform configuration
├── saikey.pem             # SSH private key (local)
├── awsefs.jpg             # Image file to be uploaded to S3
└── README.md              # Project documentation (this file)
