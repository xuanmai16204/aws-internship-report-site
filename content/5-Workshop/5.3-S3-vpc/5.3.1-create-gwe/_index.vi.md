---
title: "Khởi tạo luồng upload"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 5.3.1. </b> "
---

#### Mục tiêu

Mục tiêu của bước này là khởi tạo một yêu cầu upload hợp lệ từ giao diện CloudDoc và thực hiện quá trình lưu tài liệu lên Amazon S3. Đây là bước đầu tiên trong quy trình upload, đồng thời giúp kết nối giữa frontend và backend hoạt động đúng theo thiết kế của hệ thống.

#### Các bước thực hiện

1. Người dùng chọn tài liệu, nhập tiêu đề, mô tả và các thông tin cần thiết trên giao diện.
2. Frontend gửi yêu cầu đến backend để lấy presigned upload URL kèm theo thông tin của tài liệu.
3. Backend kiểm tra dữ liệu đầu vào, tạo khóa lưu trữ và trả về presigned URL.
4. Frontend sử dụng phương thức **PUT** để tải trực tiếp tài liệu lên Amazon S3.
5. Sau khi upload thành công, frontend tiếp tục gửi yêu cầu lưu metadata vào cơ sở dữ liệu.

#### Kết quả mong đợi

Sau khi hoàn thành bước này, tài liệu đã được lưu thành công trên Amazon S3 và metadata cũng được ghi nhận trong cơ sở dữ liệu. Đây là nền tảng để hệ thống tiếp tục thực hiện các bước kiểm duyệt, tìm kiếm và hiển thị tài liệu.
