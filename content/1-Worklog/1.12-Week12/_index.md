---
title: "Week 12 Worklog"
date: "`r Sys.Date()`"
weight: 12
chapter: false
pre: " <b> 1.12 </b> "
---

### Week 12 Objectives

* Complete the **RAG Chat Component (M2)** — Rate limiting, fallback model, error handling, and retry logic.  
* Begin **Testing & Go-live (M3)** — Login page, Chat UI, Admin Dashboard, and initiate end-to-end testing flow.

---

### Tasks to carry out this week:

| Day | Tasks | Start Date | Completion Date | Reference |
| --- | ------ | ----------- | ---------------- | ---------- |
| 2 | - Implement Rate Limiter (60 RPM, 100K TPM) <br> - Add Budget Manager ($10/day, $200/month limits) <br> - Write tests for rate-limiting logic | 24/11/2025 | 24/11/2025 | https://docs.aws.amazon.com/bedrock/ |
| 3 | - Implement fallback to Claude Haiku when Sonnet is rate-limited <br> - Add error handling & retry logic with exponential backoff + jitter <br> - Write tests (35 tests passed) | 25/11/2025 | 25/11/2025 | https://docs.aws.amazon.com/bedrock/ |
| 4 | - Implement login page integrated with Cognito Hosted UI <br> - Build AuthService for JWT parsing & validation <br> - Test full authentication flow end-to-end | 26/11/2025 | 26/11/2025 | https://docs.aws.amazon.com/cognito/ |
| 5 | - Build Chat UI using React <br> - Implement ChatPage with message bubbles & citation display <br> - Create `CitationCard` and `DocumentViewerModal` components | 27/11/2025 | 27/11/2025 | https://react.dev/ |
| 6 | - Build Admin Dashboard with drag-and-drop upload <br> - Display real-time processing status (auto-refresh every 5s) <br> - Begin E2E Integration Testing (Auth → Chat → Admin → Logs) | 28/11/2025 | 28/11/2025 | https://react.dev/ |

---

### Week 12 Achievements

#### **1. Completed RAG Chat (M2)**

* **Rate Limiter** implemented for LLM requests:  
  - 60 requests/minute  
  - 100K tokens/minute  
* **Budget Manager** added to guard against overspending:  
  - $10/day, $200/month caps  
  - 22 automated tests passed  
* **Retry mechanism** implemented using exponential backoff + jitter for higher stability under transient API failures.  
* **Fallback model logic**:  
  - Primary: **Claude 3.5 Sonnet**  
  - Automatic fallback: **Claude Haiku** during rate limit or timeout  
  → Significantly improves reliability and user experience.

---

#### **2. Initiated Testing & Go-live (M3)**

* **AuthService with JWT validation** fully implemented:  
  - Token parsing, signature validation, claim extraction  
  - Integrated into frontend login flow  
* **Chat UI v1.0 completed**:  
  - Smooth message bubbles with support for streaming responses  
  - Inline citations & detailed citation modal  
* **New components**:  
  - `CitationCard` — displays document reference  
  - `DocumentViewerModal` — previews processed PDF content  
* **Admin Dashboard**:  
  - Drag-and-drop upload interface  
  - Document list & real-time status updates  
  - Auto-refresh for monitoring processing pipeline  
* **E2E Testing started**: Auth → Chat interactions → Document upload & processing → Data displayed in UI.

---

### Learnings

* Rate-limiting patterns for AI APIs: token bucket, request throttling, and token-based limits.  
* Cost-management patterns for Bedrock: fallback models, usage budgeting, token accounting.  
* How to implement exponential backoff with jitter to reduce collision & improve reliability.  
* Building advanced React UI components for chat systems (streaming messages, citation linking, modals).  
* Cognito JWT validation — decoding tokens, verifying signatures, validating claims and expiry.  

---
