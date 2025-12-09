---
title: "Nhật ký Tuần 6"
date: "2025-10-14"
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu Tuần 6:

* Tìm hiểu cách triển khai và quản lý Amazon RDS MySQL trong kiến trúc VPC bảo mật.
* Hiểu kết nối giữa EC2 (public subnet) và RDS (private subnet).
* Triển khai ứng dụng tương tác với RDS và thực hành backup/restore.
* Tìm hiểu cách triển khai ứng dụng trên Amazon Lightsail.
* Thực hành tối ưu chi phí thông qua snapshot, scale-up, alarm và cleanup.

---

### Các nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ                                                                                                                                                                                                                                       | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                         |
| ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | ---------------- | ------------------------------------------ |
| 1    | - Tìm hiểu tổng quan Amazon RDS & yêu cầu chuẩn bị <br>&emsp; + Các engine hỗ trợ <br>&emsp; + Thiết kế VPC cho RDS (EC2 public → RDS private)                                                           | 10/14/2025   | 10/14/2025       | <https://000005.awsstudygroup.com/>        |
| 2    | - **Thực hành RDS:** <br>&emsp; + Tạo EC2 trong public subnet <br>&emsp; + Tạo RDS MySQL trong private subnet <br>&emsp; + Cấu hình security group để EC2 kết nối RDS                                   | 10/15/2025   | 10/15/2025       | <https://000005.awsstudygroup.com/>        |
| 3    | - **Triển khai ứng dụng:** <br>&emsp; + Deploy ứng dụng kết nối tới RDS <br>&emsp; + Kiểm tra CRUD từ EC2 lên database                                                                                  | 10/16/2025   | 10/16/2025       | <https://000005.awsstudygroup.com/>        |
| 4    | - **Workshop Lightsail – Phần 1:** <br>&emsp; + Deploy database trên Lightsail <br>&emsp; + Triển khai WordPress, Prestashop và Akaunting                                                               | 10/17/2025   | 10/17/2025       | <https://000045.awsstudygroup.com/>        |
| 5    | - **Workshop Lightsail – Phần 2:** <br>&emsp; + Cấu hình bảo mật ứng dụng <br>&emsp; + Tạo snapshot <br>&emsp; + Scale lên instance mạnh hơn <br>&emsp; + Tạo alarm giám sát <br>&emsp; + Cleanup tài nguyên | 10/18/2025   | 10/18/2025       | <https://000045.awsstudygroup.com/>        |

---

### Thành tựu Tuần 6:

* Hiểu kiến trúc và hoạt động của RDS trong môi trường AWS.
* Tạo thành công EC2 và RDS MySQL với cấu hình mạng & bảo mật đúng chuẩn.
* Deploy ứng dụng truy vấn RDS và kiểm thử CRUD.
* Thực hành tạo snapshot và restore trên RDS.
* Triển khai ứng dụng WordPress, Prestashop, Akaunting trên Lightsail.
* Nắm được cách tăng cường bảo mật cho ứng dụng Lightsail.
* Thực hành tối ưu chi phí: snapshot, nâng cấp instance, tạo alarm giám sát.
* Cleanup toàn bộ tài nguyên để tránh tốn phí.
