---
title: "Worklog Tuần 11"
date: "2025-11-17"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---



## Mục tiêu tuần 11

- Hoàn thiện **base infrastructure (M0)** gồm S3, DynamoDB, Cognito, ALB.  
- Bắt đầu triển khai **IDP Pipeline (M1)** — SQS, PDF Detection, PyPDF2 extraction.  
- Ổn định và tối ưu luồng **Analytics** trước đó: chuyển từ Glue Crawler sang Athena DDL để giảm chi phí và đơn giản hóa kiến trúc.  
- Chuẩn hóa lại hệ thống Lambda (AdminManager, Analytics Lambda) và đảm bảo hoạt động ổn định khi thao tác với Athena và RDS.  
- Tối ưu cấu hình Cognito để tách biệt backend và authentication logic.  
- Kiểm thử pipeline end-to-end từ **document upload → detection → extraction → DynamoDB → frontend**.

---

## Các công việc cần triển khai trong tuần này

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- |--------------|-----------------| -------------- |
| 2 | - Setup S3 bucket `arc-chatbot-documents-427995028618` <br> - Tạo DynamoDB tables (`metadata`, `chat-history`) <br> - Cấu hình schema & indexes |      17/11/2025        | 17/11/2025                | https://docs.aws.amazon.com/dynamodb/ |
| 3 | - Configure Cognito User Pool `ap-southeast-1_8KB4JYvsX` <br> - Setup user authentication flow <br> - Test sign-up/sign-in |     18/11/2025         |         18/11/2025        | https://docs.aws.amazon.com/cognito/ |
| 4 | - Setup ALB `arc-chatbot-dev-alb` với health checks <br> - Configure target groups & listeners <br> - Test routing |         19/11/2025     |        19/11/2025         | https://docs.aws.amazon.com/elasticloadbalancing/ |
| 5 | - Tạo SQS queue `arc-chatbot-dev-document-processing` <br> - Implement PDF detection (digital vs scanned) <br> - Viết unit tests cho PDF detector |      20/11/2025        |       20/11/2025          | https://docs.aws.amazon.com/sqs/ |
| 6 | - Implement PyPDF2 extraction cho digital PDFs <br> - Xử lý edge cases (encrypted, corrupted) <br> - Viết tests (30 tests passed) |      21/11/2025        |      21/11/2025           | https://pypdf2.readthedocs.io/ |

---

## Kết quả đạt được tuần 11

### **1. Hoàn thiện Base Infrastructure (M0)**  
- S3 bucket `arc-chatbot-documents-427995028618` để lưu documents.  
- DynamoDB tables:  
  - `metadata`: lưu thông tin mô tả tài liệu  
  - `chat-history`: lưu lịch sử hội thoại  
- Cognito User Pool `ap-southeast-1_8KB4JYvsX` — dùng cho xác thực & phân quyền.  
- ALB `arc-chatbot-dev-alb` — điều phối traffic API với health checks.

### **2. Khởi động & tối ưu IDP Pipeline (M1)**  
- SQS Queue `arc-chatbot-dev-document-processing` đảm nhiệm việc phân luồng xử lý tài liệu.  
- PDF Detector service: phân biệt digital vs scanned (17 tests passed).  
- PDF Extractor (PyPDF2): extract text từ digital PDF (30 tests passed).  
- Bổ sung xử lý lỗi của file PDF: encrypted, corrupted, unsupported.

### **3. Ổn định & cải thiện luồng Analytics từ tuần trước**  
- Loại bỏ Glue Crawler → chuyển sang Athena DDL để chủ động định nghĩa schema.  
- Xóa Glue DB, Glue endpoint → giảm chi phí & đơn giản hệ thống.  
- Refactor Lambda Analytics để chạy ngoài VPC khi query Athena.  
- AdminManager Lambda chỉ còn nhiệm vụ insert vào RDS → đơn giản hóa kiến trúc.  
- Tối ưu Cognito để backend không phụ thuộc trực tiếp DB.

### **4. Progress về Frontend & Authentication**  
- Deploy thành công login page trên CloudFront.  
- Hoàn thiện logic `admin_handler` để insert dữ liệu vào RDS ổn định hơn.  

---

## Học được

- Thiết kế DynamoDB schema cho hệ thống RAG/Chatbot.  
- Luồng xác thực Cognito + JWT tokens + User Pool flows.  
- SQS message processing patterns & cách thiết kế IDP pipeline.  
- Kỹ thuật đọc PDF bằng PyPDF2 và xử lý các dạng lỗi.  
- Kiến trúc Athena DDL, sự khác biệt với Glue Crawler, best practices cho chi phí/hiệu năng.  
- Cách tối ưu Lambda trong môi trường serverless pipeline.

---

## Tổng kết

Tuần 11 đạt được các mục tiêu chính: **hoàn thiện M0**, **khởi động M1**, ổn định lại pipeline phân tích dữ liệu, chuẩn hóa hệ thống Lambda và xác thực Cognito. Nhờ đó, dự án đã có nền tảng vững chắc để tiếp tục xây dựng RAG pipeline và mở rộng các module xử lý tài liệu ở tuần tiếp theo.
