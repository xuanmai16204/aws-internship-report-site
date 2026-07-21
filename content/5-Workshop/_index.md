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

## CloudDoc Demo Video

This section provides a demonstration video of the CloudDoc system developed during the First Cloud AI Journey (FCAJ) internship program.

The video showcases the user interface and the main features of the application, providing an overview of how users interact with the CloudDoc system.

{{% button href="https://drive.google.com/drive/folders/1-mvKrbzs08WWHUT0-whSGeNwgtwd4Uid?usp=sharing" icon="fab fa-google-drive" %}}
🎥 Watch CloudDoc Demo Video
{{% /button %}}

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

1. [Introduction]({{% relref "5.1-Workshop-overview" %}})
2. [Prerequisites]({{% relref "5.2-Prerequiste" %}})
3. [Implementing the Upload and Storage Workflow]({{% relref "5.3-S3-vpc" %}})
4. [End-to-End System Testing]({{% relref "5.4-S3-onprem" %}})
5. [Client Integration and System Monitoring]({{% relref "5.5-Policy" %}})
6. [Data Update]({{% relref "5.6-Cleanup" %}})
7. [Resource Cleanup]({{% relref "5.7-clean-resources" %}})