# 🚀 Cognito Task Manager - AWS Serverless Powerhouse ⚡

![AWS Serverless](https://img.shields.io/badge/AWS-Serverless-orange?logo=amazon-aws\&style=for-the-badge)
![Node.js](https://img.shields.io/badge/Node.js-18.x-green?logo=node.js\&style=for-the-badge)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-RDS-blue?logo=postgresql\&style=for-the-badge)
![DynamoDB](https://img.shields.io/badge/DynamoDB-NoSQL-yellow?logo=amazon-dynamodb\&style=for-the-badge)
![SQS](https://img.shields.io/badge/SQS-Queue-purple?logo=amazon-sqs\&style=for-the-badge)

🔗 **Live Demo**: [https://d4jy0dgm09bv1.cloudfront.net](https://d4jy0dgm09bv1.cloudfront.net) Currently Down :(.

## 🌟 Why This Rocks

✅ **Zero servers** - 100% serverless architecture
✅ **Battle-tested** - Dual database redundancy with PostgreSQL & DynamoDB
✅ **Secure by design** - Cognito authentication and VPC-isolated Lambda
✅ **Cost efficient** - Serverless, scalable, and optimized usage
✅ **Blazing fast** - CloudFront edge-optimized static UI delivery
✅ **Seamless UX** - Direct-to-S3 file uploads, async task creation, instant feedback

## 🏗️ Architecture Blueprint

```mermaid
graph LR
    U[User]-->|1: Login|C(Cognito)
    U-->|2: Visit App|EC2[EC2: Static Hosting]
    EC2-->|3: Serve|UI[index.html + JS]

    UI-->|4: Auth|C
    C-->|5: JWT|UI

    UI-->|6: File Upload|S3[S3 Bucket]
    UI-->|7: Send Metadata|G[API Gateway]
    G-->|8: Proxy|VPC_Lambda[VPC + Lambda: createTask.js]

    VPC_Lambda-->|9a: Write|R[(PostgreSQL RDS)]
    VPC_Lambda-->|9b: Cache|D[(DynamoDB)]
    VPC_Lambda-->|9c: Notify|Q[SQS Queue]

    Q-->|10: Trigger|M[Lambda: processQueue.js]
    M-->|11: Email|N[(Nodemailer SMTP)]

    R-->|fileKey|S3
    D-->|fileKey|S3
```

### 4. Project Structure Block

## 📂 Project Structure

```mermaid
graph TD
    R[/cognito-task-app/]-->F[index.html]
    R-->S[/scripts/]
    R-->L[/lambda/]
    S-->U[upload-script.js]
    L-->C[createTask.js]
    L-->G[getUploadUrl.js]
    L-->T[getTasks.js]
    L-->P[processQueue.js]
```

### 5. Tech Stack Block

## ⚡ Tech Stack

| Layer        | Technology        | Benefit                               |
| ------------ | ----------------- | ------------------------------------- |
| **Frontend** | Vanilla JS + EC2  | Lightweight UI, hosted via EC2        |
| **Auth**     | Cognito           | Secure user login & JWT issuance      |
| **Compute**  | Lambda            | Stateless logic handling, async flows |
| **Storage**  | S3 + RDS + Dynamo | Reliable, fast, and durable storage   |
| **Infra**    | VPC               | Secure connectivity for Lambda/RDS    |
| **Queueing** | SQS               | Decoupled email and processing layer  |
| **Email**    | Nodemailer (SMTP) | Easy transactional notifications      |

## 🔄 Data Flow

1. **Auth**: User logs in via Cognito, receives JWT
2. **App Load**: EC2 hosts `index.html`, JS interacts via API
3. **File Upload**: Direct PUT to S3 using pre-signed URLs
4. **Task Submit**: Task metadata sent to Lambda via API Gateway (inside VPC)
5. **DB Write**: Lambda writes to PostgreSQL and DynamoDB
6. **Queue Trigger**: SQS triggers `processQueue.js` Lambda
7. **Notification**: Email sent to user via Nodemailer + Gmail SMTP

### 6. License Block

## 🚦 License - "The MIT License But With More Sass"

This project is licensed under the **"I'm Not a Lawyer But Here's Some Rules" License**:

```mermaid
graph LR
    A[Your Interest] --> B{Read License?}
    B -->|No| C[Enjoy!]
    B -->|Yes| D[Still Enjoy!]
    C --> E[Happy Coding]
    D --> E
    E --> F[Just Don't Sue Us]
```

**By using this code you agree to:**

**-Bring snacks to the next standup**

**-Not judge our questionable Lambda naming conventions**

**-Pretend the documentation was always this good**
