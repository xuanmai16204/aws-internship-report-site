---
title: "Kiểm tra môi trường triển khai"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 5.2.1. </b> "
---

#### Mục tiêu

Trước khi bắt đầu quy trình upload tài liệu, cần kiểm tra các thành phần chính của hệ thống để đảm bảo môi trường đã sẵn sàng. Việc xác minh trước sẽ giúp giảm thiểu các lỗi phát sinh trong quá trình thực hiện những bước tiếp theo.

#### Các bước xác minh môi trường

Thực hiện lần lượt các bước kiểm tra dưới đây.

**Bước 1:** Kiểm tra website frontend có thể truy cập bình thường thông qua CloudFront.

![Kiểm tra CloudFront](/images/5-Workshop/5.2-Prerequisite/anh1.png)

**Bước 2:** Kiểm tra Amazon S3 Bucket đã được tạo và sẵn sàng lưu trữ tài liệu.

![Kiểm tra Amazon S3](/images/5-Workshop/5.2-Prerequisite/anh2.png)

**Bước 3:** Kiểm tra Amazon EC2 đang hoạt động để backend có thể tiếp nhận và xử lý yêu cầu.

![Kiểm tra Amazon EC2](/images/5-Workshop/5.2-Prerequisite/anh3.png)

**Bước 4:** Kiểm tra Amazon RDS PostgreSQL đang hoạt động và có thể sử dụng để lưu metadata.

![Kiểm tra Amazon RDS](/images/5-Workshop/5.2-Prerequisite/anh4.png)

{{% notice info %}}
Nên hoàn thành đầy đủ các bước kiểm tra trước khi tiếp tục workshop để hạn chế các lỗi phát sinh trong quá trình triển khai.
{{% /notice %}}

#### Kết quả mong đợi

Sau khi hoàn thành bước kiểm tra, toàn bộ các thành phần của hệ thống đều ở trạng thái sẵn sàng để thực hiện quy trình upload và kiểm thử trong các phần tiếp theo.
