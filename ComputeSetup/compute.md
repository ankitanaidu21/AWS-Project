Day 2 : Compute Setup

Part 1: Launch Web Server with User Data

		• Launch EC2 instance in a public subnet with HTTP and SSH access using user data(userdata.md).
		• Verify setup by accessing the instance via its Public DNS or IPv4 address in a browser.
		• Access instance using SSH or Session Manager (create IAM role for Systems Manager).

Part 2: Create Custom AMI

	• Create an image of the configured web server instance.
	• After the AMI is available, terminate the original instance

Part 3: Configure Application Load Balancer

	• Create an internet-facing ALB.
	• Select VPC and 2 public subnets created in Day 1.
	• Create a security group (Web-ALB-SG) with inbound HTTP access from Anywhere (IPv4).
	• Create a target group (Web-TG) with type Instances, no registered targets.
	• Finalize and launch the ALB.

Part 4: Configure Launch Template

	• Create a security group (ASG-Web-Inst-SG) allowing HTTP traffic only from the ALB.
	• Create a launch template:
		• Use the custom AMI
		• Select instance type, SG, and IAM instance profile (SSMInstanceProfile).

Part 5: Set Up Auto Scaling Group

	• Create an Auto Scaling Group using the launch template and private subnets.
	• Attach it to the existing ALB.
	• Enable CloudWatch group metrics collection.
	• Set group size:
		• Desired/Min = 2, Max = 4
		• Add target tracking policy for 30% average CPU utilization
	• Create the ASG.

You successfully deployed a scalable and highly available web service using an Application Load Balancer, security groups, launch template, and Auto Scaling group.

Part 6: Test Web Service

	• Verify if ALB distributes traffic correctly to instances in Auto Scaling Group.
	• Confirm scaling behaviour by simulating CPU load or changing configuration manually.

Architecture Configured So Far

Now, we've built a web service that is high available and automatically scales under load! The configuration of the services we have created so far is as follows.


<img width="726" alt="image" src="https://github.com/user-attachments/assets/bf3eeec3-89db-456b-9eaa-5b1f81ab7aab" />




