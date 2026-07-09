---
title: "Workshop"
date: 2026-04-17
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# XÂY DỰNG HỆ THỐNG CLOUDDOC TRÊN AWS

#### Tổng quan workshop

Workshop này trình bày quá trình xây dựng và triển khai hệ thống CloudDoc trên nền tảng AWS. CloudDoc là ứng dụng hỗ trợ lưu trữ và chia sẻ tài liệu, trong đó người dùng tải tài liệu lên thông qua giao diện web, backend tiếp nhận và xử lý yêu cầu, Amazon S3 đảm nhiệm việc lưu trữ tệp, cơ sở dữ liệu lưu thông tin của tài liệu và quản trị viên thực hiện kiểm duyệt trước khi tài liệu được hiển thị cho người dùng.

Nội dung workshop được sắp xếp theo đúng quy trình hoạt động của hệ thống, bắt đầu từ bước chuẩn bị môi trường, kiểm tra hạ tầng, thực hiện tải tài liệu, xác nhận dữ liệu được lưu trên AWS, kiểm thử các chức năng và hoàn tất bằng việc dọn dẹp tài nguyên sau khi kết thúc. Cách trình bày này giúp người đọc dễ theo dõi từng bước triển khai cũng như hiểu được cách các dịch vụ AWS phối hợp với nhau trong dự án.

#### Mục tiêu

Sau khi hoàn thành workshop, người đọc có thể:

- hiểu vai trò của các thành phần trong hệ thống CloudDoc;
- theo dõi quy trình xử lý tài liệu từ lúc tải lên đến khi được phê duyệt;
- đối chiếu các bước thực hiện với hình ảnh trên AWS Console;
- tham khảo cách frontend và backend phối hợp trong quá trình xử lý tài liệu;
- quan sát quy trình kiểm tra hệ thống và quản lý tài nguyên sau khi triển khai.

#### Kết quả mong đợi

Sau khi thực hiện đầy đủ các bước trong workshop, hệ thống có thể tiếp nhận tài liệu từ người dùng, lưu trữ tệp và metadata đúng vị trí, hỗ trợ kiểm duyệt tài liệu trước khi công khai và cho phép người dùng tìm kiếm, xem trước hoặc tải xuống các tài liệu đã được phê duyệt. Bên cạnh đó, quá trình vận hành của hệ thống cũng được theo dõi để phục vụ việc kiểm tra và đánh giá.

#### Cấu trúc workshop

1. Giới thiệu
2. Điều kiện tiên quyết
3. Triển khai luồng upload và lưu trữ tài liệu
4. Kiểm thử hệ thống end-to-end
5. Tích hợp ứng dụng khách và quan sát hệ thống
6. Cập nhật dữ liệu
7. Dọn dẹp tài nguyên