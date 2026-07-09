---
title: "Kiểm tra lưu trữ và đồng bộ dữ liệu"
date: 2026-04-17
weight: 2
chapter: false
pre: " <b> 5.3.2. </b> "
---

#### Mục tiêu

Sau khi quá trình upload hoàn tất, cần kiểm tra để đảm bảo cả tệp tài liệu và metadata đều đã được hệ thống ghi nhận đầy đủ. Việc xác minh này giúp đảm bảo tài liệu có thể tiếp tục đi qua các bước xử lý tiếp theo của CloudDoc.

#### Các bước kiểm tra lưu trữ

Sau khi upload hoàn tất, thực hiện các bước kiểm tra sau:

**Bước 1:** Kiểm tra xem tệp đã xuất hiện trong Amazon S3 Bucket hay chưa. Nếu object mới được tạo thành công, điều đó cho thấy quá trình upload bằng presigned URL đã hoạt động đúng.

![Tệp tài liệu đã được lưu trong Amazon S3](/images/5-Workshop/5.3-S3-vpc/anh6.png)

**Bước 2:** Xác nhận metadata của tài liệu đã được lưu vào cơ sở dữ liệu.

**Bước 3:** Kiểm tra tài liệu đã xuất hiện trong khu vực quản lý và kiểm duyệt của quản trị viên.

**Bước 4:** Xác nhận trạng thái mặc định của tài liệu được thiết lập là **pending**.

#### Kết quả mong đợi

Sau khi hoàn thành các bước kiểm tra, tài liệu đã được lưu trên Amazon S3, metadata đã được ghi nhận trong cơ sở dữ liệu và sẵn sàng cho quy trình kiểm duyệt của hệ thống CloudDoc.