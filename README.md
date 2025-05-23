# Terraform AWS WebStack

## 🚀 Overview

This project provisions a complete web infrastructure stack on AWS using Terraform. It includes:

- An EC2-based web server (Apache) with Git integration
- Amazon EFS for persistent shared storage
- Amazon S3 for object storage and image hosting
- Amazon CloudFront for global CDN distribution
- Dynamic rendering of an S3 image on the EC2-hosted webpage
- Fully automated infrastructure provisioning with remote and local executors

Designed to showcase Infrastructure as Code (IaC), automation, and multi-service AWS integration.

---

## 🛠️ Technologies Used

- **Terraform** for Infrastructure as Code
- **Amazon EC2** for web server
- **Amazon EFS** for shared file storage
- **Amazon S3** for object storage
- **Amazon CloudFront** for content delivery
- **Null Resource + Remote Exec** for provisioning logic
- **Local Exec** to test endpoint output

---

## 📦 Project Structure

```
.
├── ec2.tf               # EC2 instance and provisioning
├── efs.tf               # EFS volume and mount
├── s3.tf                # S3 bucket and object upload
├── cloudfront.tf        # CloudFront CDN configuration
├── remote_config.tf     # CloudFront image rendering logic
├── null_exec.tf         # Local exec for curl output
├── variables.tf         # Input variables (if applicable)
├── outputs.tf           # Output values
└── README.md
```

---

## 🔧 How It Works

1. **Creates a Security Group** to allow SSH and HTTP traffic.
2. **Launches an EC2 instance** using an Amazon Linux 2 AMI.
3. **Installs Apache and Git** on the instance.
4. **Creates an EFS volume**, mounts it to `/var/www/html`.
5. **Clones a GitHub repo** into the mounted EFS directory.
6. **Creates an S3 bucket** and uploads an image.
7. **Deploys a CloudFront distribution** for global access to the S3 image.
8. **Renders the CloudFront image** inside the EC2's `index.html`.
9. **Tests the endpoint** via local curl request.

---

## ✅ Prerequisites

- AWS CLI configured (`aws configure`)
- Terraform installed
- A valid AWS key pair (`.pem` file path correctly set in your code)
- Access to a VPC and subnet matching the instance's config

---

## 🚨 Security Notes

- The SSH port (22) is open to `0.0.0.0/0`. Change this in production.
- Your `.pem` file should be stored securely and **never committed** to Git.
- Make sure the S3 bucket name (`mybucket41`) is globally unique.

---

## 📸 Result

Once deployed, visit:
```
http://<ec2-public-ip>
```
You will see an Apache-hosted web page displaying an image hosted on S3, served through CloudFront.

---

## 📃 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## 🙋‍♂️ Author

**Sai Jayanth Rajamahendram**  
Cloud | DevOps | Infrastructure as Code  
[LinkedIn](https://www.linkedin.com/in/saijayanthraj/) | [GitHub](https://github.com/saijayanth41)
