# Node.js Application Deployment on AWS EC2

## Overview

This README document provides a comprehensive guide for deploying a Node.js application on an Amazon Web Services (AWS) EC2 instance. This project demonstrates how to leverage AWS EC2 for hosting a Node.js server, ensuring scalable and reliable application performance.

## Prerequisites

- AWS Account
- Basic knowledge of AWS services, especially EC2
- Node.js application ready for deployment

## Step-by-Step Deployment Guide

### Step 1: Setting Up AWS EC2 Instance
- **Description**: Creating and configuring an EC2 instance suitable for Node.js deployment.
- **Tasks**:
  - Log into AWS Management Console.
  - Navigate to the EC2 dashboard and create a new instance.
  - Choose Ubuntu system.
  - Choose an appropriate instance type (e.g., t2.micro for testing purposes).
  - Launch the instance and download the key pair.
 
### Step 2: Create Elastic IP and assign to EC2
- **Description**: This step involves creating an Elastic IP and associating it with your EC2 instance to ensure that the IP address of your instance remains constant even if it's stopped and restarted.
- **Tasks**:
  - Navigate to the Elastic IP or choose it in EC2 settings.
  - Choose 'Allocate Elastic IP address'.
  - Make sure you select the same region in which the EC2 instance was created and confirm by clicking 'Allocate'.
  - After redirecting to the list with elastic ip, click on created ip and then select 'Associate Elastic IP address' where you should select the EC2 instance you created earlier and its private address.

### Step 3: Configuring Security Groups for Your EC2 Instance
- **Description**: Security Groups act as a virtual firewall for your EC2 instances, controlling both inbound and outbound traffic. In this step, we will create and configure a Security Group to ensure that your EC2 instance has the appropriate level of security and accessibility.
- **Tasks**:
  - Navigate to the Elastic IP or choose it in EC2 settings.
  - Navigate to the EC2 instance you created earlier and go to 'Security'.
  - Select the security group that has been added to your instance and add the required rules to it by clicking 'Edit inbound rules'.
  - Add rules in the same way as shown in the screenshot, where the value of 5000 corresponds to the port on which the application is running.
 ![image](https://github.com/chlip1/deploy-node-ec2/assets/81360555/35dbc28e-7be3-4ee7-a7c1-0230f5d48a8f)
