---
title: "Worklog Tuần 3"
date: 2026-05-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

Một tuần mới bắt đầu, em chuyển sang tìm hiểu về phân quyền bảo mật máy chủ và thực hành dịch vụ lưu trữ đối tượng.

### Mục tiêu tuần:
* Hiểu cách gán quyền hạn Identity and Access Management (IAM) Role cho máy chủ Amazon Elastic Compute Cloud (EC2) an toàn.
* Học các kiến thức cơ bản về Amazon Simple Storage Service (Amazon S3) bao gồm tạo Bucket, quy tắc đặt tên, quyền truy cập và các lớp lưu trữ (Storage Classes).
* Thực hành cấu hình lưu trữ website tĩnh và thiết lập chính sách bảo mật cho Bucket.
* Tìm hiểu các tính năng quản lý phiên bản (Versioning), vòng đời đối tượng (Object Lifecycle) và cơ chế sao chép chéo vùng (Cross-Region Replication).

### Công việc thực hiện trong tuần:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành |
| --- | --- | --- | --- |
| 1 | Em cấu hình IAM Role cho máy chủ EC2 để phân quyền an toàn cho ứng dụng khi truy cập tài nguyên. | 02/05/2026 | 02/05/2026 |
| 2 | Em tìm hiểu cách khởi tạo Bucket, quy tắc đặt tên, cấu hình quyền truy cập và học về các Storage Classes trên S3. | 03/05/2026 | 03/05/2026 |
| 3 | Em thực hành chạy thử tính năng Static Website Hosting và viết chính sách Bucket Policy để phân quyền truy cập S3. | 05/05/2026 | 05/05/2026 |
| 4 | Em tìm hiểu cách bật tính năng S3 Versioning, thiết lập quy tắc Object Lifecycle và nghe giới thiệu về cơ chế Cross-Region Replication. | 07/05/2026 | 07/05/2026 |

### Dự án CloudDoc:
* **Thiết kế cơ sở dữ liệu:** Em phối hợp cùng nhóm thảo luận cấu trúc dữ liệu, xác định các bảng chính và trao đổi sơ bộ về kiến trúc hệ thống của ứng dụng CloudDoc.

### Kết quả đạt được:
* Em gán thành công IAM Role cho EC2 mà không cần dùng Access Key.
* Em thực hành khởi tạo và phân cấu hình quyền cho S3 Bucket bình thường.
* Em cùng nhóm phác thảo xong cấu trúc dữ liệu và mô hình bảng ban đầu.

### Kinh nghiệm rút ra:
* Nhờ thực hành gán IAM Role cho EC2, em biết cách xây dựng hệ thống bảo mật tốt hơn. Ngoài ra, việc trao đổi thiết kế cấu trúc dữ liệu cùng nhóm giúp em hiểu sâu hơn về kiến thức thực tiễn của dự án.

### Kế hoạch tuần tiếp theo:
* Em sẽ tìm hiểu hệ quản trị cơ sở dữ liệu Amazon Relational Database Service (Amazon RDS) và cơ cấu co giãn tải máy chủ EC2.
