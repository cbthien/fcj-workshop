---
title: "Worklog Tuần 9"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu Tuần 9:

* Hiểu cách triển khai ứng dụng có khả năng mở rộng và chịu lỗi bằng Launch Template, Load Balancer và Auto Scaling Group.
* Nắm rõ cơ chế tự động mở rộng (elasticity), phân phối tải và tính sẵn sàng cao.
* Học cách giám sát hệ thống với CloudWatch Metrics, Logs, Alarms và Dashboards.
* Áp dụng các best practices về quan sát hệ thống (observability) và giám sát ứng dụng.

---

### Các nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ                                                                                                                                                                                                                                         | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                         |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | ---------------- | ------------------------------------------ |
| 1    | - Tìm hiểu kiến trúc Auto Scaling <br>&emsp; + Chuẩn bị IAM, security group, AMI và mạng                                                                                                                 | 10/21/2025   | 10/21/2025       | <https://000006.awsstudygroup.com/>        |
| 2    | - **Thực hành Phần 1:** <br>&emsp; + Tạo Launch Template <br>&emsp; + Cấu hình user data, storage, instance settings                                                                                    | 10/22/2025   | 10/22/2025       | <https://000006.awsstudygroup.com/>        |
| 3    | - **Thực hành Phần 2:** <br>&emsp; + Tạo Application Load Balancer <br>&emsp; + Tạo target group và kiểm tra hoạt động của ứng dụng                                                                      | 10/23/2025   | 10/23/2025       | <https://000006.awsstudygroup.com/>        |
| 4    | - **Triển khai Auto Scaling Group:** <br>&emsp; + Tạo ASG và policy mở rộng <br>&emsp; + Kiểm thử scaling khi tải tăng/giảm                                                                              | 10/24/2025   | 10/24/2025       | <https://000006.awsstudygroup.com/>        |
| 5    | - **Workshop CloudWatch:** <br>&emsp; + Tìm hiểu Metrics <br>&emsp; + Thu thập Logs <br>&emsp; + Tạo Alarms <br>&emsp; + Tạo Dashboards <br>&emsp; + Cleanup tài nguyên                                  | 10/25/2025   | 10/25/2025       | <https://000008.awsstudygroup.com/>        |

---

### Thành tựu Tuần 9:

* Hiểu rõ cách Auto Scaling Group, Load Balancer và Launch Template kết hợp để đảm bảo tính sẵn sàng và khả năng mở rộng.
* Tạo thành công ASG và kiểm thử behavior của scaling policy.
* Tạo và triển khai ALB, kiểm tra phân phối tải và tính sẵn sàng.
* Thu thập và phân tích metrics & logs bằng CloudWatch.
* Tạo các cảnh báo (alarms) theo dõi sức khỏe ứng dụng và tài nguyên.
* Xây dựng dashboard trực quan để giám sát hệ thống.
* Cleanup toàn bộ tài nguyên tạo ra trong workshop để tránh phát sinh chi phí.
