# Multi-Tier-Web-Application-on-AWS-Fault-Tolerant-Architecture<br><br>

# Introduction

## Overview:
- This project involves designing, deploying, and managing a multi-tier web application using Amazon Web Services (AWS) that is highly available, scalable, and fault-tolerant.
- The architecture is structured to handle increased traffic seamlessly by scaling up resources dynamically and ensuring zero downtime through fault-tolerant mechanisms.

## Objectives:
- Build a Secure and Scalable Infrastructure: Utilize AWS services such as EC2, VPC, and IAM to create a secure and scalable environment for the application.
- Implement High Availability: Design the application to run across multiple availability zones with load balancing and auto-scaling.
- Leverage Managed Services: Use managed AWS services like RDS for database management and S3 for storage, ensuring data integrity and performance.
- Monitoring and Management: Implement monitoring solutions using CloudWatch to track performance and respond to issues proactively.
- Infrastructure as Code (IaC): Automate the deployment process using CloudFormation templates, ensuring repeatability and consistency across environments.

<br><br>

# Project Architecture

## Architecture Overview:
The architecture of this project is designed as a multi-tier setup that segregates the application into different layers, each responsible for a specific aspect of the application’s functionality. The architecture is deployed across multiple Availability Zones to ensure high availability and fault tolerance.


## Layers:
### Presentation Layer (Web Tier):
- Amazon EC2 Instances: Frontend web servers are hosted on EC2 instances within an Auto Scaling group, behind an Application Load Balancer (ALB). This ensures that the web servers can scale based on traffic demands.
- Amazon S3: Static content like images, CSS, and JavaScript files are stored in an S3 bucket for low-latency access.
Logic Layer (App Tier):
- Amazon EC2 Instances: Application logic runs on EC2 instances in a private subnet. These instances interact with the database and handle business logic.
- Auto Scaling: Ensures the application layer can automatically scale out or in based on demand.

## Data Layer (Database Tier):
- Amazon RDS (MySQL/PostgreSQL): The relational database is hosted on Amazon RDS, which provides automated backups, software patching, and failover support.

## Networking and Security:
- Amazon VPC: The application is deployed within a VPC, with public subnets for the web tier and private subnets for the app and database tiers.
- NAT Gateway: Allows instances in the private subnets to access the internet for updates without exposing them directly to the internet.
- Security Groups: Firewall rules to control inbound and outbound traffic to the instances.
- IAM Roles: Control access to AWS resources, ensuring that the application components have the necessary permissions.

## Monitoring and Management:
- Amazon CloudWatch: Monitors the performance and health of the application, providing metrics and logs for EC2 instances, ALB, and RDS.
- AWS CloudFormation: Manages the deployment and updates of the entire infrastructure as code, ensuring consistency and repeatability.

## Architecture Diagram:
- Visual Representation: A diagram that visually represents the architecture, showing the flow of data between layers, the use of Availability Zones, and how AWS services interact.

<br><br>



# Compute - Amazon EC2
Amazon EC2 provides scalable computing capacity in the AWS cloud.<br><br>

