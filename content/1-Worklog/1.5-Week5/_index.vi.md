---
title: "Worklog Tuần 5"
date: 2026-05-15
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

Tuần này em dành thời gian để học cách quản trị tên miền trực tuyến và cấu hình các công cụ giám sát máy chủ.

### Mục tiêu tuần:
* Tìm hiểu dịch vụ quản lý tên miền Amazon Route 53 để cấu hình Hosted Zone, các bản ghi DNS Records và cơ chế dự phòng Failover Routing.
* Cài đặt và cấu hình giao diện dòng lệnh AWS Command Line Interface (AWS CLI) bao gồm thiết lập Credentials và Region.
* Sử dụng dịch vụ giám sát Amazon CloudWatch để theo dõi máy chủ Amazon Elastic Compute Cloud (EC2), cấu hình cảnh báo quá tải CPU (CPU Utilization Alarm).
* Tìm hiểu giải pháp quản lý logs với CloudWatch Logs gồm Log Group và cấu hình Log Agent trên EC2.

### Công việc thực hiện trong tuần:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành |
| --- | --- | --- | --- |
| Thứ 7 | Em thực hành khai báo tên miền trong Route 53, cấu hình Hosted Zone, tạo các bản ghi DNS và chạy thử cơ chế Failover Routing. | 16/05/2026 | 16/05/2026 |
| Chủ nhật | Em cài đặt AWS CLI trên máy tính cá nhân, cấu hình Credentials truy cập và chỉ định Region mặc định. | 17/05/2026 | 17/05/2026 |
| Thứ 3 | Em thực hiện cấu hình CloudWatch để theo dõi hiệu năng EC2 và thiết lập cảnh báo Alarm khi CPU vượt ngưỡng. | 19/05/2026 | 19/05/2026 |
| Thứ 5 | Em tìm hiểu dịch vụ CloudWatch Logs, thực hiện tạo Log Group và cài đặt Log Agent trên máy chủ. | 21/05/2026 | 21/05/2026 |

### Dự án CloudDoc:
* **Khởi động dự án trên Git:** Em cùng nhóm tạo kho lưu trữ GitHub Repository chính thức cho dự án CloudDoc, thảo luận thống nhất quy tắc làm việc nhóm và thực hiện phân chia công việc cho các thành viên.

### Kết quả đạt được:
* Em cấu hình thành công các bản ghi tên miền bằng Route 53.
* Em thiết lập xong môi trường chạy AWS CLI cục bộ.
* Em cùng nhóm hoàn thành việc phân chia công việc rõ ràng trên Git.

### Kinh nghiệm rút ra:
* Thực hành CloudWatch Alarm giúp em hiểu cách quản trị hệ thống chủ động. Việc khởi tạo kho lưu trữ GitHub Repository cùng các quy tắc giúp nhóm em phối hợp trơn tru hơn trong quá trình phát triển dự án.

### Kế hoạch tuần tiếp theo:
* Em sẽ tham gia ngày hội lập trình và tìm hiểu các tính năng quản trị quy mô lớn của AWS Systems Manager.
