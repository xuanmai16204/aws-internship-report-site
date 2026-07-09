---
title: "Chuẩn bị dữ liệu và cấu hình hệ thống"
date: 2026-04-17
weight: 2
chapter: false
pre: " <b> 5.2.2. </b> "
---

#### Mục tiêu

Sau khi môi trường triển khai đã sẵn sàng, bước tiếp theo là chuẩn bị dữ liệu và kiểm tra các cấu hình cần thiết trước khi bắt đầu quy trình upload tài liệu. Việc xác nhận các thiết lập này sẽ giúp các bước thực hành tiếp theo diễn ra ổn định.

#### Các bước thực hiện

**Bước 1:** Kiểm tra cấu hình CORS của Amazon S3 Bucket để frontend có thể gửi yêu cầu upload theo đúng thiết lập.

![CORS Configuration](/images/5-Workshop/5.2-Prerequisite/anh5.png)

**Bước 2:** Kiểm tra thiết lập Public Access của Bucket nhằm đảm bảo quyền truy cập được cấu hình phù hợp.

![Public Access](/images/5-Workshop/5.2-Prerequisite/anh6.png)

**Bước 3:** Kiểm tra cấu hình Static Website Hosting để xác nhận website có thể hoạt động đúng sau khi triển khai.

![Static Website Hosting](/images/5-Workshop/5.2-Prerequisite/anh7.png)

{{% notice info %}}
Nên kiểm tra lại toàn bộ các cấu hình trước khi thực hiện các bước tiếp theo để hạn chế những lỗi liên quan đến quyền truy cập hoặc kết nối giữa các thành phần của hệ thống.
{{% /notice %}}

#### Kết quả mong đợi

Sau khi hoàn thành bước chuẩn bị, các cấu hình cần thiết đã sẵn sàng để phục vụ quá trình upload tài liệu và các nội dung tiếp theo của workshop.
