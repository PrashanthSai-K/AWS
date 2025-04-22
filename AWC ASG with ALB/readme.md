
# ⚙️ AWS Auto Scaling Group with Application Load Balancer (ALB)

### 🎯Objective :

- Setup of a high availability architecture on AWS using EC2, ALB, and Auto Scaling Group (ASG) across multiple Availability Zones (AZs) in a single VPC.

### 📌 Architecture Summary

- Region: us-east-1

- AZs: us-east-1a & us-east-1b

- Subnets: 2 public subnets

- Load Balancer: Application Load Balancer (ALB)

- Compute: Auto Scaling Group (ASG) with EC2 instances

- Security Group: Applied to ASG/ALB for controlled access

- Internet Access: Through Internet Gateway


### 🔧 Components Breakdown

### ✅ VPC
Custom VPC with subnets deployed in multiple availability zones for high availability.

#### 🌐 Public Subnets
- Public Subnet - us-east-1a

- Public Subnet - us-east-1b

- Used to host:

    - ALB (for distributing traffic)

    - EC2 instances (part of the ASG)
  
#### 🔀 Application Load Balancer (ALB)

- Placed in front of the ASG

- Accepts HTTP/HTTPS traffic

- Distributes traffic evenly across healthy EC2 instances in both AZs

#### ⚙️ Auto Scaling Group (ASG)

- Automatically manages EC2 instances

- Launches instances in both AZs

- Automatically replaces unhealthy instances

- Scales in/out based on defined metrics (e.g., CPU utilization)

#### 🧱 EC2 Instances

- Hosted in the public subnets

- Managed by the ASG

- Serve application traffic routed by ALB

#### 🔒 Security Groups

- ALB Security Group: Allows inbound HTTP/HTTPS from the internet

- EC2 Security Group: Allows inbound traffic from the ALB only

#### ☁️ Internet Gateway

- Enables outbound traffic from public subnets to the internet
 

### 📌 Output

![ASG with ALB](https://github.com/user-attachments/assets/9e2b1eb6-d21b-4da8-8e31-b2298fa352ed)

