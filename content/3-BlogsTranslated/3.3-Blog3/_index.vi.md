---
title: "Blog 3"
date: 2026-06-13
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# TÍCH HỢP IAM COMPUTE ROLES CHO ỨNG DỤNG SERVER-SIDE RENDERING TRÊN AWS AMPLIFY HOSTING

Khi xây dựng các ứng dụng Server-Side Rendering như Next.js hoặc Nuxt trên AWS, một trong những vấn đề thường gặp là làm sao để ứng dụng có thể truy cập các dịch vụ AWS một cách an sau mà không phải lưu trữ Access Key hoặc Secret Key trong mã nguồn hay biến môi trường.

Để giải quyết nhu cầu này, AWS Amplify Hosting đã giới thiệu tính năng IAM Compute Roles dành cho các ứng dụng SSR.

### 1. IAM Compute Roles là gì?

IAM Compute Roles cho phép gắn trực tiếp IAM Role vào môi trường thực thi của ứng dụng SSR trên Amplify Hosting.

Nhờ đó, mã nguồn phía server có thể truy cập các dịch vụ AWS thông qua cơ chế cấp quyền tạm thời tương tự như EC2 Instance Profile hoặc Lambda Execution Role.

### 2. Các trường hợp sử dụng phổ biến

• Truy cập AWS Secrets Manager hoặc Systems Manager Parameter Store để lấy thông tin cấu hình.
• Kết nối đến Amazon RDS hoặc Amazon DynamoDB mà không cần lưu credentials trong ứng dụng.
• Gọi API đến các dịch vụ AWS từ phía server.
• Thiết lập quyền truy cập khác nhau giữa các môi trường development, staging và production.

### 3. Ví dụ triển khai

Trong bài hướng dẫn của AWS, ứng dụng Next.js được cấu hình để truy cập một Amazon S3 bucket ở chế độ private.

Quy trình gồm:
1.	Tạo IAM Role với quyền đọc dữ liệu từ S3.
2.	Cấp quyền để Amplify Hosting sử dụng role này.
3.	Triển khai ứng dụng Next.js lên Amplify.
4.	Sử dụng AWS SDK trong API Route để truy cập dữ liệu từ S3.

Nhờ IAM Compute Roles, ứng dụng có thể xác thực với AWS mà không cần lưu Access Key hoặc Secret Key trong mã nguồn.

### 4. Kết luận

IAM Compute Roles giúp đơn giản hóa việc quản lý quyền truy cập AWS cho các ứng dụng SSR trên Amplify Hosting. Đây là một tính năng hữu ích cho các hệ thống cần truy cập tài nguyên AWS từ phía server nhưng vẫn muốn đảm bảo các nguyên tắc bảo mật và quản trị quyền truy cập.

📖 Bài viết gốc:
https://aws.amazon.com/blogs/mobile/iam-compute-roles-for-server-side-rendering-with-aws-amplify-hosting/

#AWS #AWSAmplify #IAM #SSR #NextJS #CloudSecurity
