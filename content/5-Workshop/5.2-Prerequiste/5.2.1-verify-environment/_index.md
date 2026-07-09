---
title: "Verify the Deployment Environment"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 5.2.1. </b> "
---

#### Objectives

Before starting the document upload workflow, the main system components should be verified to ensure that the deployment environment is ready. This helps reduce unexpected issues during the following implementation steps.

#### Environment Verification Steps

Complete the following checks before continuing.

**Step 1:** Verify that the frontend website is accessible through CloudFront.

![Check CloudFront](/images/5-Workshop/5.2-Prerequisite/image1.png)

**Step 2:** Verify that the Amazon S3 bucket has been created and is ready to store uploaded files.

![Check Amazon S3](/images/5-Workshop/5.2-Prerequisite/image2.png)

**Step 3:** Verify that the Amazon EC2 instance is running and ready to process backend requests.

![Check Amazon EC2](/images/5-Workshop/5.2-Prerequisite/image3.png)

**Step 4:** Verify that Amazon RDS PostgreSQL is available for storing document metadata.

![Check Amazon RDS](/images/5-Workshop/5.2-Prerequisite/image4.png)

{{% notice info %}}
Complete these verification steps before continuing to ensure a stable deployment environment.
{{% /notice %}}

#### Expected Results

After completing these checks, all required system components should be ready for the document upload workflow and the remaining workshop activities.
