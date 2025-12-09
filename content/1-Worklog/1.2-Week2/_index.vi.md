---
title: "Nhật ký Tuần 2"
date: "2025-09-15"
weight: 2
chapter: false
pre: " <b> 1.2 </b> "
---

### Mục tiêu Tuần 2:

* Hiểu AWS Budgets và cách sử dụng để quản lý, giám sát chi phí AWS.
* Tìm hiểu các loại AWS Budgets khác nhau: Cost Budget, Usage Budget, RI Budget, Savings Plans Budget.
* Thực hành tạo budgets bằng template và thiết lập tùy chỉnh, cũng như dọn dẹp tài nguyên sau khi sử dụng.
* Hiểu về AWS Support: các gói hỗ trợ, cách truy cập AWS Support, và cách tạo, quản lý yêu cầu hỗ trợ (support request).
* Nâng cao nhận thức về kiểm soát chi phí và cách nhận hỗ trợ từ AWS khi có sự cố xảy ra.

---

### Các nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ                                                                                                                                                                                                                                  | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                         |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | ---------------- | ------------------------------------------ |
| 1   | - Tìm hiểu tổng quan về **AWS Budgets** <br>&emsp; + AWS Budgets là gì? <br>&emsp; + Tại sao sử dụng budgets để kiểm soát chi phí? <br>&emsp; + Các loại budgets (Cost, Usage, RI, Savings Plans)                                         | 15/09/2025   | 15/09/2025        | <https://000007.awsstudygroup.com/>        |
| 2   | - **Thực hành với Budgets (1):** <br>&emsp; + Tạo Budget bằng Template <br>&emsp; + Tạo Cost Budget với các ngưỡng cảnh báo (alert thresholds) <br>&emsp; + Xem chi tiết budget và cấu hình thông báo                                    | 16/09/2025   | 16/09/2025      | <https://000007.awsstudygroup.com/>        |
| 3   | - **Thực hành với Budgets (2):** <br>&emsp; + Tạo Usage Budget cho một dịch vụ cụ thể (ví dụ: EC2) <br>&emsp; + Tạo RI Budget <br>&emsp; + Hiểu khi nào nên sử dụng từng loại budget                                                     | 17/09/2025   | 17/09/2025     | <https://000007.awsstudygroup.com/>        |
| 4   | - **Thực hành với Budgets (3):** <br>&emsp; + Tạo Savings Plans Budget <br>&emsp; + Xem các cảnh báo và ví dụ về kịch bản vượt chi phí (cost overrun) <br>&emsp; + Dọn dẹp budgets và các tài nguyên liên quan sau khi hoàn thành lab | 18/09/2025   | 18/09/2025       | <https://000007.awsstudygroup.com/>        |
| 5   | - Tìm hiểu **AWS Support**: <br>&emsp; + Các gói AWS Support và sự khác nhau giữa chúng <br>&emsp; + Cách truy cập AWS Support Center <br> - **Thực hành:** <br>&emsp; + Điều hướng đến Support Center <br>&emsp; + Tạo một support case <br>&emsp; + Xem / cập nhật / đóng yêu cầu hỗ trợ | 19/09/2025   | 19/09/2025       | <https://000009.awsstudygroup.com/>        |

---

### Thành tựu Tuần 2

Tuần 2 tập trung vào việc xây dựng nền tảng vững chắc về **quản lý chi phí** và **quy trình hỗ trợ (support)** trên AWS. Thay vì chỉ học về các dịch vụ, mình học cách giữ cho môi trường AWS vận hành bền vững và có kiểm soát.

* **Hiểu vai trò của AWS Budgets trong quản lý chi phí**  
  Mình đã hiểu rõ hơn về:
  * **AWS Budgets** là gì và khác gì so với chỉ xem Billing dashboard.  
  * Tại sao việc cấu hình budgets một cách chủ động lại quan trọng để tránh các đợt tăng chi phí đột ngột.  
  * Cách budgets phù hợp trong bức tranh tổng thể chiến lược quản lý chi phí cho các workload trên AWS.

