Day 3: Database Setup 

Goal: Deploy RDS Aurora (MySQL) in VPC-Lab.

Create DB Security Group
	1. Use ASG-Web-Inst-SG (from EC2 lab) for web servers.
	2. Create a new SG named DB-SG in VPC.
	3. In Inbound rules, set Type: MySQL/Aurora, port 3306.
	4. Set Source to ASG-Web-Inst-SG.

Create RDS Instance
	1. Go to AWS Console → RDS.
	2. Click Create Database.
	3. Choose Amazon Aurora (MySQL Compatible).
	4. Select Standard Create, Select Engine type: eg: Aurora (MySQL 5.7) 2.11.4.
	5. Choose Production template.
	6. Under Settings, set:
		○ DB Cluster Identifier
		○ Master Username
		○ Master Password
	7. Choose Memory Optimized class.
Availability: Create Aurora Replica in another AZ.
Type: eg: db.r5.large
	8. On Connectivity, select VPC-Lab, private subnet, no public access, add security groups.
	9. In Additional Configuration, set DB name.
	10. Leave Backup, Monitoring, etc. as default. Click Create Database.
	11. Wait until status shows Available.

Note: For production workloads, it is a best practice to enable high availability and fault tolerance by creating read replicas in different Availability Zones. It is a best practice to deploy databases within a private subnet of a VPC for better security and network isolation.

The configuration of the services we have created so far is as follows.

<img width="986" alt="image" src="https://github.com/user-attachments/assets/eb4bd7bd-ae07-4465-aa43-b5f3d4c2a013" />

