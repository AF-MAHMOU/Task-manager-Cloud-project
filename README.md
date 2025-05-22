# 🚀 Cognito Task Manager - AWS Serverless Powerhouse ⚡

![AWS Serverless](https://img.shields.io/badge/AWS-Serverless-orange?logo=amazon-aws&style=for-the-badge) 
![Node.js](https://img.shields.io/badge/Node.js-18.x-green?logo=node.js&style=for-the-badge) 
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-RDS-blue?logo=postgresql&style=for-the-badge)

A **cutting-edge serverless task management system** leveraging AWS's full potential with bulletproof architecture and seamless user experience.

🔗 **Live Demo**: [https://d4jy0dgm09bv1.cloudfront.net](https://d4jy0dgm09bv1.cloudfront.net) (Give it a spin!)

---

## 🔥 Core Features

### 🔐 Security First
- **Military-grade Auth** via AWS Cognito (JWT protected)
- **Secure File Uploads** with pre-signed S3 URLs
- **Encrypted Data** at rest (RDS + DynamoDB)

### ⚡ Performance
- **Dual Database Architecture** (RDS + DynamoDB for lightning queries)
- **Queue-Powered Processing** (SQS for background tasks)
- **Serverless Scalability** (Lambda auto-scaling)

### 📬 Smart Notifications
- **Instant Email Confirmations** via Nodemailer
- **Decoupled Processing** (SQS consumer pattern)
- **CloudWatch Monitoring** for all services

### 🛠️ Developer Experience
- **Clean Architecture** with separation of concerns
- **Environment Ready** (.env.sample template)
- **Comprehensive Logging** (CloudWatch integration)

---

## 🏗️ Architectural Blueprint

```mermaid
graph TD
    A[User] -->|Login| B[Cognito]
    A -->|Submit Form| C[API Gateway]
    B -->|JWT| C
    C -->|Create Task| D[Lambda]
    D -->|Store Data| E[(PostgreSQL RDS)]
    D -->|Cache Metadata| F[(DynamoDB)]
    D -->|Queue Message| G[SQS]
    G -->|Trigger| H[Lambda]
    H -->|Send Email| I[Nodemailer]
    A -->|Upload File| J[S3 Pre-Signed URL]

cognito-task-app/│├── index.html # Main frontend UI (HTML, CSS, JS)├── scripts/│ └── upload-script.js # Handles task creation, file uploads, and API calls├── lambda/│ ├── createTask.js # Inserts new task into RDS + DynamoDB, then sends to SQS│ ├── getUploadUrl.js # Returns pre-signed S3 URL for file uploads│ ├── getTasks.js # Fetches tasks for the current user│ └── processQueue.js # Triggered by SQS, sends email confirmations via Nodemailer├── .env.sample # Template for environment variables (credentials NOT included)├── screenshots/ # Folder to store required deployment screenshots└── README.md # Full project documentation
