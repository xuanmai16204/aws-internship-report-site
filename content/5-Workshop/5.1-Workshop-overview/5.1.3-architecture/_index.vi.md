---
title: "Kiến trúc giải pháp"
date: 2026-04-17
weight: 3
chapter: false
pre: " <b> 5.1.3. </b> "
---

#### Mục tiêu

Phần này giới thiệu kiến trúc tổng thể của hệ thống CloudDoc và cách các thành phần chính phối hợp trong quá trình xử lý tài liệu. Thông qua sơ đồ bên dưới, người đọc có thể hình dung được luồng dữ liệu từ khi người dùng gửi yêu cầu cho đến khi tài liệu được lưu trữ và hiển thị trên hệ thống.

#### Sơ đồ tham chiếu

Kiến trúc CloudDoc được xây dựng theo mô hình tách biệt giữa giao diện người dùng, backend, dịch vụ lưu trữ và cơ sở dữ liệu. Mỗi thành phần đảm nhận một nhiệm vụ riêng, giúp hệ thống dễ quản lý và thuận tiện cho việc mở rộng sau này.

![CloudDoc Architecture](/images/5-Workshop/5.1-Workshop-overview/diagram1.png)

#### Giải thích theo từng lớp

**Frontend**

Người dùng thao tác với hệ thống thông qua giao diện web để tải tài liệu, tìm kiếm và xem thông tin. Frontend gửi các yêu cầu cần thiết đến backend và hiển thị kết quả trả về.

**Backend API**

Backend tiếp nhận yêu cầu từ frontend, kiểm tra dữ liệu đầu vào, xử lý nghiệp vụ và tạo presigned URL để hỗ trợ quá trình upload lên Amazon S3. Đồng thời, backend cũng chịu trách nhiệm làm việc với cơ sở dữ liệu và các dịch vụ AWS khác.

**Amazon S3**

Amazon S3 lưu trữ các tệp tài liệu sau khi được tải lên. Việc upload trực tiếp lên S3 giúp giảm tải cho backend và hỗ trợ xử lý các tệp có dung lượng lớn hiệu quả hơn.

**Amazon RDS PostgreSQL**

Cơ sở dữ liệu lưu thông tin của tài liệu như tên, trạng thái, đường dẫn lưu trữ và các dữ liệu cần thiết khác phục vụ cho việc tìm kiếm và quản lý.

**CloudFront và CloudWatch**

CloudFront hỗ trợ phân phối nội dung tĩnh đến người dùng với tốc độ ổn định hơn. Trong khi đó, CloudWatch được sử dụng để theo dõi log và tình trạng hoạt động của hệ thống trong quá trình kiểm thử và vận hành.

#### Ý nghĩa đối với workshop

Việc trình bày kiến trúc ngay từ đầu giúp người đọc dễ liên hệ giữa sơ đồ tổng thể và các bước thực hiện ở những phần sau. Khi đi vào từng nội dung của workshop, mỗi dịch vụ AWS sẽ được minh họa bằng các thao tác và hình ảnh tương ứng để thể hiện rõ vai trò trong hệ thống CloudDoc.
