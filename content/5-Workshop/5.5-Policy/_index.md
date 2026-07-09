---
title: "Client Integration and System Monitoring"
date: 2026-04-17
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

#### Objectives

After a document has been approved, users should be able to access it securely. In addition, monitoring system activities is essential for maintaining service availability and identifying operational issues.

#### Integration and Monitoring Steps

**Step 1:** The frontend retrieves document information from the backend through CloudFront to improve performance and accessibility.

![CloudFront Distribution](/images/5-Workshop/5.5-Policy/anh1.png)

**Step 2:** When a user opens an approved document, the frontend requests a secure URL from the backend for previewing or downloading the file.

![Document Preview and Download](/images/5-Workshop/5.5-Policy/anh2.png)

**Step 3:** Amazon CloudWatch is used to collect logs and metrics for monitoring the application during runtime.

![CloudWatch Monitoring](/images/5-Workshop/5.5-Policy/anh3.png)

**Step 4:** Configure CloudWatch Alarms to monitor important metrics and generate notifications when abnormal conditions are detected.

![CloudWatch Alarm](/images/5-Workshop/5.5-Policy/anh4.png)

#### Technical Notes

Using CloudFront together with CloudWatch improves document delivery performance while providing better visibility into the operational status of the application.
