# Networking-In-AWS
This project outlines a group activity focused on AWS networking concepts and tools. The team learned how to create a Virtual Private Cloud (VPC), public and private subnets, an internet gateway, a route table, and a security group, and how to launch two EC2 instances within this network setup.
Key AWS Components and Tasks

AWS Networking & EC2 Setup
This repository contains a step-by-step guide for setting up a basic network infrastructure in Amazon Web Services (AWS). It covers creating a Virtual Private Cloud (VPC), configuring subnets, setting up an Internet Gateway and route tables, and launching two EC2 instances to test connectivity.

# Task 1: Create a VPC and Subnets
The first step is to establish an isolated network environment within AWS.

Steps:
Create VPC:

Navigate to the VPC Service and select Your VPCs.

Click Create VPC.

Set Name tag to my-group-vpc.

Provide an IPv4 CIDR block (e.g., 10.0.0.0/16).

Click Create VPC.

Create Subnets:

In the VPC Dashboard, click on Subnets.

Create Subnet 1:

Click Create subnet.

Choose the VPC you just created.

Select an Availability Zone (e.g., us-east-1a).

Name the subnet Subnet-1.

Set the Subnet CIDR block (e.g., 10.0.1.0/24).

Click Create subnet.

Create Subnet 2:

Repeat the steps above to create a second subnet.

Choose the same VPC.

Select a different Availability Zone (e.g., us-east-1b).

Name the subnet Subnet-2.

Set the Subnet CIDR block (e.g., 10.0.2.0/24).

Click Create subnet.

# Task 2: Security Groups and Routing
Next, we configure how traffic flows into and out of our VPC and its subnets.

Steps:
Create an Internet Gateway (IGW):

In the VPC Dashboard, click Internet Gateways.

Click Create internet gateway, give it a name like MyInternetGateway, and click Create.

After creation, attach it to your VPC.

Configure Routing:

Go to Route Tables in the VPC Dashboard.

Click Create route table, name it PublicRouteTable, and select your VPC.

Select the new route table and click the Routes tab, then Edit routes.

Add a route for 0.0.0.0/0 and set the Target to the Internet Gateway you created.

Click Save changes.

Associate Route Table with Subnets:

Click on the Subnet associations tab.

Click Edit subnet associations, select both of your new subnets, and Save.

Create a Security Group:

Go to Security Groups in the VPC Dashboard.

Click Create security group.

Name it AllowSSH and select your VPC.

Under Inbound rules, add a new rule:

Type: SSH

Source: 0.0.0.0/0 (for demonstration purposes, restrict this for production)

Leave outbound rules as the default.

Click Create security group.

# Task 3: Launching EC2 Instances
Now we will launch two virtual servers within our new network.

Steps:
Launch EC2 Instance in Subnet-1:

Go to the EC2 Dashboard and click Launch Instance.

Choose an AMI (e.g., Amazon Linux 2) and an instance type (t2.micro).

In the Network settings, select your VPC.

For Subnet, choose Subnet-1.

Select the AllowSSH Security Group.

Choose or create a key pair.

Click Launch instance.

Launch EC2 Instance in Subnet-2:

Repeat the steps above, but this time, select Subnet-2 for the subnet.

Task 4: Testing and Validation
Finally, we test our network setup by connecting to the public instance.

Steps:
Once both EC2 instances are running, locate the public IP address of the instance launched in Subnet-1.

Open your terminal and use the following command to connect, replacing the placeholder values with your key pair file and public IP address:

ssh -i /path/to/your-key-pair.pem ec2-user@your-public-ip-address

Troubleshoot any connectivity issues, such as security group rules or key pair permissions.

