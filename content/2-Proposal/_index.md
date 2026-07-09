---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

In this section, you need to summarize the contents of the workshop that you **plan** to conduct.

# IoT Weather Platform for Lab Research
## A Unified AWS Serverless Solution for Real-Time Weather Monitoring

### 1. Executive Summary
The IoT Weather Platform is designed for the ITea Lab team in Ho Chi Minh City to enhance weather data collection and analysis. It supports up to 5 weather stations, with potential scalability to 10-15, utilizing Raspberry Pi edge devices with ESP32 sensors to transmit data via MQTT. The platform leverages AWS Serverless services to deliver real-time monitoring, predictive analytics, and cost efficiency, with access restricted to 5 lab members via Amazon Cognito.

### 2. Problem Statement
### What’s the Problem?
Current weather stations require manual data collection, becoming unmanageable with multiple units. There is no centralized system for real-time data or analytics, and third-party platforms are costly and overly complex.

### The Solution
The platform uses AWS IoT Core to ingest MQTT data, AWS Lambda and API Gateway for processing, Amazon S3 for storage (including a data lake), and AWS Glue Crawlers and ETL jobs to extract, transform, and load data from the S3 data lake to another S3 bucket for analysis. AWS Amplify with Next.js provides the web interface, and Amazon Cognito ensures secure access. Similar to Thingsboard and CoreIoT, users can register new devices and manage connections, though this platform operates on a smaller scale and is designed for private use. Key features include real-time dashboards, trend analysis, and low operational costs.

### Benefits and Return on Investment
The solution establishes a foundational resource for lab members to develop a larger IoT platform, serving as a study resource, and provides a data foundation for AI enthusiasts for model training or analysis. It reduces manual reporting for each station via a centralized platform, simplifying management and maintenance, and improves data reliability. Monthly costs are $0.66 USD per the AWS Pricing Calculator, with a 12-month total of $7.92 USD. All IoT equipment costs are covered by the existing weather station setup, eliminating additional development expenses. The break-even period of 6-12 months is achieved through significant time savings from reduced manual work.

### 3. Solution Architecture
The platform employs a serverless AWS architecture to manage data from 5 Raspberry Pi-based stations, scalable to 15. Data is ingested via AWS IoT Core, stored in an S3 data lake, and processed by AWS Glue Crawlers and ETL jobs to transform and load it into another S3 bucket for analysis. Lambda and API Gateway handle additional processing, while Amplify with Next.js hosts the dashboard, secured by Cognito. The architecture is detailed below:

![IoT Weather Station Architecture](/images/2-Proposal/edge_architecture.jpeg)

![IoT Weather Platform Architecture](/images/2-Proposal/platform_architecture.jpeg)

### AWS Services Used
- **AWS IoT Core**: Ingests MQTT data from 5 stations, scalable to 15.
- **AWS Lambda**: Processes data and triggers Glue jobs (two functions).
- **Amazon API Gateway**: Facilitates web app communication.
- **Amazon S3**: Stores raw data in a data lake and processed outputs (two buckets).
- **AWS Glue**: Crawlers catalog data, and ETL jobs transform and load it.
- **AWS Amplify**: Hosts the Next.js web interface.
- **Amazon Cognito**: Secures access for lab users.

### Component Design
- **Edge Devices**: Raspberry Pi collects and filters sensor data, sending it to IoT Core.
- **Data Ingestion**: AWS IoT Core receives MQTT messages from the edge devices.
- **Data Storage**: Raw data is stored in an S3 data lake; processed data is stored in another S3 bucket.
- **Data Processing**: AWS Glue Crawlers catalog the data, and ETL jobs transform it for analysis.
- **Web Interface**: AWS Amplify hosts a Next.js app for real-time dashboards and analytics.
- **User Management**: Amazon Cognito manages user access, allowing up to 5 active accounts.

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

![AWS Pricing](/images/2-Proposal/anh1.png)

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

For the project team, this project is not only a product for the internship report but also a great opportunity to apply web development, database management, and cloud computing knowledge to a complete system. Through the deployment process, the team gained experience in requirement analysis, architecture design, AWS integration, and team collaboration.