* **Phân biệt các loại budget khác nhau**  
  Mình đã học cách phân biệt các trường hợp sử dụng và điểm mạnh của từng loại budget:
  * **Cost Budget** – kiểm soát tổng chi tiêu (ví dụ: tất cả dịch vụ trong một tháng).  
  * **Usage Budget** – theo dõi mức sử dụng của các tài nguyên cụ thể (ví dụ: số giờ EC2, dung lượng S3).  
  * **RI Budget** – giám sát mức sử dụng và độ bao phủ (coverage) của Reserved Instances.  
  * **Savings Plans Budget** – theo dõi chi tiêu Savings Plans và giúp đảm bảo cam kết được sử dụng hiệu quả.  
  Điều này giúp mình hiểu rằng “một loại budget không phù hợp cho mọi trường hợp” và mỗi workload có thể cần một tổ hợp budget khác nhau.

* **Trải nghiệm thực hành tạo và cấu hình budgets**  
  Mình không chỉ đọc tài liệu – mà còn thực hành:
  * Tạo budgets bằng **templates** để thiết lập nhanh hơn.  
  * Tạo **Cost Budget tùy chỉnh** với các ngưỡng và chu kỳ cụ thể.  
  * Xem chi tiết cấu hình budget, bao gồm phạm vi (scope), chu kỳ (period) và bộ lọc (filters).  
  Thông qua đó, mình tự tin hơn khi làm việc trong Billing & Cost Management console, thay vì ngại đụng vào vì sợ “liên quan đến tiền”.

* **Thiết lập cảnh báo (alerts) và kênh thông báo cho budgets**  
  Mình cấu hình gửi email thông báo sao cho:
  * Gửi thông báo khi **chi phí thực tế (actual costs)** vượt ngưỡng đã đặt.  
  * Gửi thông báo khi **dự đoán (forecasted costs)** cho thấy chi phí có thể vượt quá budget.  
  Điều này giúp mình có góc nhìn thực tế về cách sử dụng budgets trong môi trường thật để phát hiện sớm vấn đề trước khi chúng trở thành khoản chi vượt kiểm soát.

* **Dọn dẹp budgets và các tài nguyên còn sót lại sau khi làm lab**  
  Sau khi hoàn thành phần thực hành:
  * Mình rà soát lại các budgets đang tồn tại và xóa những budget không còn cần thiết.  
  * Kiểm tra lại để đảm bảo không còn các cảnh báo hoặc cấu hình test dư thừa.  
  Thói quen này giúp tài khoản gọn gàng hơn và dễ quản lý hơn về lâu dài.

* **Hiểu AWS Support và khi nào nên sử dụng**  
  Mình đã học:
  * Sự khác nhau giữa các gói **AWS Support Plans** (Basic, Developer, Business, Enterprise).  
  * Những tính năng nào có trong gói **Basic** (ví dụ: tài liệu, diễn đàn) và những gì cần gói trả phí.  
  * Các kịch bản thực tế mà trong đó việc mở một AWS support case là lựa chọn đúng đắn, thay vì cố gắng tự xử lý mọi thứ.

* **Thực hành sử dụng AWS Support Center**  
  Mình đã thực hành:
  * Điều hướng đến **AWS Support Center** từ console.  
  * Tạo một **support case**, chọn đúng loại (category) và mức độ ưu tiên (severity).  
  * Xem, cập nhật và đóng các yêu cầu hỗ trợ.  
  Điều này giúp mình “gỡ bỏ sự mơ hồ” về quy trình support và cảm thấy thoải mái hơn khi cần nhờ AWS hỗ trợ một cách bài bản.

