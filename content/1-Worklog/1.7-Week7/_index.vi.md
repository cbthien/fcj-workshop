---
title: "Nhật ký Tuần 7"
date: "2025-10-20"
weight: 7
chapter: false
pre: " <b> 1.7 </b> "
---

### Mục tiêu Tuần 7:

* Học cách triển khai và tối ưu kiến trúc AWS cho một dự án thực tế.
* Ôn tập lại các kiến thức AWS cốt lõi.
* Thử nghiệm triển khai chatbot Text-to-SQL và đánh giá các hướng mở rộng.
* Phân tích bảo mật cơ sở dữ liệu và luồng xử lý dữ liệu trong hệ thống.
* Nâng cao khả năng tư duy về chi phí, độ tin cậy và bảo mật khi phát triển kiến trúc hiện có.

---

### Các nhiệm vụ thực hiện trong tuần:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | ----- | ---------- | ---------------- | ------------------ |
| 2 | - Tìm hiểu cách downscale (giảm quy mô) dự án. <br> - Học cách triển khai một kiến trúc trên AWS. <br> - Ghi nhận một sự cố hiếm gặp: **AWS outage tại us-east-1**, ảnh hưởng đến nhiều hệ thống. | 20/10/2025 | 20/10/2025 | Internal AWS reports, incident reports |
| 3 | - Ôn tập lại các kiến thức AWS cốt lõi để chuẩn bị cho đánh giá. | 21/10/2025 | 21/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Vẽ lại kiến trúc tổng thể và ước tính chi phí cho dự án. <br> - Xác định định hướng ban đầu cho chatbot của dự án. <br> - Tài liệu định hướng (Notion). | 22/10/2025 | 22/10/2025 | Draw.io |
| 5 | - Tìm hiểu **bảo mật cơ sở dữ liệu** và **logic xử lý dữ liệu an toàn** để tránh các thao tác sai của người dùng (update/insert/delete không hợp lệ). <br> - **Triển khai chatbot Text2SQL** theo hướng dẫn trên AWS Blog. <br> - AWS Blog: *Build an AI-powered Text-to-SQL Chatbot*. | 23/10/2025 | 23/10/2025 | AWS Blog |
| 6 | - Đọc và hiểu **mã nguồn chatbot Text2SQL**. <br> - Ghi chú họp trên Notion. <br> - Họp nhóm: làm rõ cách chatbot tương tác với cơ sở dữ liệu, các biện pháp bảo mật và **giới hạn quyền truy cập DB**. <br> - Đề xuất thay thế **RAG bằng cache DynamoDB** để giảm chi phí so với OpenSearch. | 24/10/2025 | 24/10/2025 | Notion, AWS Blog |

---

### Thành tựu Tuần 7

Tuần 7 đánh dấu bước chuyển từ các bài thực hành cơ bản sang **làm việc với một kiến trúc gần với môi trường production hơn**. Thay vì chỉ làm theo tutorial, mình phải suy nghĩ về việc hệ thống sẽ scale như thế nào, tốn bao nhiêu chi phí, và làm sao để giữ an toàn khi tích hợp chatbot Text2SQL.

* **Cải thiện hiểu biết về downscaling dự án và tối ưu tài nguyên**  
  Đầu tuần, mình tập trung vào cách **giảm quy mô dự án hiện tại** để phù hợp với các ràng buộc thực tế (môi trường sinh viên, ngân sách hạn chế, workload có kiểm soát).  
  * Xem lại những thành phần nào thật sự cần chạy 24/7 và thành phần nào có thể giảm quy mô hoặc tắt khi không cần.  
  * Cân nhắc các lựa chọn như giảm kích thước instance, dùng ít AZ hơn nếu chấp nhận được, và loại bỏ các tài nguyên test không cần thiết.  
  Điều này giúp mình nhận ra tối ưu không phải lúc nào cũng là “thêm dịch vụ”, mà nhiều khi là **loại bỏ hoặc đơn giản hóa** những phần không cần thiết.

* **Củng cố nền tảng kiến trúc AWS thông qua ôn tập và áp dụng**  
  Mình ôn lại các khái niệm **AWS cốt lõi** (networking, compute, storage, IAM, bảo mật, fault tolerance) không chỉ để thi mà để gắn trực tiếp với dự án hiện tại:  
  * Kiểm tra lại cách VPC, subnet, security group và routing kết nối với nhau trong thiết kế hiện tại.  
  * Liên kết lý thuyết từ tài liệu học với các quyết định kiến trúc cụ thể trong hệ thống chatbot.  
  Việc ôn tập này giúp hiểu biết của mình vững hơn và bớt “màu thi cử”; mình có thể giải thích rõ hơn tại sao chọn các dịch vụ AWS đó trong kiến trúc.

