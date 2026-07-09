---
title: "What is CloudDoc?"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 5.1.1. </b> "
---

#### Definition

CloudDoc is a document management and sharing system built on AWS. Users can upload documents through a web interface, while the backend processes requests, stores metadata in the database, and works with Amazon S3 to manage uploaded files. Before becoming available to other users, every document must be reviewed and approved by an administrator.

#### Project Requirements

CloudDoc was developed to address several key requirements:

- allow users to upload documents quickly through a web interface;
- reduce backend workload by storing files directly in Amazon S3;
- store document metadata for searching, moderation, and management;
- track document status throughout the processing workflow;
- support system monitoring and AWS resource management.

#### Why Is This Workflow Important?

Uploading a file is only one step in a document management system. After a file is uploaded, its metadata must be recorded, the document must be reviewed, and its status must be updated before it becomes available to users. This workshop demonstrates the complete workflow so readers can better understand how different components work together.

#### Document Lifecycle in CloudDoc

Each document goes through the following stages:

1. `pending`: the document has been uploaded and is waiting for approval.
2. `approved`: the document has been reviewed and approved by an administrator.
3. `available`: the document is available for searching, previewing, and downloading.

Tracking these stages makes it easier to verify the complete document workflow during implementation and testing.
