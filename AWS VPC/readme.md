
# 🛡️ AWS VPC

### 🎯Objective :

- To build a Structure of a custom AWS VPC for learning and experimentation with a highly available 3-tier architecture using public and private subnets, route tables, and network connections like Internet Gateway (IGW) and NAT Gateway.

### 🌐 VPC Overview

- VPC Name: my-vpc

- Region: us-east-1

- Availability Zones Used: us-east-1a, us-east-1b

### 🏗️ Subnet Structure

| Subnet Type   | Subnet Name                   | AZ          |
|---------------|-------------------------------|-------------|
| Public Subnet | my-subnet-public1-us-east-1a  | us-east-1a  |
| Public Subnet | my-subnet-public2-us-east-1b  | us-east-1b  |
| Private Subnet| my-subnet-private1-us-east-1a | us-east-1a  |
| Private Subnet| my-subnet-private2-us-east-1b | us-east-1b  |


### 🛣️ Route Tables

| Route Table Name| Associated Subnets| Purpose|
|-----------------|------------------|---------|
| my-rtb-public| Public subnets| Internet access via IGW|
| my-rtb-private1-us-east-1a| Private subnet in AZ us-east-1a| NAT access via NAT Gateway|
| my-rtb-private2-us-east-1b   | Private subnet in AZ us-east-1b| NAT access via NAT Gateway (shared or additional)|
| rtb-03d05107f61fe121e| Unused or placeholder |Internet access via IGW|

### 🔌 Network Connections

| Name| Type| Description|
|-----|-----|------------|
| my-igw| Internet Gateway | Enables internet access for public subnets|
| my-nat-public1-us-east-1a | NAT Gateway| Allows private subnets to access the internet|


### 🔄 Flow Explanation

#### 🌍 Public Subnets

- Associated with my-rtb-public

- Default route (`0.0.0.0/0`) points to Internet Gateway

- Used for:

    - Load Balancers

    - Bastion hosts

    - NAT Gateway

#### 🔐 Private Subnets

- Associated with individual private route tables (`my-rtb-private1-us-east-1a`, `etc`.)

- Route internet traffic (`0.0.0.0/0`) to NAT Gateway

- Used for:

    - Application servers

    - Databases

    - Internal services

### 📌 Output

![Screenshot 2025-04-22 160923](https://github.com/user-attachments/assets/42341eaa-ce61-4c72-9188-0a8fc66be3b2)
