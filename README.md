# AWS-Project
This repository provides a step-by-step guide for deploying a scalable and fault-tolerant 3-tier web application architecture on Amazon Web Services (AWS). 

## 🚀 Day 1: AWS Networking Setup

Set up the foundational networking environment in AWS using a custom VPC.

### ✅ Steps:
1. Create an IAM user with admin access and log in.
2. Launch a custom VPC (10.0.0.0/16) with DNS resolution and hostnames enabled.
3. Create 2 public and 2 private subnets across two Availability Zones.
4. Attach an Internet Gateway and set up a NAT Gateway.
5. Create and associate route tables with correct routes.
6. Verify the architecture using the diagram: `AWSNetworkSetup.jpeg`

📘 Refer to [NetworkSetup/network.md] for step-by-step instructions.

---

## 💻 Day 2: Compute Setup

Launch EC2 web servers, configure an Auto Scaling Group, and set up load balancing.

### ✅ Tasks:
- Launch EC2 instances with user data scripts.
- Configure a security group.
- Create a custom Amazon Machine Image (AMI).
- Set up an Application Load Balancer (ALB).
- Create a Launch Template.
- Configure an Auto Scaling Group.
- Test and update scaling behavior.

📘 Refer to [ComputeSetup/compute.md] for detailed guidance.

---

## 🛢️ Day 3: Database Setup

Deploy an Amazon RDS Aurora (MySQL) instance and integrate it with the web application.

### ✅ Best Practices:
- Enable **high availability** using read replicas across AZs.
- Place databases in a private subnet** for security.

### ✅ Tasks:
- Create a VPC security group for RDS.
- Launch and configure the RDS Aurora instance.
- Connect RDS to the web application.
- Access RDS via an EC2 instance using MySQL client.
- Explore RDS management features.

📘 Refer to [DatabaseSetup/database.md] for step-by-step instructions.
