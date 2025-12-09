---
title: "Nhật ký Tuần 1"
date: "2025-09-08"
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu Tuần 1:

* Hiểu cấu trúc tài khoản AWS và vai trò của Root User.
* Học cách tạo và bảo mật tài khoản AWS.
* Thiết lập IAM User, IAM Group và gán chính sách quyền.
* Kích hoạt MFA và cấu hình cảnh báo chi phí.
* Làm quen với giao diện AWS Management Console.

### Các nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ                                                                                                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                        |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | ---------------- | ------------------------------------------ |
| 1    | - Tổng quan về tài khoản AWS và trách nhiệm của Root User <br> - Hiểu các khái niệm IAM (User, Group, Policy)                                                                                                                             | 08/09/2025   | 08/09/2025       | <https://000001.awsstudygroup.com/>        |
| 2    | - Tạo tài khoản AWS <br> - Thêm phương thức thanh toán <br> - Xác thực email & số điện thoại <br> - Đăng nhập lần đầu và khám phá AWS Console                                                                                            | 09/09/2025   | 09/09/2025       | <https://000001.awsstudygroup.com/>        |
| 3    | - Bảo mật tài khoản Root <br>&emsp; + Kích hoạt MFA <br>&emsp; + Cấu hình password policy <br>&emsp; + Giảm thiểu việc sử dụng Root User <br> - Thiết lập Billing Preferences & theo dõi Free Tier                                        | 10/09/2025   | 10/09/2025       | <https://000001.awsstudygroup.com/>        |
| 4    | - Tạo IAM Group (Administrators) <br> - Gắn AdministratorAccess policy <br> - Tạo IAM User <br> - Cấu hình đăng nhập cho user và bật MFA                                                           | 11/09/2025   | 11/09/2025       | <https://000001.awsstudygroup.com/>        |
| 5    | - Tạo Budget và Billing Alerts <br> - Kiểm tra danh sách bảo mật tài khoản <br> - Thực hành đăng nhập bằng IAM User <br> - Khám phá giao diện AWS Console <br> - Tổng kết bài học & các vấn đề phát sinh | 12/09/2025   | 12/09/2025       | <https://000001.awsstudygroup.com/>        |

---

### Kết quả đạt được Tuần 1

Tuần 1 là giai đoạn mình “đặt nền móng” cho toàn bộ hành trình với AWS, nên mình cố gắng làm mọi thứ thật chỉnh chu và có hệ thống:

* **Nắm vững cấu trúc tài khoản AWS**  
  Mình đã hiểu được sự khác biệt rõ ràng giữa:
  * **Root User** – chỉ dùng cho các tác vụ quản trị cấp cao, nhạy cảm.  
  * **IAM User / IAM Group / Policy** – dùng cho việc phân quyền hằng ngày theo best practice.  
  Nhờ đó, mình không còn suy nghĩ đơn giản kiểu “cứ đăng nhập root là xong” như trước nữa, mà ý thức được vấn đề bảo mật lâu dài.

* **Tạo và bảo mật tài khoản AWS một cách có quy trình**  
  Mình không chỉ dừng lại ở việc tạo được tài khoản AWS, mà còn:
  * Thiết lập đầy đủ thông tin thanh toán, xác thực email và số điện thoại.  
  * Kiểm tra lại từng bước để đảm bảo tài khoản hoạt động ổn định.  
  Điều này giúp mình tự tin hơn khi sử dụng tài khoản cho các bài lab và dự án sau này.

* **Bảo vệ tài khoản Root và IAM User đúng chuẩn best practices**  
  * Kích hoạt **MFA** cho Root User và cho IAM User chính mà mình sử dụng hằng ngày.  
  * Thiết lập **password policy** ở mức chặt chẽ (độ dài, ký tự đặc biệt, vòng đời mật khẩu…).  
  * Hạn chế tối đa việc đăng nhập bằng Root, chỉ dùng IAM User để thao tác.  
  Qua đó, mình nhận ra tầm quan trọng của bảo mật ngay từ bước đầu, thay vì chỉ quan tâm đến “chạy được dịch vụ”.

* **Thiết lập quản lý chi phí và cảnh báo sớm**  
  * Cấu hình **Billing Preferences** để nhận email khi có thay đổi.  
  * Tạo **Budget** và **Billing Alerts** để tránh vượt quá Free Tier.  
  Nhờ những bước này, mình yên tâm hơn khi thực hiện các bài thực hành vì biết rằng nếu có phát sinh chi phí bất thường, mình sẽ được cảnh báo sớm.

