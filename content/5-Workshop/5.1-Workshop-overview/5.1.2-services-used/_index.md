---
title: "Services Used"
date: 2026-04-17
weight: 2
chapter: false
pre: " <b> 5.1.2. </b> "
---

#### Main Components

The CloudDoc workshop uses several AWS services to build and operate the system:

- **Amazon S3** stores uploaded documents and frontend static assets.
- **Amazon CloudFront** delivers static content to users through a CDN.
- **Amazon EC2** hosts the backend API and processes application requests.
- **Amazon RDS PostgreSQL** stores document metadata and system information.
- **Amazon CloudWatch** collects logs, metrics, and monitors system activity.

#### Role of Each Service

Each AWS service has a specific responsibility within the document workflow:

1. Amazon S3 stores uploaded files, reducing the workload on the backend.
2. Amazon EC2 processes requests from the frontend and generates presigned URLs for file uploads.
3. Amazon RDS PostgreSQL stores metadata, document status, and related information.
4. Amazon CloudFront delivers frontend static assets with lower latency.
5. Amazon CloudWatch helps monitor system performance and detect operational issues.

#### Security and Operations Notes

During implementation, the project follows several security best practices. Permissions are assigned according to actual requirements, high-privilege accounts are used only when necessary, and sensitive information is not stored directly in the source code. CloudWatch is also used to monitor logs and system health throughout testing and deployment.
