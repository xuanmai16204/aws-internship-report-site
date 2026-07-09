---
title: "Verify Storage and Data Synchronization"
date: 2026-04-17
weight: 2
chapter: false
pre: " <b> 5.3.2. </b> "
---

#### Objectives

After the upload process is completed, both the uploaded file and its metadata should be verified to ensure they have been recorded correctly. This confirmation allows the document to continue through the remaining CloudDoc workflow.

#### Storage Verification Steps

After the upload is completed, perform the following checks:

**Step 1:** Verify that the uploaded file appears in the Amazon S3 bucket. A newly created object indicates that the presigned URL upload process has completed successfully.

![Uploaded document stored in Amazon S3](/images/5-Workshop/5.3-S3-vpc/anh6.png)

**Step 2:** Confirm that the document metadata has been saved in the database.

**Step 3:** Verify that the document appears in the administrator moderation area.

**Step 4:** Confirm that the initial document status is set to **pending**.

#### Expected Results

At the end of this step, the uploaded document is stored in Amazon S3, its metadata has been recorded successfully, and the document is ready to proceed through the CloudDoc moderation workflow.