* **Thiết kế lại kiến trúc tổng thể và xây dựng phiên bản có ý thức về chi phí**  
  Trong nhiệm vụ vẽ lại kiến trúc, mình:  
  * Tạo một phiên bản kiến trúc mới phản ánh **phạm vi dự án hiện tại**, bao gồm chatbot Text2SQL, cơ sở dữ liệu và các thành phần hỗ trợ.  
  * Thêm góc nhìn chi phí vào sơ đồ (ví dụ: thành phần nào tạo chi phí cố định hàng tháng, thành phần nào scale theo mức sử dụng, và nơi nào có thể tận dụng free tier hoặc dịch vụ serverless).  
  * Ghi lại kiến trúc và các giả định về pricing trong Notion để team cùng thảo luận và phản biện.  
  Đây là bước quan trọng để chuyển từ “kiến trúc kiểu lab” sang một thiết kế gần hơn với **dự án thực tế**.

* **Xác định định hướng ban đầu cho chatbot Text2SQL**  
  Mình làm rõ cách chatbot cần hoạt động ở góc độ **trải nghiệm người dùng** và **thiết kế hệ thống**:  
  * Mô tả flow: từ câu hỏi của người dùng → prompt gửi cho model → sinh SQL → kiểm tra/validate → thực thi → format kết quả trả về.  
  * Ghi lại các ràng buộc như độ phức tạp truy vấn tối đa, giới hạn timeout, và các bước kiểm tra an toàn trước khi chạy SQL được sinh ra.  
  * Liệt kê các câu hỏi còn mở (ví dụ: log query như thế nào, giám sát lạm dụng ra sao, giới hạn tài nguyên thế nào).  
  Nhờ đó, dự án có một định hướng kỹ thuật rõ hơn thay vì chỉ dừng lại ở mức “muốn làm một chatbot Text2SQL”.

* **Triển khai chatbot Text2SQL theo hướng dẫn AWS Blog**  
  Mình làm theo tutorial chính thức trên AWS Blog để **triển khai chatbot Text-to-SQL có dùng AI**:  
  * Thiết lập các thành phần hạ tầng cần thiết (API, Lambda functions, kết nối cơ sở dữ liệu, và tích hợp Bedrock nếu áp dụng).  
  * Deploy giải pháp mẫu và kiểm tra rằng câu hỏi của người dùng được chuyển thành truy vấn SQL và thực thi đúng trên database.  
  * Xem log và trace để đảm bảo các lỗi (truy vấn không hợp lệ, timeout, lỗi cú pháp) được xử lý an toàn.  
  Việc triển khai thành công chatbot giúp mình tự tin hơn trong việc tích hợp các thành phần AI vào kiến trúc cloud.

* **Phân tích bảo mật cơ sở dữ liệu và logic xử lý dữ liệu an toàn**  
  Để đảm bảo chatbot không làm hỏng hệ thống hoặc dữ liệu, mình:  
  * Tìm hiểu các pattern **safe data logic** để tránh các thao tác nguy hiểm như UPDATE/DELETE/INSERT ngoài ý muốn hoặc thiếu điều kiện.  
  * Cân nhắc dùng **role chỉ đọc (read-only)** cho các truy vấn Text2SQL nhằm giới hạn khả năng chỉnh sửa dữ liệu.  
  * Suy nghĩ về lớp validation để kiểm tra hoặc hạn chế câu SQL được sinh ra trước khi thực thi.  
  Qua đó, mình nhận ra hệ thống có dùng AI càng cần **kiểm soát và validate chặt chẽ** hơn so với ứng dụng truyền thống.

* **Đọc và hiểu mã nguồn chatbot Text2SQL**  
  Mình xem chi tiết **mã nguồn** của giải pháp:  
  * Phân tích cách tạo prompt, cách sinh SQL và cách chuyển kết quả thành câu trả lời thân thiện với người dùng.  
  * Ghi chú lại cách code xử lý lỗi, logging và tích hợp với các dịch vụ AWS.  
  * Gắn từng phần code với các thành phần trong kiến trúc (ví dụ: Lambda nào đảm nhiệm bước nào trong flow).  
  Điều này giúp mình hiểu sâu hơn ở mức triển khai thay vì xem giải pháp như một “hộp đen”.

