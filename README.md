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

### Step 4: Connect To EC2 via SSH
- **Description**: Secure Shell (SSH) is a protocol used to securely log onto remote systems. In this step, you will connect to your AWS EC2 instance using SSH. AWS provides the exact SSH command, including the key pair and public DNS or IP address, in the EC2 console.
- **Tasks**:
  - Select your instance and click on the 'Connect' button at the top.
  - In the "Connect to instance" section, you will find the SSH command for your instance under "SSH client" tab.
  - The command will typically look like this: ssh -i "your-key-pair.pem" ec2-user@ec2-xx-xxx-xx-xx.compute-1.amazonaws.com. Replace "your-key-pair.pem" with your actual key pair file name.
  - Open a terminal on your local machine.
  - Ensure that your private key file (.pem file) permissions are set correctly with the command: chmod 400 your-key-pair.pem.
  - Use the SSH command you retrieved from the AWS console to connect to your instance.

 ### Step 5: Preparing the Linux Server for Node.js
 - **Description**: This step involves updating your Linux server and setting up Node.js using Node Version Manager (NVM). NVM allows you to easily manage and switch between different Node.js versions.
 - **Tasks**:
  1. **Update and Upgrade the Server**:
     - Run the following commands to update your package listings and upgrade your system to the latest versions of installed packages:
       ```bash
       sudo apt update && sudo apt upgrade -y
       ```

  2. **Install NVM (Node Version Manager)**:
     - Execute the following command to download and install NVM:
       ```bash
       curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
       ```
     - This script clones the NVM repository to `~/.nvm` and adds the source lines to your profile (`~/.bashrc`, `~/.zshrc`, `~/.profile`, or `~/.bash_profile`).

  3. **Load NVM and Install Node.js**:
     - To load NVM, you'll need to either open a new terminal session or run these commands:
       ```bash
       export NVM_DIR="$HOME/.nvm"
       [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
       [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
       ```
     - Once NVM is loaded, install the latest LTS version of Node.js using NVM:
       ```bash
       nvm install --lts
       ```
### Step 6: Launching the Node.js Application with PM2

- **Description**: This step involves navigating to your Node.js application directory, installing dependencies, and using PM2 to start and manage your application process.

- **Tasks**:
  1. **Navigate to Your Application Directory**:
     - Change to the application's directory (e.g backend) skip this step if you only have node js applications in the repository:
       ```bash
       cd backend
       ```

  2. **Install Application Dependencies**:
     - Install the necessary Node.js packages specified in your `package.json`:
       ```bash
       npm i
       ```

  3. **Install and Configure PM2**:
     - Install PM2 globally using npm:
       ```bash
       npm install -g pm2
       ```
     - Start your application with PM2:
       ```bash
       pm2 start app.js --name=YOUR_APP
       ```
     - Save the current application list to be resurrected on reboot:
       ```bash
       pm2 save
       ```
     - To setup the PM2 startup script (which keeps your app running after system reboots), execute the command generated by:
       ```bash
       pm2 startup
       ```
       - Follow the instructions provided by the `pm2 startup` command to complete the setup.
