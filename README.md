# 🚀 Cognito Task Manager - AWS Serverless Powerhouse ⚡

![AWS Serverless](https://img.shields.io/badge/AWS-Serverless-orange?logo=amazon-aws&style=for-the-badge) 
![Node.js](https://img.shields.io/badge/Node.js-18.x-green?logo=node.js&style=for-the-badge) 
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-RDS-blue?logo=postgresql&style=for-the-badge)
![DynamoDB](https://img.shields.io/badge/DynamoDB-NoSQL-yellow?logo=amazon-dynamodb&style=for-the-badge)
![SQS](https://img.shields.io/badge/SQS-Queue-purple?logo=amazon-sqs&style=for-the-badge)

🔗 **Live Demo**: [https://d4jy0dgm09bv1.cloudfront.net](https://d4jy0dgm09bv1.cloudfront.net)


## 🌟 Why This Rocks
✅ **Zero servers** - 100% serverless architecture  
✅ **Battle-tested** - Dual database redundancy  
✅ **Secure by design** - End-to-end encryption  
✅ **Cost efficient** - Pay only for what you use  
✅ **Blazing fast** - Edge-optimized delivery  

## 🏗️ Architecture Blueprint
```mermaid
graph LR
    U[User]-->|1: Login|C(Cognito)
    U-->|2: Submit Task|G[API Gateway]
    C-->|JWT|G
    G-->|3: Process|L[Lambda]
    L-->|4a: Store|R[(PostgreSQL)]
    L-->|4b: Cache|D[(DynamoDB)]
    L-->|5: Queue|Q[SQS]
    Q-->|6: Trigger|M[Mailer Lambda]
    M-->|7: Send|N[(Nodemailer)]
    U-->|8: Upload|S[/S3 Bucket\]
```

### 4. Project Structure Block
```markdown
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
```markdown
## ⚡ Tech Stack
| Layer          | Technology       | Benefit                     |
|----------------|------------------|-----------------------------|
| **Frontend**   | Vanilla JS       | Zero framework bloat        |
| **Auth**       | Cognito          | Enterprise-grade security  |
| **Compute**    | Lambda           | Auto-scaling powerhouse    |
| **Storage**    | S3 + RDS + Dynamo| Perfect data trio           |
```

## 🔄 Data Flow
1. **Auth**: User → Cognito → JWT
2. **Task**: Form → API → Lambda → DBs
3. **Files**: Direct S3 uploads
4. **Emails**: SQS → Lambda → Inbox



### 8. License Block
No license bro