* **Đánh giá việc thay thế RAG bằng cache dựa trên DynamoDB để giảm chi phí**  
  Trong buổi họp nhóm, bọn mình thảo luận trade-off giữa **RAG dùng OpenSearch** và **cache bằng DynamoDB**:  
  * Nhận ra rằng với một số loại truy vấn, kết hợp dữ liệu có cấu trúc + cache có thể rẻ và đơn giản hơn so với giải pháp vector search đầy đủ.  
  * Đề xuất dùng DynamoDB làm cache cho các truy vấn thường gặp hoặc kết quả đã được xử lý trước để giảm cả độ trễ và chi phí OpenSearch.  
  * Cân nhắc tác động lên tính linh hoạt: DynamoDB cache “ít linh hoạt” hơn RAG, nhưng đủ dùng cho các pattern truy vấn được định hình rõ.  
  Qua đó, mình học được cách cân nhắc giữa **chi phí và độ linh hoạt**, tránh mặc định chọn giải pháp phức tạp nhất.

* **Rút kinh nghiệm từ sự cố thật AWS outage (khu vực us-east-1)**  
  Khi ghi nhận sự cố **AWS outage tại us-east-1**, mình:  
  * Suy nghĩ về việc một sự cố cấp vùng có thể ảnh hưởng đồng thời rất nhiều hệ thống như thế nào.  
  * Nghĩ về cách kiến trúc hiện tại của mình sẽ ứng xử trong tình huống tương tự và những chiến lược giảm thiểu nào (multi-AZ, multi-region, fallback) có thể cân nhắc trong tương lai.  
  Trải nghiệm này giúp mình nâng cao nhận thức về **tính chịu lỗi và khả năng phục hồi**, vượt ra khỏi phạm vi thiết kế chỉ trong một region.

---

#### 1. Tự đánh giá

* **Tự tin hơn khi thảo luận về kiến trúc và trade-off**  
  Mình cảm thấy thoải mái hơn khi giải thích tại sao sử dụng một dịch vụ nhất định, chúng kết nối với nhau ra sao và trade-off giữa chi phí, hiệu năng, độ phức tạp là gì.

* **Giỏi hơn trong việc liên kết giữa code và kiến trúc**  
  Việc đọc mã nguồn của chatbot Text2SQL và mapping lại với sơ đồ kiến trúc giúp mình hiểu rõ cách các quyết định thiết kế ở mức cao được triển khai thành code cụ thể.

* **Cải thiện nhận thức bảo mật cho hệ thống dùng AI**  
  Giờ đây mình chú ý nhiều hơn đến quyền truy cập dữ liệu khi có LLM hoặc cơ chế sinh SQL tự động, thay vì chỉ kiểm tra xem “nó chạy được hay không”.

#### 2. Khó khăn gặp phải

* **Cân bằng giữa độ phức tạp và chi phí**  
  Khó khăn lớn là quyết định khi nào nên dùng các thành phần nâng cao (như RAG + OpenSearch) và khi nào một pattern đơn giản hơn (như cache bằng DynamoDB) là đủ. Điều này đòi hỏi sự phán đoán chứ không chỉ làm theo best practice.

* **Tư duy về outage và tính chịu lỗi**  
  Việc tưởng tượng các sự cố hiếm như outage cả một region không hề tự nhiên lúc đầu. Mình phải “căng não” để suy nghĩ theo kiểu “nếu cả region này không còn hoạt động thì sao?” thay vì chỉ tập trung vào trạng thái hệ thống chạy bình thường.

* **Hiểu toàn bộ luồng Text2SQL chi tiết**  
  Một số phần trong flow giữa model AI, sinh SQL và thực thi trên database khá phức tạp. Mình cần thời gian để lần theo toàn bộ đường đi của request và hiểu rõ từng bước.

---

Nhìn chung, Tuần 7 giúp mình tiến gần hơn tới mindset của một **cloud engineer làm dự án thực**: không chỉ triển khai các thành phần, mà còn tối ưu kiến trúc, kiểm soát chi phí, bảo vệ dữ liệu và chuẩn bị cho các tình huống sự cố, trong khi vẫn tích hợp các khả năng AI vào hệ thống.
