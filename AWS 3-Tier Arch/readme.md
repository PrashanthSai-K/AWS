
# 🌐 Simple Web App with 3-Tier Architecture on AWS

### 🎯Objective :

- To setup a highly available and secure 3-tier architecture for a web application deployed across multiple Availability Zones (AZs) in the AWS Cloud and separates responsibilities into three distinct layers:

- Web (Frontend)

- Application (Backend)

- Data (Database)


### 🧱 Architecture Layers

#### 1️⃣ Web Tier (Frontend)

- Location: Public subnets in us-east-1a and us-east-1b

- Resources: EC2 instances running the web app

- Access:

    - Exposed to the internet through an Internet-facing Application Load Balancer (ALB)

    - Protected by a Security Group allowing HTTP/HTTPS traffic only

    - Scalability: Can be placed behind Auto Scaling Group for elasticity

#### 2️⃣ App Tier (Backend)

- Location: Private subnets in both AZs

- Resources: EC2 instances running backend logic (APIs, business logic)

- Access:

    - Traffic comes only from the frontend layer through the Backend Internal Load Balancer (ALB)

    - Secured via Security Group rules
 
    - Communication: Sends/receives data to/from the Database Layer

#### 3️⃣ Database Tier

- Location: Private subnets

- Resources:

    - Primary database in one AZ

    - Standby (replica) database in another AZ for failover

- Access:

    - Only accessible from the App Layer via security group rules

    - No public internet access

- High Availability: Achieved using Amazon RDS Multi-AZ deployments or manually configured replication

#### 🔐 Security Architecture

- Security Groups control access between layers:

- Web SG → allows internet → ALB → web app

- Web App SG → allows LB traffic → App Server

- App SG  → Database

- Internet Gateway is attached only to the public subnet

- Private Subnets ensure App and DB layers are not internet-accessible

#### 📈 Scalability & Redundancy

- Use Auto Scaling Groups for both Web and App layers

- Load Balancers distribute traffic evenly across AZs

- Multi-AZ deployment ensures fault tolerance and high availability


### 📌 Output

