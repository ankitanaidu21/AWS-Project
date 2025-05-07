Day 1: AWS Networking Setup
	1. In your root AWS Account, Create an IAM user and attach Administrator Access policy.
	2. Log out from the root user and then log in to the Administrator user.
	3. After logging in to the AWS console, select VPC from the service menu.
	4. Create a Custom VPC with 2 Public and 2 Private Subnets (across 2 AZs).
	5. Go to VPC Dashboard → Your VPCs → Create VPC
		• Name: my-vpc
		• IPv4 CIDR: 10.0.0.0/16
		• Tenancy: Default
	6. Enable DNS Support and Hostnames:
	With your VPC selected, click Actions → Edit DNS Resolution and Hostnames
	7. Create 4 Subnets, Select VPC ID which we created. Enable Auto Assign Public IP settings for Public Subnets.
		• Public Subnet A   → 10.0.0.0/24 → AZ1
		• Private Subnet A  → 10.0.1.0/24 → AZ1
		• Public Subnet B   → 10.0.16.0/20 → AZ2
		• Private Subnet B  → 10.0.32.0/24 → AZ2
	8. Create and attach an Internet Gateway to your VPC. (Note: IG on their own do not allow internet access,
	we must edit Route tables)
	Note: You can use a NAT gateway so that instances in your private subnets can connect to services outside your VPC, but external services cannot initiate direct connections to these instances
	9. Create a NAT gateway in only one Availability Zone to save cost.
	NAT Gateway
		1. Click Create NAT Gateway
		2. Name: e.g., App-nat-gateway
		3. Subnet: Select a public subnet (because it needs internet access)
		4. Allocate Elastic IP
		5. Click Create NAT Gateway.
	10. Create Public Route table and Private Route.
	Public Route Table:
		1. Go to VPC → Route Tables → Create
		2. Name: public-rt, select your VPC
		3. Go to Subnet Associations → select your public subnets
		4. Add route: 0.0.0.0/0 → Target: Internet Gateway
	Private Route Table:
		1. Create private-rt, select your VPC
		2. Go to Subnet Associations → select your private subnets
		3. Add route: 0.0.0.0/0 → Target: NAT Gateway
	
The environment configured so far is as follows.

![image](https://github.com/user-attachments/assets/ea0dc38f-bc49-4bb6-a9a3-01ed45ad30c5)



