# Day 3: Database Setup

We will deploy an RDS Aurora (MySQL) instance in our VPC and configure a web service (Apache + PHP) in an Auto Scaling Group to use the database.

For production workloads, it is recommended to:
- Enable high availability and fault tolerance using **read replicas** in different Availability Zones.
- Deploy databases in a private subnet of a VPC for better **security** and network isolation.

# Tasks

Create VPC Security Group
Create RDS Instance
Connect RDS with Web App Server
Access RDS from EC2
RDS Management Features
Connect to RDS Aurora

Refer to:

database.md for detailed step-by-step instructions.
