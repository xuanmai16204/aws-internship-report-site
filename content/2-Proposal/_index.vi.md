---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

Tại phần này, bạn cần tóm tắt các nội dung trong workshop mà bạn **dự tính** sẽ làm.

# CloudDoc  
## Hệ thống quản lý và chia sẻ tài liệu trực tuyến trên nền tảng AWS  

### 1. Tóm tắt điều hành  
CloudDoc là hệ thống quản lý và chia sẻ tài liệu học tập dành cho sinh viên được triển khai trên nền tảng điện toán đám mây Amazon Web Services (AWS). Hệ thống hỗ trợ các chức năng cốt lõi bao gồm tải lên tài liệu (upload), tìm kiếm (search), xem trước trực tuyến (preview), tải xuống (download) và quy trình kiểm duyệt tài liệu (moderation workflow) dành cho quản trị viên. Kiến trúc của CloudDoc được thiết kế an toàn, tối ưu chi phí và có khả năng mở rộng tốt bằng việc tích hợp các dịch vụ AWS hiện đại, giúp phân phối nội dung nhanh chóng và lưu trữ dữ liệu an toàn.

### 2. Tuyên bố vấn đề  
*Vấn đề hiện tại*  
Các phương thức quản lý tài liệu truyền thống thường gặp khó khăn trong việc xử lý tệp tải lên có dung lượng lớn, phân quyền người dùng chưa tối ưu, thiếu quy trình kiểm duyệt nội dung tự động hoặc tập trung, và khó đáp ứng khả năng mở rộng khi lượng truy cập tăng đột biến. Việc lưu trữ trực tiếp các tệp tin lớn trên máy chủ ứng dụng (backend) cũng làm tiêu tốn tài nguyên và tăng chi phí hạ tầng không cần thiết.

*Giải pháp*  
CloudDoc giải quyết các vấn đề trên bằng cách xây dựng một kiến trúc tách biệt giữa giao diện frontend (React), backend xử lý logic (Node.js/Express) và dịch vụ lưu trữ đối tượng (Amazon S3). Luồng upload sử dụng presigned URL giúp tải tệp trực tiếp lên S3, giảm tải tối đa cho backend. Đối với việc lưu trữ lâu dài và tối ưu chi phí, hệ thống chuyển giao các tệp tin cũ sang Amazon S3 Glacier. Cơ sở dữ liệu PostgreSQL lưu trữ metadata phục vụ tìm kiếm nhanh chóng. Quy trình kiểm duyệt tự động hóa và thông báo được quản lý thông qua luồng tin nhắn và thông báo của AWS để đảm bảo tính sẵn sàng và tính tương tác của hệ thống.

*Lợi ích và hoàn vốn đầu tư (ROI)*  
Giải pháp giúp cung cấp nền tảng quản lý tài liệu ổn định cho sinh viên, đồng thời giảm thiểu đáng kể thời gian xử lý thủ công nhờ quy trình duyệt tài liệu tích hợp định sẵn. Việc lưu trữ trực tiếp trên Amazon S3 và chuyển đổi lớp lưu trữ sang Glacier giúp tối ưu hóa chi phí đến mức tối đa. Chi phí vận hành thấp của mô hình serverless kết hợp với các máy chủ EC2 kích thước nhỏ giúp hệ thống tiết kiệm ngân sách đáng kể ngay từ giai đoạn thử nghiệm đến khi vận hành thực tế.

### 3. Kiến trúc giải pháp  
CloudDoc áp dụng mô hình kiến trúc phân lớp an toàn và tiện lợi để quản lý cũng như lưu trữ tài liệu. Hệ thống vận hành trơn tru nhờ sự phối hợp của các thành phần sau:

![CloudDoc Architecture](/images/2-Proposal/anh1.png)

*Các dịch vụ AWS sử dụng và vai trò*  
- **Frontend**: Giao diện người dùng được triển khai tối ưu và truyền tải qua mạng lưới phân phối nội dung **Amazon CloudFront** giúp giảm độ trễ truy cập.
- **Application Load Balancer**: Điều phối lưu lượng mạng đến các máy chủ backend một cách cân bằng và hiệu quả.
- **Amazon EC2**: Server chạy Backend API bằng Node.js và Express để xử lý logic, nghiệp vụ, phân quyền và tạo presigned URL.
- **Amazon RDS PostgreSQL**: Cơ sở dữ liệu Postgres lưu trữ thông tin người dùng, metadata và trạng thái tài liệu.
- **Amazon S3**: Lưu trữ các tài liệu gốc và tệp đính kèm do người dùng tải lên thông qua cơ chế presigned URL.
- **Amazon S3 Glacier**: Lưu trữ lưu trữ dữ liệu lưu trữ lịch sử, ít truy cập nhằm tiết kiệm chi phí tối đa.
- **Amazon SQS** & **Amazon SNS**: Hệ thống hàng đợi (SQS) và dịch vụ thông báo (SNS) giúp xử ký bất đồng bộ các tác vụ và gửi thông báo về trạng thái của tài liệu đến hệ thống.
- **Amazon CloudWatch**: Thu thập log, theo dõi metric và cấu hình các alarm cảnh báo để giám sát trạng thái hoạt động của toàn bộ hạ tầng.

