---
title: "Prepare Data and System Configuration"
date: 2026-04-17
weight: 2
chapter: false
pre: " <b> 5.2.2. </b> "
---

#### Objectives

After verifying the deployment environment, the next step is to prepare the required data and review the system configuration before starting the document upload workflow. This helps ensure that the following implementation steps can be completed smoothly.

#### Implementation Steps

**Step 1:** Verify the Amazon S3 Bucket CORS configuration to allow upload requests from the frontend.

![CORS Configuration](/images/5-Workshop/5.2-Prerequisite/anh5.png)

**Step 2:** Review the Bucket Public Access settings to ensure the required permissions are configured correctly.

![Public Access](/images/5-Workshop/5.2-Prerequisite/anh6.png)

**Step 3:** Verify the Static Website Hosting configuration to confirm that the website can be accessed correctly after deployment.

![Static Website Hosting](/images/5-Workshop/5.2-Prerequisite/anh7.png)

{{% notice info %}}
Review these configurations before continuing to reduce permission or connectivity issues during the remaining workshop activities.
{{% /notice %}}

#### Expected Results

After completing this section, the required configuration is ready for the document upload workflow and the remaining workshop activities.
