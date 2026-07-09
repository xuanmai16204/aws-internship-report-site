---
title: "Initialize the Upload Workflow"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 5.3.1. </b> "
---

#### Objectives

The purpose of this step is to initialize a valid upload request from the CloudDoc interface and transfer the document to Amazon S3. This is the starting point of the upload workflow and ensures that the frontend and backend communicate correctly.

#### Implementation Steps

1. The user selects a document and enters the required information.
2. The frontend sends a request to the backend to obtain a presigned upload URL.
3. The backend validates the request, generates a storage key, and returns the presigned URL.
4. The frontend uploads the document directly to Amazon S3 using the **PUT** method.
5. After the upload is completed, the frontend sends another request to store the document metadata in the database.

#### Expected Results

After completing this step, the document is stored successfully in Amazon S3 and its metadata is saved in the database. The system is then ready for the following stages, including document moderation, searching, and preview.