### 4. Triển khai kỹ thuật

Trong quá trình phát triển CloudDoc, nhóm lựa chọn triển khai theo từng giai đoạn nhằm đảm bảo các chức năng quan trọng đều được xây dựng, kiểm thử và tích hợp ổn định trước khi chuyển sang bước tiếp theo. Việc chia nhỏ quá trình phát triển giúp hạn chế lỗi phát sinh, đồng thời tạo điều kiện thuận lợi cho việc mở rộng hệ thống trong tương lai.

Các nội dung chính đã được triển khai gồm:

- Xây dựng giao diện người dùng bằng React cho các chức năng Home, Search, Upload, Preview, Download và Dashboard quản trị.
- Thiết kế Backend API bằng Node.js và Express để xử lý xác thực, phân quyền, quản lý tài liệu và sinh Presigned URL.
- Thiết kế cơ sở dữ liệu PostgreSQL nhằm lưu trữ metadata, trạng thái tài liệu, thông tin người dùng và lịch sử xử lý.
- Tích hợp Amazon S3 để lưu trữ file gốc, giúp backend không cần xử lý trực tiếp dữ liệu nhị phân.
- Xây dựng luồng upload sử dụng Presigned URL để giảm tải cho máy chủ ứng dụng và tăng khả năng mở rộng.
- Kết nối frontend, backend và các dịch vụ AWS thành một quy trình xử lý thống nhất.
- Thực hiện kiểm thử end-to-end nhằm xác nhận toàn bộ quy trình từ upload, kiểm duyệt đến preview và download đều hoạt động đúng.

Nhóm cũng ưu tiên chuẩn hóa cấu trúc mã nguồn, tách biệt giữa giao diện, xử lý nghiệp vụ và tầng dữ liệu để việc bảo trì và phát triển các chức năng mới trở nên thuận tiện hơn.

### 5. Lộ trình và mốc triển khai

Để đảm bảo tiến độ thực hiện, dự án CloudDoc được chia thành ba giai đoạn chính.

#### Giai đoạn 1: Hoàn thiện chức năng nền tảng

Ở giai đoạn đầu, nhóm tập trung xây dựng các chức năng cốt lõi của hệ thống.

- Thiết kế giao diện người dùng.
- Xây dựng chức năng đăng nhập và phân quyền.
- Phát triển chức năng upload tài liệu.
- Thiết kế cơ sở dữ liệu lưu metadata.
- Hoàn thiện chức năng tìm kiếm cơ bản.

#### Giai đoạn 2: Tích hợp các dịch vụ AWS

Sau khi hoàn thành phần ứng dụng, nhóm tiến hành tích hợp các dịch vụ trên AWS.

- Kết nối frontend với backend.
- Tích hợp Amazon S3 để lưu trữ tài liệu.
- Sử dụng Presigned URL cho quá trình upload.
- Hoàn thiện API phục vụ preview và download.
- Kiểm thử toàn bộ luồng xử lý tài liệu.

#### Giai đoạn 3: Hoàn thiện và tối ưu hệ thống

Ở giai đoạn cuối, nhóm tập trung hoàn thiện sản phẩm và chuẩn bị cho việc báo cáo.

- Tối ưu giao diện người dùng.
- Hoàn thiện Dashboard quản trị.
- Bổ sung cơ chế giám sát bằng CloudWatch.
- Chuẩn bị tài liệu báo cáo và demo hệ thống.
- Kiểm thử toàn bộ chức năng trước khi nghiệm thu.

Việc chia dự án thành nhiều giai đoạn giúp nhóm dễ dàng theo dõi tiến độ, đánh giá kết quả sau từng mốc và giảm rủi ro khi tích hợp các thành phần của hệ thống.

### 6. Ước tính ngân sách

Để đánh giá khả năng triển khai CloudDoc trên môi trường AWS, nhóm sử dụng AWS Pricing Calculator để ước tính chi phí vận hành hằng tháng đối với một kiến trúc gần với môi trường thực tế.

