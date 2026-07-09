---
title: "Solution Architecture"
date: 2026-04-17
weight: 3
chapter: false
pre: " <b> 5.1.3. </b> "
---

#### Objectives

This section introduces the overall architecture of the CloudDoc system and how the main components cooperate to process documents. Through the diagram below, readers can visualize the data flow from when a user submits a request to when a document is stored and displayed on the system.

#### Reference Architecture

CloudDoc follows a layered architecture that separates the user interface, backend services, storage, and database. Each component has a dedicated responsibility, making the system easier to maintain and extend.

![CloudDoc Architecture](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)

#### Explanation by Layer

**Frontend**

Users interact with the system via a web interface to upload documents, search, and view information. The frontend sends the necessary requests to the backend and displays the returned results.

**Backend API**

The backend receives requests from the frontend, validates input data, processes business logic, and generates presigned URLs for uploading to Amazon S3. In addition, the backend is responsible for interacting with the database and other AWS services.

**Amazon S3**

Amazon S3 stores document files after they are uploaded. Storing files directly in S3 reduces the workload on the backend and supports handling large files more efficiently.

**Amazon RDS PostgreSQL**

The database stores document metadata such as file names, status, storage paths, and other necessary data for searching and management.

**CloudFront and CloudWatch**

CloudFront helps distribute static content to users more efficiently. Meanwhile, CloudWatch is used to monitor logs and system health during testing and operations.

#### Importance to the Workshop

Presenting the architecture at the beginning helps readers connect the overall diagram to the implementation steps in the following sections. In each section of the workshop, each AWS service is illustrated with corresponding actions and screenshots to highlight its role in the CloudDoc system.
