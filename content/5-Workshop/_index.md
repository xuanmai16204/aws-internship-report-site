---
title: "Workshop"
date: 2026-04-17
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# BUILDING THE CLOUDDOC SYSTEM ON AWS

#### Workshop Overview

This workshop presents the implementation process of the CloudDoc system on AWS. CloudDoc is a document management and sharing application where users upload files through a web interface, the backend processes requests, Amazon S3 stores uploaded files, the database maintains document metadata, and administrators review documents before they become available to other users.

The workshop follows the actual workflow of the system, starting with environment preparation, infrastructure verification, document uploading, storage validation, feature testing, and ending with resource cleanup. This structure helps readers understand how AWS services work together throughout the project.

#### Objectives

After completing this workshop, readers will be able to:

- understand the role of each component in the CloudDoc system;
- follow the complete document processing workflow;
- compare each implementation step with the corresponding AWS Console screenshots;
- understand how the frontend and backend cooperate during document processing;
- observe how the system is tested and maintained after deployment.

#### Expected Results

Upon completing the workshop, the system will be able to receive uploaded documents, store files and metadata correctly, support the document approval process, and allow users to search, preview, and download approved documents. In addition, the operating status of the system can be monitored for validation and evaluation purposes.

#### Workshop Structure

1. Introduction
2. Prerequisites
3. Implementing the Upload and Storage Workflow
4. End-to-End System Testing
5. Client Integration and System Monitoring
6. Data Update
7. Resource Cleanup