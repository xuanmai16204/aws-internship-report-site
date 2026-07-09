---
title: "CloudDoc là gì?"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 5.1.1. </b> "
---

#### Định nghĩa

CloudDoc là hệ thống hỗ trợ quản lý và chia sẻ tài liệu học tập được xây dựng trên nền tảng AWS. Người dùng có thể tải tài liệu lên thông qua giao diện web, trong khi backend chịu trách nhiệm xử lý yêu cầu, lưu metadata vào cơ sở dữ liệu và phối hợp với Amazon S3 để quản lý tệp. Trước khi được hiển thị cho mọi người, tài liệu sẽ được quản trị viên xem xét và phê duyệt.

#### Bài toán dự án cần giải quyết

CloudDoc được xây dựng nhằm đáp ứng một số yêu cầu chính của hệ thống:

- cho phép người dùng tải tài liệu lên nhanh chóng thông qua giao diện web;
- giảm tải cho backend bằng cách lưu tệp trực tiếp trên Amazon S3;
- lưu trữ metadata để phục vụ tìm kiếm, kiểm duyệt và quản lý tài liệu;
- theo dõi trạng thái của tài liệu trong suốt quá trình xử lý;
- hỗ trợ giám sát hoạt động của hệ thống và quản lý tài nguyên trên AWS.

#### Vì sao workflow này quan trọng?

Một hệ thống quản lý tài liệu không chỉ dừng lại ở việc lưu tệp thành công. Sau khi upload, tài liệu cần được ghi nhận metadata, trải qua bước kiểm duyệt và cập nhật trạng thái trước khi có thể hiển thị cho người dùng. Vì vậy, workshop này mô phỏng đầy đủ quy trình xử lý tài liệu để giúp người đọc dễ hình dung cách các thành phần trong hệ thống phối hợp với nhau.

#### Vòng đời tài liệu trong CloudDoc

Trong CloudDoc, tài liệu sẽ lần lượt trải qua các trạng thái sau:

1. `pending`: tài liệu đã được tải lên và đang chờ kiểm duyệt.
2. `approved`: tài liệu đã được quản trị viên phê duyệt.
3. `available`: tài liệu được hiển thị trên hệ thống để người dùng tìm kiếm, xem trước và tải xuống.

Việc theo dõi các trạng thái này giúp nhóm kiểm tra được toàn bộ luồng xử lý của hệ thống trong quá trình triển khai và thử nghiệm.