* **Áp dụng IAM theo best practices thay vì làm cho có**  
  * Tạo **IAM Group (Administrators)** và gán **AdministratorAccess** đúng cách.  
  * Tạo **IAM User** riêng và thêm vào group thay vì gán policy trực tiếp vào user.  
  * Thử đăng nhập bằng IAM User, kiểm tra quyền hạn và thử bật MFA.  
  Những thao tác này giúp mình hiểu IAM không chỉ là lý thuyết, mà là công cụ quan trọng để vận hành hệ thống an toàn.

* **Làm quen với AWS Management Console và cách tư duy dịch vụ**  
  * Dành thời gian khám phá giao diện, tìm kiếm dịch vụ qua thanh search.  
  * Ghi chú lại những dịch vụ xuất hiện nhiều trong tài liệu (EC2, S3, IAM, CloudWatch, v.v.).  
  Sau tuần 1, cảm giác “choáng ngợp” ban đầu với giao diện AWS giảm đi khá nhiều, thay vào đó là sự quen tay và dễ hình dung hơn khi đọc tài liệu / kiến trúc.

---

### Đánh giá bản thân và khó khăn gặp phải trong Tuần 1

Tuần 1 tuy chưa đụng nhiều vào phần “xây hệ thống”, nhưng lại là tuần mình phải thay đổi cách suy nghĩ về việc sử dụng tài khoản cloud một cách chuyên nghiệp.

#### 1. Đánh giá bản thân

* **Tích cực, chủ động làm tới cùng từng bước**  
  Mình không chỉ làm cho xong checklist, mà cố gắng hiểu “vì sao cần làm như vậy”, đặc biệt là các bước về Root User, IAM và Billing. Khi gặp chỗ chưa rõ, mình chủ động tra tài liệu, hỏi mentor và ghi chú lại.

* **Tuân thủ quy trình và bảo mật ngay từ đầu**  
  Thay vì bỏ qua các phần như MFA, Budget (thường bị xem nhẹ), mình nghiêm túc thực hiện đầy đủ. Điều này giúp mình hình thành thói quen tốt cho các tuần sau, khi hệ thống phức tạp hơn.

* **Biết tự hệ thống hóa kiến thức**  
  Sau mỗi ngày, mình đều tổng kết lại: hôm nay học được gì, đã làm bước nào, còn vướng gì. Việc ghi lại như vậy giúp mình không bị “quên ngang” và có thể quay lại ôn nhanh khi cần.

#### 2. Khó khăn gặp phải

* **Bỡ ngỡ với khái niệm tài khoản & quyền hạn**  
  Ban đầu mình khá lúng túng trong việc phân biệt:
  * Khi nào dùng Root, khi nào dùng IAM User?  
  * Gán quyền cho Group khác gì với gán thẳng cho User?  
  Sau khi học thêm tài liệu AWS và làm thử vài lần, mình mới hiểu rõ hơn mô hình phân quyền.

* **Lo lắng về chi phí và thanh toán**  
  Vì phải thêm phương thức thanh toán (thẻ/bank), mình khá lo việc bị trừ tiền ngoài ý muốn. Điều này khiến mình cẩn trọng hơn, nhưng cũng làm mình mất thêm thời gian để:
  * Đọc kỹ phần Billing & Free Tier.  
  * Tìm hiểu cách tạo Budget và Alerts.  
  Về lâu dài, đây là khó khăn “tốt”, vì nhờ vậy mình hiểu sâu hơn về kiểm soát chi phí.

* **Quá nhiều thông tin mới trong thời gian ngắn**  
  Ngay từ tuần đầu đã phải làm quen với:
  * Khái niệm tài khoản, bảo mật, thanh toán.  
  * Giao diện Console với rất nhiều dịch vụ.  
  Có lúc mình cảm thấy hơi quá tải, nhưng mình giải quyết bằng cách:
  * Chia nhỏ nội dung theo từng ngày (như trong bảng nhiệm vụ).  
  * Chỉ tập trung sâu vào những gì liên quan trực tiếp đến tài khoản & bảo mật trong tuần 1.

---

Nhìn chung, Tuần 1 tuy chủ yếu là “thiết lập nền”, nhưng mình đã cố gắng làm một cách cẩn thận và có suy nghĩ, thay vì làm cho đủ. Đây là nền tảng quan trọng để tuần 2, tuần 3 mình có thể tập trung hơn vào dịch vụ và kiến trúc mà không phải quay lại sửa các lỗi cơ bản về tài khoản và bảo mật.
