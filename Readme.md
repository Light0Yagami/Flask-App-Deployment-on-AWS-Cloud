# Flask Application Deployment on AWS

This repository contains documentation and scripts for deploying a Flask application on AWS using Amazon EC2, DynamoDB, and S3. Follow the steps below to deploy the application successfully.

## Table of Contents
1. [Getting Started](#getting-started)
    - [Logging in to the AWS Management Console](#task-1-logging-in-to-the-aws-management-console)
    - [Enabling MFA (optional)](#task-2-enabling-mfa-optional)
    - [Creating an IAM user](#task-3-creating-an-iam-user)
2. [Setting Up IAM Role](#setting-up-iam-role)
    - [Creating IAM Role for EC2](#task-4-setting-up-an-iam-role-for-an-ec2-instance)
3. [Launching EC2 Instance](#launching-ec2-instance)
    - [Downloading the Application](#task-1-launching-an-ec2-instance-that-uses-a-role)
4. [Setting Up Networking](#setting-up-networking)
    - [Creating VPC](#task-1-creating-the-vpc)
    - [Creating Subnets](#task-2-creating-subnets)
    - [Creating Route Tables](#task-3-creating-route-tables)
5. [Configuring DynamoDB](#configuring-dynamodb)
    - [Creating DynamoDB Table](#task-2-creating-the-dynamodb-table)
6. [Testing the Application](#testing-the-application)
    - [Launching EC2 Instance](#task-1-launching-an-ec2-instance)
    - [Creating Application Load Balancer](#task-2-creating-the-application-load-balancer)
    - [Creating Launch Template](#task-3-creating-the-launch-template)
    - [Creating Auto Scaling Group](#task-4-creating-the-auto-scaling-group)
    - [Testing the Application](#task-5-testing-the-application)
7. [Cleaning Up](#cleaning-up)
    - [Deleting AWS Resources](#task-6-deleting-the-course-resources)

---

## Getting Started

### Task 1: Logging in to the AWS Management Console

1. Open your web browser and navigate to the [AWS Management Console](https://aws.amazon.com/console/).

2. Enter your AWS account credentials and click "Sign In."

### Task 2: Enabling MFA (optional)

(Optional) Enable Multi-Factor Authentication (MFA) for your AWS account. Follow the AWS documentation to set up MFA.

### Task 3: Creating an IAM user

1. In the AWS Management Console, navigate to the IAM dashboard.

2. Click "Users" in the left navigation pane.

3. Click "Add user."

4. Enter a username and select "Programmatic access."

5. Attach the necessary policies, such as "AmazonDynamoDBFullAccess" and "AmazonS3FullAccess."

6. Complete the user creation process and note down the Access Key ID and Secret Access Key.

---

## Setting Up IAM Role

### Task 4: Setting up an IAM role for an EC2 instance

1. In the AWS Management Console, navigate to the IAM dashboard.

2. Click "Roles" in the left navigation pane.

3. Click "Create role."

4. Select "EC2" as the service that will use this role.

5. Attach policies "AmazonDynamoDBFullAccess" and "AmazonS3FullAccess" to the role.

6. Review and name the role, then click "Create role."

---

## Launching EC2 Instance

### Task 1: Launching an EC2 instance that uses a role

1. SSH into your EC2 instance or use the AWS Systems Manager Session Manager to access it.

2. Run the following commands to set up the Flask application:

```bash
wget https://aws-tc-largeobjects.s3-us-west-2.amazonaws.com/DEV-AWS-MO-GCNv2/FlaskApp.zip
unzip FlaskApp.zip
cd FlaskApp/
yum -y install python3-pip
pip install -r requirements.txt
yum -y install stress
export PHOTOS_BUCKET=<YOUR_PHOTOS_BUCKET_NAME>
export AWS_DEFAULT_REGION=<YOUR_AWS_REGION>
export DYNAMO_MODE=on
FLASK_APP=application.py /usr/local/bin/flask run --host=0.0.0.0 -

```
## Setting Up Networking

### Task 1: Creating the VPC
- **Importance**: Establishes the foundational network within AWS to host all resources.

### Task 2: Creating Subnets

- **Importance**: Divides the VPC into subnetworks to organize resources and control traffic flow.

### Task 3: Creating Route Tables
- **Importance**: Defines rules to direct network traffic from subnets for efficient communication.

---

## Configuring DynamoDB

### Task 2: Creating the DynamoDB table
- **Importance**: Sets up a NoSQL database to store and retrieve application data quickly.

## Testing the Application
### Task 3: Testing the application
- **Importance**: Ensures the Flask application functions correctly before deployment.

### Task 4: Viewing the item in the database
- **Importance**: Confirms that the application's data is being accurately stored in DynamoDB.

--- 

## Launching EC2 Instance (Load Balancer)

### Task 1: Launching an EC2 instance
- **Importance**: Provides a virtual server to run the application.

### Task 2: Creating the Application Load Balancer
- **Importance**: Distributes incoming application traffic across multiple targets for better performance.

### Task 3: Creating the launch template
- **Importance**: Streamlines the process of launching instances with predefined configurations.

### Task 4: Creating the Auto Scaling group
- **Importance**: Automatically adjusts the number of EC2 instances to meet the application's demand.

---

### Task 5: Testing the application
- **Importance**: Verifies the application's functionality under the load-balanced environment.

---

## Cleaning Up

### Task 6: Deleting the course resources
- **Importance**: Removes AWS resources to prevent unnecessary costs after the project is completed.



This README provides a brief overview of each task and its significance in the setup and management of AWS resources for your application. It's essential to follow these steps to ensure a scalable, reliable, and cost-effective infrastructure.

<sub>
This project was created as the final submission for a Coursera course. It encompasses a comprehensive AWS infrastructure setup and management, demonstrating the practical application of cloud services in a real-world scenario. Upon successful submission, a Certificate of Completion was awarded.
</sub>






