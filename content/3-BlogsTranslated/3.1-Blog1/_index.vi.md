---
title: "Blog 1"
date: 2026-06-13
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# XÂY DỰNG ỨNG DỤNG OFFLINE-FIRST VỚI AWS AMPLIFY, TANSTACK QUERY, APPSYNC VÀ MONGODB ATLAS

Khi sử dụng các ứng dụng web hoặc mobile trong điều kiện kết nối mạng không ổn định, người dùng thường gặp tình trạng dữ liệu tải chậm, thao tác bị gián đoạn hoặc thậm chí mất dữ liệu khi offline. Để mang lại trải nghiệm liền mạch hơn, nhiều hệ thống hiện nay áp dụng mô hình Offline-First kết hợp với Optimistic UI.

Một bài blog gần đây từ AWS giới thiệu cách xây dựng kiến trúc này bằng cách kết hợp AWS Amplify, AWS AppSync, TanStack Query và MongoDB Atlas.

### 1. Tổng quan giải pháp

Kiến trúc sử dụng:
• AWS Amplify Gen 2 để xây dựng và triển khai ứng dụng full-stack.
• AWS AppSync cung cấp GraphQL API cho việc đồng bộ dữ liệu.
• TanStack Query quản lý dữ liệu phía client, hỗ trợ caching và optimistic updates.
• MongoDB Atlas đóng vai trò cơ sở dữ liệu backend.

Ngoài ra, hệ thống còn sử dụng AWS Lambda cho xử lý serverless và Amazon Cognito cho xác thực người dùng.

### 2. Optimistic UI hoạt động như thế nào?

Thay vì chờ phản hồi từ server rồi mới cập nhật giao diện, Optimistic UI cho phép ứng dụng hiển thị kết quả dự kiến ngay sau khi người dùng thực hiện thao tác.

Ví dụ khi tạo một công việc mới trong ứng dụng To-do:
• Giao diện sẽ hiển thị công việc đó ngay lập tức.
• Request được gửi đến AppSync để lưu dữ liệu.
• Nếu request thành công, dữ liệu được đồng bộ như bình thường.
• Nếu xảy ra lỗi hoặc mất kết nối, trạng thái trước đó sẽ được khôi phục thông qua cơ chế rollback.

Cách tiếp cận này giúp ứng dụng phản hồi nhanh hơn và giảm cảm giác chờ đợi cho người dùng.

### 3. Luồng xử lý

1.	Người dùng thực hiện thao tác tạo dữ liệu.
2.	TanStack Query cập nhật cache cục bộ và hiển thị kết quả ngay trên giao diện.
3.	Request được gửi đến AppSync thông qua GraphQL.
4.	AppSync xử lý và lưu dữ liệu xuống MongoDB Atlas.
5.	Nếu xảy ra lỗi, dữ liệu cache được phục hồi về trạng thái trước đó.

Trong ví dụ của AWS, cơ chế xử lý xung đột được triển khai theo nguyên tắc First-Come, First-Served.

### 4. Kết luận

Offline-First và Optimistic UI đang trở thành những kỹ thuật quan trọng để cải thiện trải nghiệm người dùng trong các ứng dụng hiện đại. Với Amplify, AppSync và TanStack Query, việc triển khai các tính năng này trở nên đơn giản hơn mà vẫn đảm bảo khả năng đồng bộ dữ liệu khi kết nối mạng được khôi phục.

📖 Bài viết gốc:
https://aws.amazon.com/blogs/mobile/offline-caching-with-aws-amplify-tanstack-appsync-and-mongodb-atlas/

#AWS #AWSAmplify #AppSync #TanStackQuery #MongoDB #OfflineFirst
