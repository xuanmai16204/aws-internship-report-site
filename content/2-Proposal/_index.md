---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

In this section, you need to summarize the contents of the workshop that you **plan** to conduct.

# CloudDoc
## A Web-based Document Management and Sharing Platform on AWS

### 1. Executive Summary
CloudDoc is a web-based document management and sharing platform designed for students, deployed on the Amazon Web Services (AWS) cloud platform. The system supports core functionalities including file upload, document search, online live preview, download, and an administrative document moderation workflow. CloudDoc's system architecture is designed to be secure, cost-optimized, and highly scalable by integrating modern AWS services to ensure rapid content delivery and reliable data storage.

### 2. Problem Statement
*Current Challenges*
Traditional document management tools frequently struggle to handle large file uploads, lack proper user role separation, lack centralized or automated content moderation workflows, and fail to scale effectively during high-traffic peaks. Additionally, storing large files directly on application backend servers rapidly consumes compute resources and increases infrastructure costs.

*The Solution*
CloudDoc addresses these challenges by employing a decoupled architecture that separates the user-facing React frontend, the Node.js/Express backend API, and object storage services on Amazon S3. The upload workflow leverages S3 presigned URLs, allowing clients to upload documents directly to S3 and significantly reducing backend server load. For long-term storage and cost efficiency, older or archival files are transitioned to Amazon S3 Glacier. A PostgreSQL DB stores metadata to facilitate fast, efficient searching. Lastly, administrative task management and user notifications are handled using AWS messaging services to ensure high availability and responsiveness.

*Benefits and Return on Investment (ROI)*
The solution establishes a stable document sharing environment for students while minimizing manual overhead via integrated moderation logic. Relying on Amazon S3 and lifecycle transition into Glacier optimizes database storage budgets. The low running costs of serverless components paired with cost-optimized EC2 instances ensure that the platform remains financially viable from development to production.

### 3. Solution Architecture
CloudDoc uses a secure and decoupled architecture to manage, search, and store files. The system coordinates the following components:

![CloudDoc Architecture](/images/2-Proposal/anh1.png)

*AWS Services Used & Roles*
- **Frontend**: The user interface is optimized and served via **Amazon CloudFront** to drop content delivery latency.
- **Application Load Balancer**: Balances and routes API requests efficiently to backend servers.
- **Amazon EC2**: Houses the Node.js/Express Backend API to process business logic, handle authentication, manage document flows, and issue presigned URLs.
- **Amazon RDS PostgreSQL**: Stores user credentials, document metadata records, and moderation histories.
- **Amazon S3**: Stores original uploaded documents and media attachments directly via customer client upload sessions.
- **Amazon S3 Glacier**: Archives older or infrequently-accessed files to reduce active storage costs.
- **Amazon SQS** & **Amazon SNS**: Feeds message queues (SQS) and notification configurations (SNS) to process actions asynchronously and message users about document moderation updates.
- **Amazon CloudWatch**: Collects log streams, tracks service metrics, and sets alarm criteria to monitor infrastructure performance.

### 4. Technical Implementation

During the development of CloudDoc, the team opted for a phased implementation to ensure that critical functions were built, tested, and integrated stably before moving to the next step. Breaking down the development process helps mitigate unexpected errors and facilitates future system scalability.

The main components implemented include:

- Building the user interface with React for Home, Search, Upload, Preview, Download, and Administration Dashboard functions.
- Designing the Backend API with Node.js and Express to handle authentication, authorization, document management, and Presigned URL generation.
- Designing the PostgreSQL database to store metadata, document status, user information, and processing logs.
- Integrating Amazon S3 for storing raw files, reducing the backend's workload of handling binary data directly.
- Establishing the upload workflow using Presigned URLs to reduce application server load and improve scalability.
- Connecting the frontend, backend, and AWS services into a unified processing workflow.
- Performing end-to-end testing to verify that the entire workflow—from upload and moderation to preview and download—functions correctly.

