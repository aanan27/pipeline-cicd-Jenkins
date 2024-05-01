
# Continuous Integration and Continuous Deployment (CI/CD) Pipeline with Jenkins on AWS

## Overview

This project demonstrates setting up a CI/CD pipeline using Jenkins on an AWS EC2 instance for a Node.js application. The pipeline automates the process of building, testing, and deploying the application whenever changes are pushed to the GitHub repository.

## Requirements

- AWS account
- GitHub repository for the Node.js application
- Jenkins and Docker installed on an AWS EC2 Instance

## Setup

### Step 1: Set Up AWS EC2 Instance

1. Launch an EC2 instance on AWS, preferably using Ubuntu image and a t2.micro instance type.
2. Configure security groups to allow SSH, HTTP, and HTTPS traffic.
3. Connect to the instance via SSH.

### Step 2: Install Jenkins on EC2 Instance

1. Update the server and install Java.
   ```bash
   sudo apt-get update
   sudo apt install openjdk-11-jre
   ```
2. Verify Java installation.
   ```bash
   java -version
   ```
3. Install Jenkins.
   ```bash
   curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
   echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
   sudo apt-get update
   sudo apt-get install jenkins
   ```
4. Start Jenkins service.
   ```bash
   sudo systemctl enable jenkins
   sudo systemctl start jenkins
   sudo systemctl status jenkins
   ```
5. Access Jenkins on your browser using your EC2 instance's public IP address and port 8080.

### Step 3: Configure Jenkins

1. Unlock Jenkins and install suggested plugins.
2. Create an admin user for Jenkins.
3. Install necessary plugins such as Git, Pipeline, and Docker.

### Step 4: GitHub Integration

1. Generate SSH keys on the EC2 instance.
2. Add the public SSH key to your GitHub account.
3. Configure Jenkins credentials for GitHub integration.

### Step 5: Create Jenkins Job

1. Create a new Freestyle Project in Jenkins.
2. Configure project parameters including GitHub repository URL and branch.
3. Add build steps to build and deploy the application using Docker.

### Step 6: Test the Pipeline

1. Trigger a build in Jenkins.
2. Verify that Jenkins successfully builds the Docker image and deploys the application.
3. Access the deployed application on your browser.

## Additional Steps (Optional)

- Implement webhook in GitHub to trigger Jenkins builds automatically on code push.
- Enhance pipeline with additional stages such as testing, security scanning, and deployment to production.



