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

## Demo CloudDoc & Tài nguyên Workshop

Đây là phần tài liệu minh họa và demo của dự án CloudDoc được thực hiện trong quá trình thực tập AWS.

Thư mục Google Drive bao gồm toàn bộ tài liệu Workshop, hình ảnh minh họa, cấu hình AWS, tài liệu hướng dẫn, các tệp phục vụ triển khai và những nội dung được sử dụng trong quá trình xây dựng hệ thống CloudDoc.

Người đọc có thể sử dụng các tài liệu này kết hợp với Workshop để dễ dàng theo dõi quy trình triển khai và thực hành lại hệ thống CloudDoc trên nền tảng AWS.

**📁 Mở Demo CloudDoc & Tài nguyên Workshop**

{{% button href="https://drive.google.com/drive/folders/1-mvKrbzs08WWHUT0-whSGeNwgtwd4Uid?usp=sharing" icon="fab fa-google-drive" %}}Demo CloudDoc & Tài nguyên Workshop{{% /button %}}

## Video Demo CloudDoc

Phần này cung cấp video demo của hệ thống CloudDoc được thực hiện trong chương trình thực tập First Cloud AI Journey (FCAJ).

Video giới thiệu các chức năng chính của hệ thống và minh họa quá trình sử dụng ứng dụng CloudDoc.

{{% button href="https://drive.google.com/drive/folders/1-mvKrbzs08WWHUT0-whSGeNwgtwd4Uid?usp=sharing" icon="fab fa-google-drive" %}}Xem Video Demo CloudDoc{{% /button %}}

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

1. [Giới thiệu]({{% relref "5.1-Workshop-overview" %}})
2. [Điều kiện tiên quyết]({{% relref "5.2-Prerequiste" %}})
3. [Triển khai luồng upload và lưu trữ tài liệu]({{% relref "5.3-S3-vpc" %}})
4. [Kiểm thử hệ thống end-to-end]({{% relref "5.4-S3-onprem" %}})
5. [Tích hợp ứng dụng khách và quan sát hệ thống]({{% relref "5.5-Policy" %}})
6. [Cập nhật dữ liệu]({{% relref "5.6-Cleanup" %}})
7. [Dọn dẹp tài nguyên]({{% relref "5.7-clean-resources" %}})