---
title: "Worklog Tuần 12"
date: "`r Sys.Date()`"
weight: 12
chapter: false
pre: " <b> 1.12 </b> "
---

### Mục tiêu tuần 12:

* Hoàn thiện **RAG Chat Component (M2)** với các chức năng quan trọng: rate limiting, fallback model, error handling & retry logic.
* Khởi động giai đoạn **Testing & Go-live (M3)** — tập trung vào login page, chat UI, admin dashboard và bắt đầu kiểm thử end-to-end toàn hệ thống.

---

### Các công việc cần triển khai trong tuần này:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | ---------------- | -------------- |
| 2 | - Implement Rate Limiter (60 RPM, 100K TPM) <br> - Tích hợp Budget Manager (giới hạn $10/day, $200/month) <br> - Viết test cho toàn bộ rate limiting logic | 24/11/2025 | 24/11/2025 | https://docs.aws.amazon.com/bedrock/ |
| 3 | - Implement fallback sang Claude Haiku khi Sonnet bị rate limit/timeout <br> - Xây dựng error handling pipeline và retry với exponential backoff + jitter <br> - Viết tests (35 tests passed) | 25/11/2025 | 25/11/2025 | https://docs.aws.amazon.com/bedrock/ |
| 4 | - Xây dựng login page tích hợp Cognito Hosted UI <br> - Implement AuthService: parse & validate JWT, handle refresh tokens <br> - Test full authentication flow từ login → callback → lưu token | 26/11/2025 | 26/11/2025 | https://docs.aws.amazon.com/cognito/ |
| 5 | - Build giao diện Chat UI bằng React <br> - Implement ChatPage: message bubbles, context display, citations renderer <br> - Tạo component `CitationCard` & `DocumentViewerModal` | 27/11/2025 | 27/11/2025 | https://react.dev/ |
| 6 | - Build Admin Dashboard: drag-drop upload, document list, status tracking <br> - Hiển thị real-time document processing status (auto-refresh mỗi 5s) <br> - Bắt đầu integration testing E2E (Auth → Chat → Admin → Logs) | 28/11/2025 | 28/11/2025 | https://react.dev/ |

---

### Kết quả đạt được tuần 12:

#### **1. Hoàn thiện RAG Chat (M2)**

* **Rate Limiter** cho toàn bộ LLM requests: giới hạn 60 requests/minute và 100K tokens/minute.
* **Budget Manager** giúp bảo vệ chi phí:  
  - Giới hạn **$10/ngày**, **$200/tháng**  
  - Ngăn spam & misuse trong môi trường staging/production  
  - 22 unit tests passed
* **Retry logic** với exponential backoff + jitter, giảm lỗi tạm thời từ Bedrock.  
* **Fallback model logic**:  
  - Mặc định dùng **Claude 3.5 Sonnet**  
  - Khi gặp rate limit/timeout → **tự động fallback sang Claude Haiku**  
  - Tăng độ ổn định cho user trải nghiệm.

---

#### **2. Bắt đầu Testing & Go-live (M3)**

* **AuthService hoàn chỉnh**:  
  - Decode + validate Cognito JWT  
  - Lưu & refresh tokens an toàn  
  - Tích hợp trực tiếp vào frontend  
* **Chat UI v1.0**:  
  - Message bubbles mượt, hỗ trợ streaming  
  - Citation inline + hiển thị modal chi tiết  
  - UX gần với production standard  
* **Components mới**:  
  - `CitationCard` — hiển thị thông tin nguồn  
  - `DocumentViewerModal` — xem nội dung PDF đã xử lý  
* **Admin Dashboard**:  
  - Drag-drop upload file  
  - Bảng liệt kê document + trạng thái real-time  
  - Auto-refresh để theo dõi pipeline  
* **Bắt đầu E2E Testing**: login → chat → upload → process logs → display results.

---

### Học được:

* Các mô hình rate limiting cho AI APIs: token bucket, leaky bucket, request throttling.  
* Cách quản lý chi phí với Bedrock: fallback, token budgeting, usage monitoring.  
* Exponential backoff với jitter — tăng độ ổn định hệ thống khi API lỗi tạm thời.  
* Xây dựng React UI phức tạp (streaming messages, citation linking, modals).  
* JWT validation với Cognito — cách trích token, verify signature, decode claims.  

---

