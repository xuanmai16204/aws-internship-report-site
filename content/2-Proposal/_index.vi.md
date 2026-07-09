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

# IoT Weather Platform for Lab Research  
## Giải pháp AWS Serverless hợp nhất cho giám sát thời tiết thời gian thực  

### 1. Tóm tắt điều hành  
IoT Weather Platform được thiết kế dành cho nhóm *ITea Lab* tại TP. Hồ Chí Minh nhằm nâng cao khả năng thu thập và phân tích dữ liệu thời tiết. Nền tảng hỗ trợ tối đa 5 trạm thời tiết, có khả năng mở rộng lên 10–15 trạm, sử dụng thiết bị biên Raspberry Pi kết hợp cảm biến ESP32 để truyền dữ liệu qua MQTT. Nền tảng tận dụng các dịch vụ AWS Serverless để cung cấp giám sát thời gian thực, phân tích dự đoán và tiết kiệm chi phí, với quyền truy cập giới hạn cho 5 thành viên phòng lab thông qua Amazon Cognito.  

### 2. Tuyên bố vấn đề  
*Vấn đề hiện tại*  
Các trạm thời tiết hiện tại yêu cầu thu thập dữ liệu thủ công, khó quản lý khi có nhiều trạm. Không có hệ thống tập trung cho dữ liệu hoặc phân tích thời gian thực, và các nền tảng bên thứ ba thường tốn kém và quá phức tạp.  

*Giải pháp*  
Nền tảng sử dụng AWS IoT Core để tiếp nhận dữ liệu MQTT, AWS Lambda và API Gateway để xử lý, Amazon S3 để lưu trữ (bao gồm data lake), và AWS Glue Crawlers cùng các tác vụ ETL để trích xuất, chuyển đổi, tải dữ liệu từ S3 data lake sang một S3 bucket khác để phân tích. AWS Amplify với Next.js cung cấp giao diện web, và Amazon Cognito đảm bảo quyền truy cập an toàn. Tương tự như Thingsboard và CoreIoT, người dùng có thể đăng ký thiết bị mới và quản lý kết nối, nhưng nền tảng này hoạt động ở quy mô nhỏ hơn và phục vụ mục đích sử dụng nội bộ. Các tính năng chính bao gồm bảng điều khiển thời gian thực, phân tích xu hướng và chi phí vận hành thấp.  

*Lợi ích và hoàn vốn đầu tư (ROI)*  
Giải pháp tạo nền tảng cơ bản để các thành viên phòng lab phát triển một nền tảng IoT lớn hơn, đồng thời cung cấp nguồn dữ liệu cho những người nghiên cứu AI phục vụ huấn luyện mô hình hoặc phân tích. Nền tảng giảm bớt báo cáo thủ công cho từng trạm thông qua hệ thống tập trung, đơn giản hóa quản lý và bảo trì, đồng thời cải thiện độ tin cậy dữ liệu. Chi phí hàng tháng ước tính 0,66 USD (theo AWS Pricing Calculator), tổng cộng 7,92 USD cho 12 tháng. Tất cả thiết bị IoT đã được trang bị từ hệ thống trạm thời tiết hiện tại, không phát sinh chi phí phát triển thêm. Thời gian hoàn vốn 6–12 tháng nhờ tiết kiệm đáng kể thời gian thao tác thủ công.  

### 3. Kiến trúc giải pháp  
Nền tảng áp dụng kiến trúc AWS Serverless để quản lý dữ liệu từ 5 trạm dựa trên Raspberry Pi, có thể mở rộng lên 15 trạm. Dữ liệu được tiếp nhận qua AWS IoT Core, lưu trữ trong S3 data lake và xử lý bởi AWS Glue Crawlers và ETL jobs để chuyển đổi và tải vào một S3 bucket khác cho mục đích phân tích. Lambda và API Gateway xử lý bổ sung, trong khi Amplify với Next.js cung cấp bảng điều khiển được bảo mật bởi Cognito.  

![IoT Weather Station Architecture](/images/2-Proposal/edge_architecture.jpeg)

![IoT Weather Platform Architecture](/images/2-Proposal/platform_architecture.jpeg)

*Dịch vụ AWS sử dụng*  
- *AWS IoT Core*: Tiếp nhận dữ liệu MQTT từ 5 trạm, mở rộng lên 15.  
- *AWS Lambda*: Xử lý dữ liệu và kích hoạt Glue jobs (2 hàm).  
- *Amazon API Gateway*: Giao tiếp với ứng dụng web.  
- *Amazon S3*: Lưu trữ dữ liệu thô (data lake) và dữ liệu đã xử lý (2 bucket).  
- *AWS Glue*: Crawlers lập chỉ mục dữ liệu, ETL jobs chuyển đổi và tải dữ liệu.  
- *AWS Amplify*: Lưu trữ giao diện web Next.js.  
- *Amazon Cognito*: Quản lý quyền truy cập cho người dùng phòng lab.  

*Thiết kế thành phần*  
- *Thiết bị biên*: Raspberry Pi thu thập và lọc dữ liệu cảm biến, gửi tới IoT Core.  
- *Tiếp nhận dữ liệu*: AWS IoT Core nhận tin nhắn MQTT từ thiết bị biên.  
- *Lưu trữ dữ liệu*: Dữ liệu thô lưu trong S3 data lake; dữ liệu đã xử lý lưu ở một S3 bucket khác.  
- *Xử lý dữ liệu*: AWS Glue Crawlers lập chỉ mục dữ liệu; ETL jobs chuyển đổi để phân tích.  
- *Giao diện web*: AWS Amplify lưu trữ ứng dụng Next.js cho bảng điều khiển và phân tích thời gian thực.  
- *Quản lý người dùng*: Amazon Cognito giới hạn 5 tài khoản hoạt động.  

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

![AWS Pricing](/images/2-Proposal/anh1.png)

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

Đối với nhóm thực hiện, dự án không chỉ là sản phẩm phục vụ báo cáo thực tập mà còn là cơ hội vận dụng các kiến thức về phát triển web, cơ sở dữ liệu và điện toán đám mây vào một hệ thống hoàn chỉnh. Qua quá trình triển khai, nhóm có thêm kinh nghiệm trong việc phân tích yêu cầu, thiết kế kiến trúc, tích hợp dịch vụ AWS và phối hợp làm việc theo nhóm để hoàn thành một dự án thực tế.