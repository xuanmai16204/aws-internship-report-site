---
title: "Triển khai luồng upload và lưu trữ tài liệu"
date: 2026-04-17
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

#### Mục tiêu

Phần này trình bày quy trình đưa tài liệu từ giao diện CloudDoc lên Amazon S3 bằng cơ chế presigned URL. Đây là bước kết nối giữa frontend và backend, đồng thời minh họa quy trình upload tài liệu hoàn chỉnh của hệ thống thay vì chỉ mô phỏng giao diện.

#### Thành phần chính

Quy trình upload sử dụng các thành phần sau:

- Form upload trên giao diện người dùng.
- API tạo presigned upload URL.
- Amazon S3 Bucket lưu trữ tài liệu.
- Cơ sở dữ liệu lưu metadata của tài liệu.

#### Luồng xử lý tiêu biểu

Trong CloudDoc, backend không trực tiếp nhận file từ trình duyệt. Thay vào đó, backend xác thực yêu cầu, tạo khóa lưu trữ và sinh presigned URL. Sau khi nhận được URL, frontend tải file trực tiếp lên Amazon S3 rồi tiếp tục gửi yêu cầu lưu metadata vào cơ sở dữ liệu. Cách triển khai này giúp giảm tải cho backend và thuận tiện khi mở rộng hệ thống.

#### Code snippet

![Code tạo Presigned URL](/images/5-Workshop/5.3-S3-vpc/anh1.png)

![API xử lý Presigned Upload](/images/5-Workshop/5.3-S3-vpc/anh2.png)

#### Các bước thực hiện luồng upload

**Bước 1:** Người dùng nhập thông tin tài liệu và chọn tệp cần tải lên từ giao diện CloudDoc.

![Biểu mẫu upload tài liệu](/images/5-Workshop/5.3-S3-vpc/anh3.png)

**Bước 2:** Hệ thống tạo presigned URL và trình duyệt tải trực tiếp tệp lên Amazon S3.

![Quá trình upload lên Amazon S3](/images/5-Workshop/5.3-S3-vpc/anh4.png)

**Bước 3:** Sau khi upload hoàn tất và metadata được ghi nhận, hệ thống hiển thị thông báo thành công.

![Thông báo upload thành công](/images/5-Workshop/5.3-S3-vpc/anh5.png)

#### Các bước thực hiện

1. Khởi tạo luồng upload.
2. Kiểm tra lưu trữ và đồng bộ dữ liệu.