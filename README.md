# 🧠 Cognito Task Manager (AWS Serverless Project)

This is a full-stack serverless task management application built on AWS. It allows users to log in via AWS Cognito, create tasks with optional file attachments, store data in RDS and DynamoDB, and trigger email confirmations using SQS and Nodemailer.

## 🌐 Live URL
[https://d4jy0dgm09bv1.cloudfront.net](https://d4jy0dgm09bv1.cloudfront.net)

---

## 🧩 Features

- 🔐 **User Authentication** using AWS Cognito
- 📝 **Task Creation** with title, description, and optional file upload
- ☁️ **File Storage** via Amazon S3 (pre-signed URL pattern)
- 🗄️ **Data Storage**
  - **PostgreSQL (RDS)**: Structured task data
  - **DynamoDB**: Lightweight metadata for redundancy/performance
- 📩 **Email Notifications** with Nodemailer via SQS consumer Lambda
- 📨 **Queue-Based Processing** using Amazon SQS
- 💻 **Frontend Hosted** on EC2 inside a custom VPC
- 🔐 Secure communication with Authorization headers (JWT from Cognito)
- 📈 CloudWatch logs integrated for all AWS services

---

## 📦 Tech Stack

- **Frontend**: HTML/CSS/JS (static frontend hosted on EC2)
- **Backend**: AWS Lambda (Node.js 18.x)
- **Database**: Amazon RDS (PostgreSQL) & DynamoDB
- **Authentication**: AWS Cognito (User Pool)
- **File Storage**: Amazon S3
- **Email Service**: Nodemailer (Gmail)
- **Queue Service**: Amazon SQS
- **Monitoring**: AWS CloudWatch

---

## 🛠️ Project Structure
cognito-task-app/
│
├── index.html                 # Main frontend UI (HTML, CSS, JS)
├── scripts/
│   └── upload-script.js       # Handles task creation, file uploads, and API calls
├── lambda/
│   ├── createTask.js          # Inserts new task into RDS + DynamoDB, then sends to SQS
│   ├── getUploadUrl.js        # Returns pre-signed S3 URL for file uploads
│   ├── getTasks.js            # Fetches tasks for the current user
│   └── processQueue.js        # Triggered by SQS, sends email confirmations via Nodemailer
├── .env.sample                # Template for environment variables (credentials NOT included)
├── screenshots/               # Folder to store required deployment screenshots
└── README.md                  # Full project documentation

