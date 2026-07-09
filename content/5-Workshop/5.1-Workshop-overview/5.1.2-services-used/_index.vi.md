---
title: "Dịch vụ sử dụng"
date: 2026-04-17
weight: 2
chapter: false
pre: " <b> 5.1.2. </b> "
---

#### Các thành phần chính

Workshop CloudDoc sử dụng một số dịch vụ AWS để xây dựng và vận hành hệ thống:

- **Amazon S3** lưu trữ tài liệu do người dùng tải lên và các tệp tĩnh của frontend.
- **Amazon CloudFront** phân phối nội dung tĩnh đến người dùng thông qua CDN.
- **Amazon EC2** chạy backend API và xử lý các yêu cầu từ ứng dụng.
- **Amazon RDS PostgreSQL** lưu trữ metadata và các thông tin phục vụ cho hệ thống.
- **Amazon CloudWatch** theo dõi log, metric và hỗ trợ giám sát hoạt động của hệ thống.

#### Vai trò của từng dịch vụ

Mỗi dịch vụ đảm nhận một vai trò riêng trong quy trình xử lý tài liệu:

1. Amazon S3 lưu trữ tệp, giúp backend không cần xử lý trực tiếp các file có dung lượng lớn.
2. Amazon EC2 tiếp nhận yêu cầu từ frontend, xử lý nghiệp vụ và tạo presigned URL cho quá trình upload.
3. Amazon RDS PostgreSQL lưu metadata, trạng thái tài liệu và các thông tin liên quan.
4. Amazon CloudFront phân phối các tệp tĩnh của frontend để người dùng truy cập nhanh hơn.
5. Amazon CloudWatch hỗ trợ theo dõi hoạt động của hệ thống và phát hiện các vấn đề trong quá trình vận hành.

#### Ghi chú về bảo mật và vận hành

Trong quá trình triển khai, nhóm áp dụng một số nguyên tắc nhằm tăng tính an toàn cho hệ thống. Các quyền truy cập được cấp theo nhu cầu sử dụng, hạn chế sử dụng tài khoản có quyền cao và tránh lưu trữ thông tin nhạy cảm trong mã nguồn. Ngoài ra, CloudWatch được sử dụng để hỗ trợ theo dõi log và tình trạng hoạt động của hệ thống trong quá trình kiểm thử và vận hành.
