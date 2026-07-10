---
title: "Giới thiệu"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

#### Mục tiêu

Phần này giúp người đọc có cái nhìn tổng quan về workshop và quy trình xử lý tài liệu của hệ thống CloudDoc. Trước khi bắt đầu các bước triển khai, việc hiểu được vai trò của frontend, backend, cơ sở dữ liệu và các dịch vụ AWS sẽ giúp dễ theo dõi hơn trong các phần tiếp theo.

#### Bối cảnh bài toán

Trong một hệ thống quản lý tài liệu, việc tải tệp lên chỉ là bước đầu của toàn bộ quy trình. Sau khi người dùng gửi tài liệu, hệ thống cần lưu trữ tệp, ghi nhận thông tin, kiểm duyệt nội dung và cập nhật trạng thái trước khi tài liệu được hiển thị cho người dùng khác. Nếu toàn bộ quá trình upload đều đi qua backend, hệ thống sẽ tiêu tốn nhiều tài nguyên hơn khi số lượng hoặc dung lượng tệp tăng lên. Vì vậy, CloudDoc sử dụng cơ chế upload trực tiếp lên Amazon S3 bằng presigned URL để giảm tải cho backend nhưng vẫn đảm bảo việc quản lý dữ liệu.

#### Luồng tổng quát của workshop

Workshop được xây dựng dựa trên quy trình xử lý tài liệu gồm các bước sau:

1. Người dùng nhập thông tin và chọn tài liệu cần tải lên.
2. Backend tiếp nhận yêu cầu và tạo presigned URL phục vụ việc upload.
3. Trình duyệt gửi tệp trực tiếp lên Amazon S3 thông qua URL được cấp.
4. Metadata của tài liệu được lưu vào cơ sở dữ liệu với trạng thái `pending`.
5. Quản trị viên kiểm tra và phê duyệt tài liệu.
6. Sau khi được phê duyệt, tài liệu sẽ hiển thị trên hệ thống để người dùng tìm kiếm, xem trước hoặc tải xuống.

#### Các nội dung tiếp theo

Ba mục dưới đây sẽ lần lượt giới thiệu những nội dung nền tảng của workshop:

1. [CloudDoc là gì?]({{% relref "5.1.1-what-is-clouddoc" %}})
2. [Dịch vụ sử dụng]({{% relref "5.1.2-services-used" %}})
3. [Kiến trúc giải pháp]({{% relref "5.1.3-architecture" %}})