![AWS Pricing](/images/2-Proposal/anh2.png)

Hình ảnh trên đây được tạo bằng cách sử dụng AWS Pricing Calculator nhằm ước tính chi phí vận hành hằng tháng đối với kiến trúc của hệ thống CloudDoc.

Theo kết quả ước tính, Amazon RDS và Amazon EC2 là hai thành phần chiếm tỷ trọng chi phí lớn nhất do phải duy trì hoạt động liên tục. Các dịch vụ như Application Load Balancer, CloudWatch và NAT Gateway cũng phát sinh chi phí nhưng ở mức thấp hơn.

Trong giai đoạn học tập và thử nghiệm, nhóm có thể giảm đáng kể chi phí bằng các biện pháp sau:

- Sử dụng cấu hình EC2 có kích thước nhỏ.
- Dừng EC2 khi không sử dụng.
- Tận dụng AWS Free Tier đối với các dịch vụ đủ điều kiện.
- Thiết lập S3 Lifecycle để chuyển dữ liệu ít sử dụng sang lớp lưu trữ chi phí thấp.
- Theo dõi ngân sách bằng AWS Budgets để tránh phát sinh chi phí ngoài dự kiến.

Mức chi phí trên chỉ mang tính tham khảo cho mô hình triển khai đầy đủ và có thể thay đổi tùy theo quy mô hệ thống cũng như nhu cầu sử dụng thực tế.

### 7. Đánh giá rủi ro

Trong quá trình triển khai CloudDoc, nhóm nhận thấy một số rủi ro có thể ảnh hưởng đến chất lượng và khả năng vận hành của hệ thống.

| Rủi ro | Ảnh hưởng | Biện pháp giảm thiểu |
| --- | --- | --- |
| Upload thất bại do Presigned URL hết hạn | Người dùng không thể tải tài liệu lên | Giới hạn thời gian hợp lý và cho phép tạo lại URL mới |
| Metadata không được lưu thành công | Tài liệu không xuất hiện trong hệ thống | Kiểm tra giao dịch giữa upload và lưu metadata |
| Cấu hình IAM chưa phù hợp | Không truy cập được tài nguyên AWS hoặc phân quyền quá rộng | Áp dụng nguyên tắc Least Privilege |
| Chi phí AWS tăng ngoài dự kiến | Ảnh hưởng ngân sách triển khai | Theo dõi bằng AWS Budgets và dọn dẹp tài nguyên định kỳ |
| Thiếu cơ chế giám sát | Khó phát hiện lỗi khi hệ thống vận hành | Sử dụng CloudWatch Logs, Metrics và Alarm |
| Hệ thống khó mở rộng | Khó đáp ứng khi số lượng người dùng tăng | Thiết kế kiến trúc theo hướng tách biệt frontend, backend và storage |

Việc nhận diện các rủi ro ngay từ giai đoạn thiết kế giúp nhóm chủ động xây dựng các phương án xử lý, đồng thời nâng cao khả năng vận hành ổn định của hệ thống.

### 8. Kết quả kỳ vọng

CloudDoc hướng đến việc xây dựng một hệ thống quản lý tài liệu học tập hiện đại, có khả năng lưu trữ, tìm kiếm và chia sẻ tài liệu trên nền tảng điện toán đám mây AWS.

Sau khi hoàn thành dự án, hệ thống kỳ vọng sẽ đạt được các mục tiêu sau:

- Người dùng có thể tải lên, quản lý và chia sẻ tài liệu một cách thuận tiện.
- Tài liệu được lưu trữ an toàn trên Amazon S3 và quản lý bằng metadata trong PostgreSQL.
- Hỗ trợ tìm kiếm, xem trước và tải xuống tài liệu nhanh chóng.
- Áp dụng quy trình kiểm duyệt nhằm nâng cao chất lượng tài liệu trước khi công bố.
- Kiến trúc được thiết kế theo hướng mở rộng, dễ dàng bổ sung các tính năng mới trong tương lai.
- Các dịch vụ AWS được tích hợp hợp lý, giúp tăng tính bảo mật, khả năng mở rộng và tối ưu hiệu năng.

Đối với nhóm thực hiện, dự án không chỉเป็น sản phẩm phục vụ báo cáo thực tập mà còn là cơ hội vận dụng các kiến thức về phát triển web, cơ sở dữ liệu và điện toán đám mây vào một hệ thống hoàn chỉnh. Qua quá trình triển khai, nhóm có thêm kinh nghiệm trong việc phân tích yêu cầu, thiết kế kiến trúc, tích hợp dịch vụ AWS và phối hợp làm việc theo nhóm để hoàn thành một dự án thực tế.