---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# INTEGRATING IAM COMPUTE ROLES FOR SERVER-SIDE RENDERING APPLICATIONS ON AWS AMPLIFY HOSTING

When building Server-Side Rendering (SSR) applications such as Next.js or Nuxt on AWS, one of the common challenges is how the application can access AWS services securely without storing Access Keys or Secret Keys in the source code or environment variables.

To address this need, AWS Amplify Hosting has introduced the IAM Compute Roles feature for SSR applications.

### 1. What are IAM Compute Roles?

IAM Compute Roles allow attaching an IAM Role directly to the execution environment of an SSR application on Amplify Hosting.

Consequently, server-side code can access AWS services through a temporary credential mechanism, similar to EC2 Instance Profiles or Lambda Execution Roles.

### 2. Common Use Cases

• Accessing AWS Secrets Manager or Systems Manager Parameter Store to retrieve configuration details.
• Connecting to Amazon RDS or Amazon DynamoDB without storing credentials inside the application.
• Making API calls to AWS services from the server side.
• Setting up distinct access permissions across development, staging, and production environments.

### 3. Deployment Example

In the AWS tutorial, a Next.js application is configured to access a private Amazon S3 bucket.

The process involves:
1. Creating an IAM Role with permissions to read data from S3.
2. Granting permissions for Amplify Hosting to assume this role.
3. Deploying the Next.js application to Amplify.
4. Using the AWS SDK within API Routes to access data from S3.

Thanks to IAM Compute Roles, the application can authenticate with AWS without storing Access Keys or Secret Keys in the source code.

### 4. Conclusion

IAM Compute Roles simplify AWS access management for SSR applications on Amplify Hosting. This is a beneficial feature for systems that need server-side access to AWS resources while adhering to security principles and access-control governance.

📖 Original Article:
https://aws.amazon.com/blogs/mobile/iam-compute-roles-for-server-side-rendering-with-aws-amplify-hosting/

#AWS #AWSAmplify #IAM #SSR #NextJS #CloudSecurity
