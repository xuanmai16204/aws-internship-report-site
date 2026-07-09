---
title: "Tích hợp ứng dụng khách và quan sát hệ thống"
date: 2026-04-17
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

#### Mục tiêu

Sau khi tài liệu được phê duyệt, hệ thống cần hỗ trợ người dùng truy cập và sử dụng tài liệu một cách an toàn. Đồng thời, việc theo dõi hoạt động của hệ thống cũng rất quan trọng để kịp thời phát hiện và xử lý các vấn đề trong quá trình vận hành.

#### Các bước tích hợp và quan sát

**Bước 1:** Frontend lấy dữ liệu tài liệu từ backend thông qua CloudFront để đảm bảo khả năng truy cập và hiệu năng.

![CloudFront Distribution](/images/5-Workshop/5.5-Policy/anh1.png)

**Bước 2:** Khi người dùng chọn tài liệu đã được phê duyệt, frontend gửi yêu cầu đến backend để lấy URL phục vụ xem trước hoặc tải tài liệu.

![Preview và Download tài liệu](/images/5-Workshop/5.5-Policy/anh2.png)

**Bước 3:** Amazon CloudWatch được sử dụng để theo dõi log và metric của hệ thống trong quá trình vận hành.

![CloudWatch Monitoring](/images/5-Workshop/5.5-Policy/anh3.png)

**Bước 4:** Thiết lập CloudWatch Alarm để theo dõi các chỉ số quan trọng và cảnh báo khi phát hiện dấu hiệu bất thường.

![CloudWatch Alarm](/images/5-Workshop/5.5-Policy/anh4.png)

#### Ghi chú kỹ thuật

Việc kết hợp CloudFront với CloudWatch giúp cải thiện hiệu năng truy cập tài liệu, đồng thời hỗ trợ giám sát hoạt động của hệ thống trong quá trình vận hành.