![Screenshot 2024-09-04 215909](https://github.com/user-attachments/assets/ea685491-b4d6-4f10-ba28-0e1c29a4a6bc)<br><br>

![image](https://github.com/user-attachments/assets/5dbd0948-7716-401e-9906-614b165aef0c)<br><br>

## steps:
- Create a New Key Pair: Explanation and purpose.
- Launch a Web Server Instance: Step-by-step guide.
- Connecting to your Windows Instance: Various methods.
- Elastic IPs & Instance Type: Optional configurations.
- Clean Up Resources: Importance and method.<br><br>

![image](https://github.com/user-attachments/assets/aa745374-6cfa-4b6b-ba7f-cb8e244db3c4)<br><br>

![image](https://github.com/user-attachments/assets/78f8930c-4895-45b6-8f47-3a8377bb4afd)<br><br>

![image](https://github.com/user-attachments/assets/9d5d5440-c0f2-451f-9759-5e01476241f1)<br><br>



# Auto Scaling on AWS
AWS Auto Scaling monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost. Using AWS Auto Scaling, it’s easy to setup application scaling for multiple resources across multiple services in minutes. <br><br>

![Screenshot 2024-09-04 215934](https://github.com/user-attachments/assets/d31d56bc-deb7-4b7a-a4a6-95af672b2a8b)<br><br>

## Services and concepts :
- Primary: Auto Scaling, Launch Templates, Creation and configuration of Security Groups
- Secondary: AMIs, Application Load Balancers

## Steps:

- Creating a Launch Template: Steps and best practices.
- Setup an Auto Scaling Group: Importance and method.
- Configuring Security Groups: Overview and importance.
- Testing the Auto Scaling Group: Ensuring proper scaling.
- Auto Scaling Lab Teardown: Cleanup procedures. 

<br><br>



# Network - Amazon VPC
Amazon VPC lets you create a private network within the AWS cloud.<br><br>

![Screenshot 2024-09-04 220815](https://github.com/user-attachments/assets/f58753ad-907c-4a11-ac2f-f87a0243b2e2)<br><br>

![image](https://github.com/user-attachments/assets/d1774140-0c3a-4819-aea0-14b9c23a35f5)<br><br>


## Steps:
- Create VPC: Set up the VPC with CIDR block.

- Subnets: Create public and private subnets.

- Internet Gateway: Attach an Internet Gateway to the VPC.

- NAT Gateway: Configure NAT Gateway for private subnet instances.

- Route Tables: Set up route tables for traffic routing.<br><br>

![image](https://github.com/user-attachments/assets/d2fa917b-1423-493f-8699-16f925ca8f98)<br><br>


![image](https://github.com/user-attachments/assets/8c5038c0-b4e0-43a3-a376-5d4dd3694a86)<br><br>

![image](https://github.com/user-attachments/assets/5138e882-aa42-4049-997d-9f8bd940f937)<br><br>


![image](https://github.com/user-attachments/assets/759ed561-8d23-40cf-ba18-e1a29eeb0a52)<br><br>



![image](https://github.com/user-attachments/assets/7cd9b269-f1cd-4416-8af5-ae5d82f32c3b)<br><br>

![image](https://github.com/user-attachments/assets/420b6a96-b1d8-4be6-9689-c0e8fa7a7855)<br><br>


![image](https://github.com/user-attachments/assets/8ad9097a-2eb0-4afd-92e1-fe18f4b34aa3)<br><br>

![image](https://github.com/user-attachments/assets/05a8e366-14d0-4cd3-8222-3de6fd87e60c)<br><br>


![image](https://github.com/user-attachments/assets/33c4fc9f-5842-4fed-b920-e4a389998546)

<br><br>



# Security - AWS IAM<br><br>

AWS IAM manages access to AWS services and resources securely.<br><br>

![Screenshot 2024-09-04 220947](https://github.com/user-attachments/assets/6c0023ba-7b96-4a0e-896b-55d6e8cd5fc2)<br><br>

## Steps:
- Launch EC2 Instances with Tags: Organizing and managing instances.

- Create AWS IAM Identities: Overview of users, groups, roles.

![Screenshot 2024-09-04 221001](https://github.com/user-attachments/assets/966c6166-5367-482f-9575-7dd7d73e3282)<br><br>

- Test the Access for Resources: Ensuring proper permissions.

- Assign IAM Role for EC2 Instance: How roles enhance security. 

![Screenshot 2024-09-04 221051](https://github.com/user-attachments/assets/dae15eb3-a04e-4797-a722-8d59826895fc)

<br><br>



# Monitoring - Amazon CloudWatch
CloudWatch provides monitoring for AWS resources and applications.<br><br>

![Screenshot 2024-09-04 221107](https://github.com/user-attachments/assets/210d3ca5-5ce9-4079-bb81-8ae475d60ee6)<br><br>


## Steps:
- Set Up CloudWatch: Enable monitoring for EC2, RDS, etc.<br><br>

![Screenshot 2024-09-04 221116](https://github.com/user-attachments/assets/5d8648c1-7139-4791-9e79-fddeba9137ca)<br><br>


- Create Alarms: Set up alarms based on metrics like CPU usage.

- Logs: Configure CloudWatch Logs for application and system logs.

<br><br>


# Database - Amazon RDS<br><br>

![Screenshot 2024-09-04 221142](https://github.com/user-attachments/assets/43c4ceea-0a66-4961-9c8e-b82813d6d7dc)<br><br>

Amazon RDS manages relational databases with high availability.

![Screenshot 2024-09-04 221155](https://github.com/user-attachments/assets/3a4bf78c-3ca2-41d7-9307-1cf066d28e36)<br><br>


## Steps:
- Launch RDS Instance: Choose the database engine and instance type.

- Configuration: Set up database parameters and security groups.

- Backup: Configure automated backups and snapshots.<br><br>


![Screenshot 2024-09-04 221214](https://github.com/user-attachments/assets/ba55fea7-1507-42cd-ae41-8e28065191ae)
<br><br>


# Storage - Amazon S3 & EFS<br><br>

![Screenshot 2024-09-04 221240](https://github.com/user-attachments/assets/c958ed9f-1497-4112-8824-833055768151)<br><br>

Amazon S3 provides scalable object storage; EFS provides scalable file storage.<br><br>

![Screenshot 2024-09-04 221305](https://github.com/user-attachments/assets/3487a2cf-1252-4f7b-9aed-f4f5f76259d8)<br><br>

## Steps:
- Create S3 Bucket: For static file storage and application data.<br><br>

![Screenshot 2024-09-04 221405](https://github.com/user-attachments/assets/5ec0b47e-98e0-4bce-8f44-5196d9bc4a20)<br><br>


- Configure Permissions: Set bucket policies and access controls.

- Set Up EFS: Configure EFS for shared file storage among instances.

![Screenshot 2024-09-04 221331](https://github.com/user-attachments/assets/d47d2f79-1c92-4ce8-bb8d-b2c9401f1940)

<br><br>


# Provisioning - AWS CloudFormation<br><br>

![Screenshot 2024-09-04 221419](https://github.com/user-attachments/assets/698fbf13-bb68-44bc-8fac-740bdfb17ce6)<br><br>


AWS CloudFormation automates the provisioning of AWS resources.

## Steps:
- Create Templates: Define resources in CloudFormation templates.

- Deploy Stacks: Use templates to deploy resources in a repeatable manner.

- Update and Manage: Update stacks and manage resources.



























