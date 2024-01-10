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
  - Choose an appropriate instance type (e.g., t2.micro for testing purposes).
  - Launch the instance and download the key pair.
 
### Step 2: Create Elastic IP and assign to EC2
- **Description**: This step involves creating an Elastic IP and associating it with your EC2 instance to ensure that the IP address of your instance remains constant even if it's stopped and restarted.
- **Tasks**:
  - Navigate to the Elastic IP or choose it in EC2 settings.
  - Choose Allocate Elastic IP address.
  - Make sure you select the same region in which the EC2 instance was created and confirm by clicking Allocate.
  - After redirecting to the list with elastic ip, click on created ip and then select Associate Elastic IP address where you should select the EC2 instance you created earlier and its private address.
