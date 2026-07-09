---
title: "Worklog Tuần 4"
date: 2026-05-08
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

Tuần này em chuyển sang tìm hiểu về dịch vụ cơ sở dữ liệu quan hệ trên đám mây và cơ chế co giãn tài nguyên.

### Mục tiêu tuần:
* Hiểu cơ chế hoạt động của Amazon Relational Database Service (Amazon RDS) bao gồm cấu hình dự phòng Multi-AZ, Read Replica và sao lưu (Backup).
* Thực hành khởi tạo cơ sở dữ liệu RDS MySQL và kết nối đến Database.
* Học cách sao lưu (Backup), tạo bản Snapshot và thực hiện khôi phục (Restore) dữ liệu.
* Tìm hiểu cấu trúc vận hành của hệ thống co giãn tự động EC2 Auto Scaling và bộ cân bằng tải Elastic Load Balancer (ELB).

### Công việc thực hiện trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành |
| --- | --- | --- | --- |
| Thứ 3 | Em thực hiện cấu hình sao lưu tự động, tự tạo Snapshot và thực hành khôi phục dữ liệu database. | 12/05/2026 | 12/05/2026 |
| Thứ 5 | Em tìm hiểu cấu trúc hoạt động của EC2 Auto Scaling và bộ cân bằng tải ELB. | 14/05/2026 | 14/05/2026 |
| Thứ 7 | Em tự tìm hiểu lý thuyết về RDS, phân biệt cách thiết lập Multi-AZ, Read Replica và cơ chế sao lưu. | 09/05/2026 | 09/05/2026 |
| Chủ nhật | Em thực hành tạo cơ sở dữ liệu RDS MySQL và kiểm tra việc kết nối vào Database. | 10/05/2026 | 10/05/2026 |

### Dự án CloudDoc:
* **Thiết kế kiến trúc:** Em phối hợp cùng nhóm trao đổi và phác thảo sơ đồ thiết kế kiến trúc hệ thống của ứng dụng CloudDoc.

### Kết quả đạt được:
* Em khởi tạo chạy thử thành công một cơ sở dữ liệu RDS MySQL.
* Em thực hiện sao lưu và khôi phục dữ liệu từ Snapshot thành công.
* Em cùng nhóm thống nhất sơ đồ phác thảo kiến trúc hệ thống.

### Kinh nghiệm rút ra:
* Thực hành tạo cơ sở dữ liệu độc lập giúp em hiểu rõ lợi ích của việc phân chia cấu phần hệ thống. Ngoài ra, việc làm việc cùng nhóm giúp em nắm được phương pháp phác thảo kiến trúc tổng thể cho một ứng dụng thực tế.

### Kế hoạch tuần tiếp theo:
* Em sẽ tìm hiểu cách quản lý tên miền thông qua Amazon Route 53 và cài đặt công cụ AWS CLI.
