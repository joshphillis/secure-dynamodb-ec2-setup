# secure-dynamodb-ec2-setup

# AWS DynamoDB EC2 Deployment Guide

## 📦 Overview
This project demonstrates how to deploy an EC2 instance on AWS, configure Python and Boto3, and interact with a DynamoDB table using IAM roles. It’s designed as a hands-on lab for cloud engineers, educators, or veteran mentors introducing secure cloud architecture.

## 🚀 Prerequisites
- AWS account with EC2 and IAM permissions
- Familiarity with basic Linux commands
- SSH key pair for EC2 access
- DynamoDB table (e.g., `inventory`) in **us-west-2**

## 🛠️ Setup Instructions

### 1. Launch EC2 Instance
- AMI: Ubuntu Server 24.04 LTS
- Instance type: t2.micro (or preferred)
- Security Group: Allow SSH (port 22) and HTTP (port 80)
- Key Pair: Create or use existing for SSH access

### 2. Configure Environment
```bash
sudo apt update && sudo apt install python3.12 python3.12-venv -y
python3.12 -m venv /opt/dynamodb/venv
source /opt/dynamodb/venv/bin/activate
pip install boto3
```

### 3. IAM Role Setup
- Create IAM role: `DynamoDB2`
- Attach policy: `AmazonDynamoDBFullAccess`
- Attach role to EC2 instance via AWS Console

### 4. Python Script Execution
- Place script in `/opt/dynamodb/inventory.py`
- Ensure it uses `boto3.resource('dynamodb')`
- Run script to query or update the `inventory` table

### 5. DynamoDB Table Access
- Switch region to `us-west-2` in AWS Console
- Verify table exists and is accessible via script

## 🧹 Cleanup
- Terminate EC2 instance
- Delete IAM role if no longer needed
- Remove DynamoDB table if created for testing

## 📚 Learning Objectives
- Understand IAM role-based access for EC2
- Practice secure credential handling
- Explore DynamoDB operations via Python
- Compare AWS and Azure cloud patterns

## 🧠 Author Notes
This guide was built to support cloud infrastructure education, veteran mentorship, and hands-on learning. Adapt it freely for workshops, CTE programs, or onboarding labs.

