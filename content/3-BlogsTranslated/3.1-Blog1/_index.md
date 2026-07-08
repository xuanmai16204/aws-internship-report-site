---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# BUILDING OFFLINE-FIRST APPLICATIONS WITH AWS AMPLIFY, TANSTACK QUERY, APPSYNC, AND MONGODB ATLAS

When using web or mobile applications in unstable network conditions, users often experience slow data loading, interrupted operations, or even data loss when offline. To deliver a more seamless experience, many systems today adopt an Offline-First model combined with Optimistic UI.

A recent blog post from AWS introduces how to build this architecture by combining AWS Amplify, AWS AppSync, TanStack Query, and MongoDB Atlas.

### 1. Solution Overview

Architecture used:
• AWS Amplify Gen 2 to build and deploy full-stack applications.
• AWS AppSync providing a GraphQL API for data synchronization.
• TanStack Query managing client-side data, supporting caching and optimistic updates.
• MongoDB Atlas serving as the backend database.

Additionally, the system utilizes AWS Lambda for serverless processing and Amazon Cognito for user authentication.

### 2. How does Optimistic UI work?

Instead of waiting for a response from the server before updating the interface, Optimistic UI allows the application to display the expected outcome immediately after the user performs an action.

For example, when creating a new task in a To-do application:
• The UI displays the task immediately.
• A request is sent to AppSync to save the data.
• If the request succeeds, data is synchronized normally.
• If an error occurs or connection is lost, the previous state is restored via a rollback mechanism.

This approach makes the application more responsive and reduces the perceived waiting time for users.

### 3. Execution Flow

1.	The user performs a data creation operation.
2.	TanStack Query updates the local cache and displays the result immediately on the UI.
3.	The request is sent to AppSync via GraphQL.
4.	AppSync processes and saves the data to MongoDB Atlas.
5.	If an error occurs, cache data is restored to the previous state.

In the AWS example, the conflict resolution mechanism is implemented following the First-Come, First-Served principle.

### 4. Conclusion

Offline-First and Optimistic UI are becoming crucial techniques to improve user experience in modern applications. With Amplify, AppSync, and TanStack Query, implementing these features becomes simpler while still ensuring data synchronization when network connectivity is restored.

📖 Original Article:
https://aws.amazon.com/blogs/mobile/offline-caching-with-aws-amplify-tanstack-appsync-and-mongodb-atlas/

#AWS #AWSAmplify #AppSync #TanStackQuery #MongoDB #OfflineFirst