The team also prioritized standardizing the codebase structure, separating the user interface, business logic, and data layer to make maintenance and future feature development more convenient.

### 5. Implementation Roadmap and Milestones

To ensure steady progress, the CloudDoc project was divided into three main phases.

#### Phase 1: Completing Foundation Features

In the first phase, the team focused on building the core functions of the system.

- Designing the user interface.
- Implementing authentication and authorization.
- Developing the document upload feature.
- Designing the database for storing metadata.
- Completing the basic search functionality.

#### Phase 2: Integrating AWS Services

After completing the application core, the team integrated AWS cloud services.

- Connecting the frontend with the backend.
- Integrating Amazon S3 for document storage.
- Using Presigned URLs for the upload workflow.
- Completing the APIs for document preview and download.
- Testing the end-to-end document processing workflow.

#### Phase 3: Finalizing and Optimizing the System

In the final phase, the team focused on refining the product and preparing for the final presentation.

- Optimizing the user interface.
- Finalizing the Administration Dashboard.
- Adding system monitoring via Amazon CloudWatch.
- Preparing project presentation and demonstration materials.
- Testing all functionalities before final evaluation.

Dividing the project into multiple phases helped the team easily track progress, evaluate outcomes after each milestone, and reduce integration risks.

### 6. Budget Estimation

To evaluate the feasibility of deploying CloudDoc in a production environment, the team used the AWS Pricing Calculator to estimate the monthly operational costs for an architecture close to reality.

![AWS Pricing](/images/2-Proposal/anh2.png)

The figure above is generated using the AWS Pricing Calculator for the CloudDoc architecture.

Based on the estimation results, Amazon RDS and Amazon EC2 consume the largest portion of the budget due to their continuous operation. Services such as Application Load Balancer, CloudWatch, and NAT Gateway also incur costs but at lower rates.

During the learning and testing phases, the team can significantly reduce costs using the following measures:

- Using smaller EC2 instance sizes.
- Stopping EC2 instances when not in use.
- Leveraging AWS Free Tier for eligible services.
- Setting up S3 Lifecycle policies to transition infrequently accessed data to lower-cost storage classes.
- Monitoring resource costs via AWS Budgets to prevent unexpected expenses.

The estimated cost above is for reference only and can vary depending on the actual scale and usage patterns of the system.

### 7. Risk Assessment

During the implementation of CloudDoc, the team identified several risks that could affect the system's quality and operation.

| Risk | Impact | Mitigation Strategy |
| --- | --- | --- |
| Upload failures due to expired Presigned URLs | Users cannot upload documents | Set a reasonable expiration time and allow generating new URLs |
| Metadata save failures | Documents do not appear in the system | Implement transactions between file upload and metadata storage |
| Inappropriate IAM configuration | Vulnerable access to AWS resources or overly broad permissions | Apply the Least Privilege principle |
| Unexpected AWS cost spikes | Budget constraints | Monitor costs using AWS Budgets and perform regular resource cleanups |
| Absence of system monitoring | Difficult to identify runtime errors | Use CloudWatch Logs, Metrics, and Alarms |
| Scalability bottlenecks | Hard to accommodate user growth | Separate frontend, backend, and storage components |

Identifying these risks early in the design stage allowed the team to proactively formulate contingency plans, ensuring the system's reliability and stability.

### 8. Expected Outcomes

CloudDoc aims to build a modern study document management and sharing system on AWS.

After completing the project, the system is expected to achieve the following goals:

- Users can upload, manage, and share documents easily.
- Documents are securely stored in Amazon S3 and managed via metadata in PostgreSQL.
- Fast document search, preview, and download functionalities.
- Document moderation workflow to improve document quality before publication.
- Scalable architecture that easily integrates new features in the future.
- Appropriate integration of AWS services to enhance security, scalability, and performance.

In conclusion, CloudDoc provides valuable practical experience in web development, cloud computing, AWS services, and teamwork. By executing this project, the team gained hands-on expertise in analyzing requirements, designing architectures, writing reliable full-stack applications, and resolving integration challenges in a development setting.