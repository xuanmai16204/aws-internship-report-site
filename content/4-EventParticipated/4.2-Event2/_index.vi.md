---
title: "Meet Up – First Cloud AI Journey"
date: 2026-05-30
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# BÀI THU HOẠCH
# Meet Up – First Cloud AI Journey

### 1. Thông tin chung
- **Tên sự kiện:** Meet Up – First Cloud AI Journey
- **Thời gian:** 30/05/2026
- **Địa điểm:** Văn phòng Công ty TNHH Amazon Web Services Việt Nam
- **Vai trò:** Người tham dự (Participant)

### 2. Mục tiêu của sự kiện
Buổi Meet Up được tổ chức nhằm tạo điều kiện cho các nhóm thực tập sinh trao đổi sâu sắc về tiến độ dự án, chia sẻ kinh nghiệm triển khai kỹ thuật và tháo gỡ các khó khăn khi tích hợp hệ thống. Sự kiện tập trung giải quyết các bài toán về kết nối Frontend/Backend, cấu hình deploy hạ tầng đám mây và tối ưu hóa tài nguyên trên AWS.

### 3. Các hoạt động chính
Tại buổi Meet Up, em đã trực tiếp tham gia báo cáo tiến độ và thảo luận các vấn đề kỹ thuật của dự án CloudDoc cùng các anh chị mentors:
- **Trình bày tiến độ dự án CloudDoc**: Trình bày giao diện thiết kế React đã hoàn thiện của các trang Home, Search, Upload và Dashboard quản trị.
- **Thảo luận tích hợp Frontend/Backend**: Trao đổi sâu về cấu trúc lưu trữ tài liệu (document metadata) trong DB và cách gọi API bảo mật để kết nối Client với Server Node.js.
- **Tư vấn giải pháp AWS Deployment**: Lắng nghe ý kiến của mentors về cách deploy backend lên EC2 instance, sử dụng Application Load Balancer (ALB) và thiết lập bảo mật với IAM policies.
- **Phiên Q&A giải đáp thắc mắc**: Trực tiếp đặt câu hỏi và nhận câu trả lời thực tế từ các kỹ sư AWS về cách ngăn chặn các cuộc gọi API không hợp lệ và cấu hình CORS khi thực hiện luồng upload lên S3.

### 4. Kiến thức tích lũy
Qua ngày hội Meet Up, em đã tích luỹ được các nhóm kiến thức thiết thực:
- **Kiến thức thực tiễn về kết nối hệ thống**: Hiểu rõ cách frontend và backend đồng bộ hóa dữ liệu thông qua RESTful APIs, đặc biệt là cách xử lý dữ liệu metadata trước và sau khi lưu vào cơ sở dữ liệu.
- **Nguyên lý cấu hình IAM và Bảo mật**: Biết cách thiết lập quyền hạn chi tiết (least privilege principle) cho các tác vụ AWS để đảm bảo an toàn cho tài sản dữ liệu.
- **Giải quyết lỗi CORS khi upload**: Nắm vững phương pháp cấu hình CORS (Cross-Origin Resource Sharing) trong AWS S3 Bucket để cho phép React App gửi tệp trực tiếp qua presigned URL.

### 5. Trải nghiệm và nhận xét cá nhân
Buổi Meet Up là cầu nối tuyệt vời để em kiểm tra giả định thiết kế và mã nguồn của CloudDoc dưới góc nhìn của các kỹ sư chuyên nghiệp. Sự chỉ dẫn nhiệt tình của các mentors đã giúp em tháo gỡ được những nút thắt lớn về tích hợp hạ tầng và cấu hình CORS. Những bài học đắt giá này không chỉ giúp hoàn thiện dự án đúng thời hạn mà còn mang lại cho em tư duy giải quyết vấn đề hệ thống sâu sắc hơn.
