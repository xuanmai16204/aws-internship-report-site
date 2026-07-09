---
title: "Introduction"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

#### Objectives

This section provides an overview of the workshop and the document processing workflow used in the CloudDoc system. Before starting the implementation steps, understanding the responsibilities of the frontend, backend, database, and AWS services will make the following sections easier to follow.

#### Background

In a document management system, uploading a file is only the first step of the overall workflow. After a document is submitted, the system must store the file, record its metadata, review the content, and update its status before making it available to other users. If every upload request is processed directly through the backend, the application may consume more resources as the number or size of uploaded files increases. To address this, CloudDoc uses presigned URLs so that files are uploaded directly to Amazon S3 while the backend manages the business logic.

#### Overall Workflow

The workshop follows the document processing workflow below:

1. The user enters document information and selects a file to upload.
2. The backend receives the request and generates a presigned URL.
3. The browser uploads the file directly to Amazon S3.
4. The document metadata is stored in the database with a `pending` status.
5. An administrator reviews and approves the document.
6. Once approved, the document becomes available for searching, previewing, and downloading.

#### Next Sections

The following sections introduce the main concepts used throughout the workshop:

1. What is CloudDoc?
2. Services Used
3. Solution Architecture