* **Xây dựng nhận thức rõ hơn về kiểm soát chi phí và quy trình hỗ trợ**  
  Nhìn chung, Tuần 2 giúp mình nhận ra rằng:
  * Sử dụng AWS một cách có trách nhiệm không chỉ là triển khai tài nguyên, mà còn là **chủ động theo dõi chi phí**.  
  * Biết **khi nào và làm thế nào để liên hệ AWS Support** là một kỹ năng quan trọng, đặc biệt trong môi trường gần với production.  
  Tư duy này sẽ rất hữu ích khi các tuần sau bắt đầu làm việc với kiến trúc và dịch vụ phức tạp hơn.

---

#### 1. Đánh giá bản thân

* **Tự tin hơn khi làm việc với Billing console**  
  Lúc đầu, mình vẫn hơi ngại vào mục Billing vì sợ cấu hình sai gây phát sinh chi phí. Đến cuối tuần, sau khi đã tạo, chỉnh sửa và xóa nhiều budgets khác nhau, mình tự tin hơn khi điều hướng và đọc các thông tin liên quan đến chi phí.

* **Hiểu rõ hơn về khả năng quan sát chi phí và cảnh báo**  
  Mình bắt đầu suy nghĩ theo hướng:
  * “Nếu mình quên tắt một số tài nguyên thì chuyện gì sẽ xảy ra?”  
  * “Làm sao mình biết trước là chi phí sắp vượt mức cho phép?”  
  Đây là một bước tiến lớn so với việc chỉ nghĩ về chức năng kỹ thuật thuần túy.

* **Cách học có quy trình rõ ràng hơn**  
  Mình tuân theo một chu trình:
  * Học khái niệm → làm lab thực hành → xem lại kết quả → dọn dẹp tài nguyên.  
  Cách này giúp mình ghi nhớ lâu hơn và tránh tình trạng chỉ “click cho xong” mà không hiểu gì.

#### 2. Khó khăn gặp phải

* **Khó phân biệt lúc đầu nên dùng loại budget nào**  
  Ban đầu mình khá rối khi:
  * Khi nào dùng **Cost Budget** và khi nào dùng **Usage Budget**?  
  * Trong trường hợp nào **RI** và **Savings Plans** Budget mới thực sự cần thiết?  
  Mình vượt qua bằng cách gắn mỗi loại budget với các tình huống sử dụng thực tế (ví dụ: sử dụng EC2 lâu dài, có cam kết dùng Savings Plans, hay môi trường sinh viên/Free Tier).

* **Khó hiểu sự khác nhau giữa số liệu dự đoán và số liệu thực tế**  
  Mình mất một khoảng thời gian để hiểu:
  * Sự khác nhau giữa **actual** và **forecasted** cost/usage.  
  * Tại sao alert có thể bật lên dù chi tiêu hiện tại vẫn chưa vượt budget (do dự đoán sẽ vượt).  
  Điều này đòi hỏi mình phải đọc kỹ thông tin trên console và thử nghiệm với nhiều ngưỡng khác nhau.

* **Làm quen với quy trình tạo support case**  
  Lần đầu tạo support case, mình gặp khó khăn trong việc:
  * Chọn đúng **category** và mức độ ưu tiên (**severity**).  
  * Viết mô tả vấn đề sao cho rõ ràng, ngắn gọn.  
  Sau vài lần thực hành, mình dần biết cách mô tả sự cố hiệu quả hơn – đây là kỹ năng quan trọng trong các dự án thực tế.

---

Nhìn chung, Tuần 2 giúp mình củng cố hiểu biết về **quản lý chi phí** và **quy trình hỗ trợ** trên AWS. Đây là những kỹ năng thiết yếu để vận hành workload thực tế trên cloud, chứ không chỉ để hoàn thành lab hay bài thực hành. Kiến thức học được sẽ giúp mình tránh các tình huống thường gặp như hóa đơn bất ngờ tăng cao hoặc cảm giác “bí” khi hệ thống gặp sự cố trên môi trường đám mây.
