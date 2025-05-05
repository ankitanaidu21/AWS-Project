#Highly Available and Scalable 3-Tier Web Application on AWS
Day 1: AWS Networking Setup

1. Create an IAM User and attach the AdministratorAccess policy for Administrator Access
   Log out from the root user, then log in using the Administrator user.
2. Select VPC from the service menu.
3. Create a Custom VPC:
     Go to VPC Dashboard → Your VPCs → Create VPC.
     Name: my-vpc
     IPv4 CIDR Block: 10.0.0.0/16
     Tenancy: Default
4. Enable DNS Resolution and Hostnames:
    With your newly created VPC selected, click Actions → Edit DNS Resolution and Hostnames.
    Enable both DNS Resolution and DNS Hostnames to allow proper DNS functionality.
5. Create Subnets:
    Create 4 subnets within the VPC, across 2 Availability Zones (AZs). Make sure to enable Auto Assign Public IP for Public Subnets.
    Public Subnet A → 10.0.0.0/24 → AZ1
    Private Subnet A → 10.0.1.0/24 → AZ1
    Public Subnet B → 10.0.16.0/24 → AZ2
    Private Subnet B → 10.0.32.0/24 → AZ2
5. Attach an Internet Gateway (IGW) to the VPC:
    Create an Internet Gateway and attach it to your VPC. (Note: Simply attaching an IGW does not provide internet access to your instances until route tables are updated.)
6. Configure the NAT Gateway for Private Subnet Internet Access:
   To save cost, create a NAT gateway in only one Availability Zone.
   NAT Gateway Creation Steps:
    Click Create NAT Gateway.
    Name: App-nat-gateway (or your preferred name).
    Subnet: Select a public subnet (since it needs internet access).
    Allocate Elastic IP and click Create NAT Gateway.
7. Create and Configure Route Tables:
   Public Route Table:
     Go to VPC → Route Tables → Create Route Table.
     Name: public-rt, select your VPC.
     Go to Subnet Associations and select your public subnets.
     Add Route: 0.0.0.0/0 → Target: Internet Gateway.
   Private Route Table:
    Create a route table named private-rt and select your VPC.
    Go to Subnet Associations and select your private subnets.
    Add Route: 0.0.0.0/0 → Target: NAT Gateway.

   
Summary of Current Configuration:
VPC: my-vpc with CIDR 10.0.0.0/16.
Subnets:
2 Public Subnets in AZ1 and AZ2.
2 Private Subnets in AZ1 and AZ2.
Internet Gateway (IGW): Attached for public internet access.
NAT Gateway: Created in one AZ for private subnet internet access.
Route Tables:
Public Route Table: Routes traffic to the IGW for public subnets.
Private Route Table: Routes traffic to the NAT Gateway for private subnets.


The environment configured so far is as follows.
	
![image](https://github.com/user-attachments/assets/0a6d86b5-fb04-41ce-9b9c-efcd5618bbce)

