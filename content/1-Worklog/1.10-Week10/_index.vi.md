---
title: "Worklog Tuần 10"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
### Mục tiêu tuần 10

* Học cách cài đặt, cấu hình và sử dụng AWS CLI để thao tác với các dịch vụ AWS.
* Quản lý tài nguyên AWS (S3, SNS, IAM, VPC, EC2) thông qua dòng lệnh.
* Tìm hiểu Route 53 Resolver và xây dựng mô hình Hybrid DNS giữa on-premises và AWS.
* Triển khai Microsoft AD và cấu hình DNS forwarding với Route 53 Resolver.

---

### Nhiệm vụ thực hiện trong tuần

| Ngày | Nhiệm vụ | Bắt đầu | Hoàn thành | Tài liệu |
| --- | -------- | -------- | ---------- | -------- |
| 1 | - Giới thiệu AWS CLI <br> - Môi trường chạy CLI (Linux/macOS/Windows/Remote) <br> - Tìm hiểu CLI Profiles <br> - Cấu hình CLI bằng `aws configure` | 28/10/2025 | 28/10/2025 | https://000011.awsstudygroup.com/ |
| 2 | - Cài đặt AWS CLI <br> - Xem tài nguyên AWS bằng CLI <br> - Làm việc với Amazon S3 bằng CLI (list, upload, download) | 29/10/2025 | 29/10/2025 | https://000011.awsstudygroup.com/ |
| 3 | - AWS CLI với Amazon SNS (tạo topic, subscription, publish) <br> - AWS CLI với IAM (tạo user, list policies) <br> - AWS CLI với VPC (list VPCs, subnets, SGs) | 30/10/2025 | 30/10/2025 | https://000011.awsstudygroup.com/ |
| 4 | - Tạo EC2 bằng AWS CLI <br> - Xử lý lỗi CLI <br> - Dọn dẹp tài nguyên CLI <br><br> **Bắt đầu Lab Route 53 Hybrid DNS:** <br> - Giới thiệu Hybrid DNS và Route 53 Resolver | 31/10/2025 | 31/10/2025 | https://000011.awsstudygroup.com/ <br> https://000010.awsstudygroup.com/ |
| 5 | - Triển khai Microsoft AD trong lab <br> - Cấu hình Route 53 Resolver rules <br> - Tạo inbound & outbound endpoints <br> - Kiểm tra phân giải DNS giữa on-premises và AWS <br> - Clean up resources | 01/11/2025 | 01/11/2025 | https://000010.awsstudygroup.com/ |

---

### Thành tựu tuần 10

* Cài đặt và cấu hình AWS CLI thành công (Access Key, Secret Key, Default Region).
* Thao tác S3, SNS, IAM, VPC thông qua câu lệnh CLI.
* Tạo EC2 instance bằng CLI và khắc phục lỗi liên quan.
* Hiểu rõ kiến trúc Hybrid DNS với Route 53 Resolver.
* Triển khai Microsoft AD và cấu hình DNS forwarding giữa on-premises và AWS.
* Kiểm tra hoạt động của Resolver rules, inbound/outbound endpoints.  
* Dọn dẹp toàn bộ tài nguyên sau khi hoàn tất bài lab.

