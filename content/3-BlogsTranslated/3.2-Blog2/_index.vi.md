---
title: "Blog 2"
date: 2026-06-13
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# NHÚNG TRỢ LÝ GENAI VÀO ỨNG DỤNG NỘI BỘ VỚI AWS AMPLIFY, CDK VÀ AMAZON Q BUSINESS

Khi khối lượng tài liệu nội bộ ngày càng lớn, việc tìm kiếm thông tin bằng từ khóa truyền thống thường không đáp ứng được nhu cầu của người dùng. Thay vì tìm kiếm từng tài liệu, nhiều tổ chức đang chuyển sang sử dụng trợ lý AI có khả năng trả lời câu hỏi bằng ngôn ngữ tự nhiên dựa trên dữ liệu doanh nghiệp.

Một bài blog từ AWS hướng dẫn cách xây dựng mô hình này bằng Amazon Q Business kết hợp với AWS Amplify và AWS CDK.

### 1. Tổng quan giải pháp

Kiến trúc sử dụng:
• Amazon Q Business để cung cấp khả năng hỏi đáp dựa trên dữ liệu nội bộ.
• AWS Amplify Gen 2 để xây dựng và triển khai ứng dụng.
• AWS CDK để quản lý hạ tầng dưới dạng mã nguồn.
• Amazon Cognito và IAM Identity Center để xác thực và phân quyền.
• Amazon S3 để lưu trữ tài liệu phục vụ quá trình lập chỉ mục dữ liệu.

### 2. Kiến trúc hoạt động

1.	Người dùng đăng nhập vào ứng dụng thông qua Cognito.
2.	Tài liệu nội bộ được tải lên Amazon S3.
3.	Amazon Q Business được cấp quyền truy cập và lập chỉ mục dữ liệu từ S3.
4.	Giao diện chat được nhúng trực tiếp vào ứng dụng web.
5.	Người dùng có thể đặt câu hỏi và nhận câu trả lời dựa trên dữ liệu doanh nghiệp kèm nguồn tham chiếu.

### 3. Điểm đáng chú ý

Một điểm mình thấy khá hữu ích là phần lớn việc cấu hình hạ tầng và quyền truy cập được triển khai bằng AWS CDK. Điều này giúp giảm đáng kể các thao tác cấu hình thủ công và dễ dàng quản lý môi trường thông qua Infrastructure as Code.

Ngoài ra, việc sử dụng Amazon Q Business cũng giúp doanh nghiệp triển khai tính năng GenAI nhanh hơn mà không cần tự xây dựng hoặc vận hành mô hình AI riêng.

### 4. Kết luận

Việc tích hợp trợ lý AI vào các ứng dụng nội bộ đang trở thành nhu cầu phổ biến trong nhiều tổ chức. Kiến trúc sử dụng Amazon Q Business, Amplify và CDK là một cách tiếp cận đáng tham khảo cho các hệ thống cần khai thác tri thức từ tài liệu doanh nghiệp một cách an toàn và có kiểm soát.

📖 Bài viết gốc:
https://aws.amazon.com/blogs/mobile/from-build-to-embed-creating-and-embedding-genai-apps-with-aws-amplify-cdk-and-amazon-q-business/

#AWS #AmazonQ #AWSAmplify #AWSCDK #GenerativeAI
