---
title: "Dọn dẹp tài nguyên"
date: 2026-04-17
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

#### Mục tiêu

Sau khi hoàn thành workshop, cần rà soát và dọn dẹp các tài nguyên đã sử dụng nhằm tránh phát sinh chi phí không cần thiết và chuẩn bị môi trường cho các lần triển khai tiếp theo.

#### Các bước thực hiện

**Bước 1:** Xóa các dữ liệu thử nghiệm không còn sử dụng trong Amazon S3 Bucket.

![Xóa dữ liệu trên S3](/images/5-Workshop/5.7-clean-resources/anh1.png)

**Bước 2:** Dừng hoặc kết thúc EC2 Instance phục vụ cho môi trường thử nghiệm.

![Dừng EC2 Instance](/images/5-Workshop/5.7-clean-resources/anh2.png)

**Bước 3:** Kiểm tra lại các cấu hình giám sát và cảnh báo trước khi kết thúc môi trường.

**Bước 4:** Rà soát các tài nguyên còn liên quan để tránh bỏ sót trước khi xóa.

#### Hoàn tất

Sau khi hoàn thành các bước trên, môi trường thử nghiệm đã được thu hồi và sẵn sàng cho những lần triển khai hoặc thực hành tiếp theo.
