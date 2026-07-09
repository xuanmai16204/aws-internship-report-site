---
title: "Implementing the Document Upload and Storage Workflow"
date: 2026-04-17
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

#### Objectives

This section describes how CloudDoc uploads documents to Amazon S3 by using presigned URLs. It illustrates the interaction between the frontend and backend while demonstrating the complete upload workflow.

#### Main Components

The upload workflow includes:

- Frontend upload form.
- Presigned upload URL API.
- Amazon S3 bucket for document storage.
- Database for storing document metadata.

#### Typical Workflow

Instead of sending the uploaded file through the backend, CloudDoc validates the request, generates a storage key and a presigned URL, then allows the browser to upload the file directly to Amazon S3. After the upload is completed, the frontend submits another request to save the document metadata in the database.

#### Code Snippet

![Generate Presigned URL](/images/5-Workshop/5.3-S3-vpc/anh1.png)

![Presigned Upload API](/images/5-Workshop/5.3-S3-vpc/anh2.png)

#### Upload Workflow

**Step 1:** The user enters the document information and selects a file from the CloudDoc interface.

![CloudDoc Upload Form](/images/5-Workshop/5.3-S3-vpc/anh3.png)

**Step 2:** The system generates a presigned URL and uploads the selected file directly to Amazon S3.

![Uploading File to Amazon S3](/images/5-Workshop/5.3-S3-vpc/anh4.png)

**Step 3:** After the upload and metadata storage are completed, the system displays a success notification.

![Upload Completed Successfully](/images/5-Workshop/5.3-S3-vpc/anh5.png)

#### Next Steps

1. Initialize the upload workflow.
2. Verify storage and data synchronization.