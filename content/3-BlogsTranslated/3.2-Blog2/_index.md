---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# EMBEDDING A GENAI ASSISTANT INTO INTERNAL APPLICATIONS WITH AWS AMPLIFY, CDK, AND AMAZON Q BUSINESS

As the volume of internal documents grows, searching for information using traditional keywords often fails to meet user needs. Instead of searching through individual documents, many organizations are transitioning to AI assistants capable of answering questions in natural language based on corporate data.

An AWS blog post guides how to build this model using Amazon Q Business integrated with AWS Amplify and AWS CDK.

### 1. Solution Overview

Architecture used:
• Amazon Q Business to provide Q&A capabilities based on internal data.
• AWS Amplify Gen 2 to build and deploy the application.
• AWS CDK to manage infrastructure as code.
• Amazon Cognito and IAM Identity Center for authentication and authorization.
• Amazon S3 to store documents for the data indexing process.

### 2. Operating Architecture

1.	The user logs into the application via Cognito.
2.	Internal documents are uploaded to Amazon S3.
3.	Amazon Q Business is granted access and indexes the data from S3.
4.	The chat interface is embedded directly into the web application.
5.	Users can ask questions and receive answers based on business data, accompanied by reference sources.

### 3. Key Highlights

One aspect I find particularly useful is that most of the infrastructure setup and access permissions are implemented using AWS CDK. This significantly reduces manual configuration and facilitates environment management through Infrastructure as Code.

Additionally, using Amazon Q Business helps enterprises deploy GenAI features faster without having to build or operate their own AI models.

### 4. Conclusion

Integrating AI assistants into internal applications is becoming a common need across many organizations. The architecture using Amazon Q Business, Amplify, and CDK is a worthy reference approach for systems that need to secure and control the extraction of knowledge from corporate documents.

📖 Original Article:
https://aws.amazon.com/blogs/mobile/from-build-to-embed-creating-and-embedding-genai-apps-with-aws-amplify-cdk-and-amazon-q-business/

#AWS #AmazonQ #AWSAmplify #AWSCDK #GenerativeAI
