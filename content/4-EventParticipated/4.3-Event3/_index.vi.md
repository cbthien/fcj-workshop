---
title: "Event 3"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 4.3 </b> "
---

# Bài thu hoạch: “AWS Cloud Mastery Series #3 – AWS Well-Architected Security Pillar Workshop”

---

##  Mục Tiêu Sự Kiện

- Chia sẻ và củng cố kiến thức cốt lõi trong **AWS Well-Architected Framework – Security Pillar**.  
- Trang bị tư duy và kỹ năng xây dựng hệ thống **an toàn, bền vững, tuân thủ chuẩn AWS**.  
- Đi sâu vào 5 trụ cột bảo mật chính:

  1. **Identity & Access Management (IAM)**  
  2. **Detection & Continuous Monitoring**  
  3. **Infrastructure Protection**  
  4. **Data Protection**  
  5. **Incident Response**

- Giới thiệu sáng kiến **AWS Cloud Clubs** và các hoạt động cộng đồng hỗ trợ sinh viên học cloud tại trường đại học.

---

##  Diễn Giả

- **Lê Vũ Xuân An** – AWS Cloud Club Captain HCMUTE  
- **Trần Đức Anh** – AWS Cloud Club Captain SGU  
- **Trần Đoàn Công Lý** – AWS Cloud Club Captain PTIT  
- **Danh Hoàng Hiếu Nghị** – AWS Cloud Club Captain HUFLIT  
- **Huỳnh Hoàng Long** – AWS Community Builder  
- **Đinh Lê Hoàng Anh** – AWS Community Builder / Cloud Engineer Trainee  
- **Nguyễn Tuấn Thịnh** – Cloud Engineer Trainee  
- **Nguyễn Đỗ Thành Đạt** – Cloud Engineer Trainee  
- **Văn Hoàng Kha** – Cloud Security Engineer, AWS Community Builder  
- **Thịnh Lâm** – FCJ Member  
- **Việt Nguyễn** – FCJ Member  
- **Mendel Grabski (Long)** – Ex-Head of Security & DevOps, Cloud Security Solution Architect  
- **Trịnh Trương** – Platform Engineer tại TymeX, AWS Community Builder  

(Cùng với các anh/chị trong **FCJ Team** và cộng đồng AWS.)

---

#  Các Điểm Nổi Bật

##  Giới Thiệu AWS Cloud Club & Security Foundation

Sự kiện mở đầu với:

- Giới thiệu về **AWS Cloud Club**:
  - Nền tảng giúp sinh viên phát triển kỹ năng cloud qua **tình huống thực tế**.  
  - Cơ hội nhận **mentorship** từ chuyên gia AWS & cộng đồng.  
  - Xây dựng cộng đồng, kết nối sinh viên từ nhiều trường: HCMUTE, SGU, PTIT, HUFLIT…

- **Security Foundation – Nền tảng bảo mật AWS**:
  - **Least Privilege – Zero Trust – Defense in Depth**: 3 nguyên tắc nền tảng cho hệ thống bảo mật hiện đại.  
  - **Shared Responsibility Model**:
    - AWS bảo mật **của cloud**.  
    - Khách hàng bảo mật **trong cloud**.

- **Top Cloud Threats tại Việt Nam**:
  - Public S3 / databases / Redis  
  - Lộ access key  
  - IAM cấu hình sai  
  - EC2 nhiễm malware (đào coin)  
  - Thiếu logging hoặc không bật GuardDuty  

Thông điệp chính: **Security = culture, not a feature** – bảo mật là văn hóa, không phải tính năng gắn thêm.

---

##  Trụ cột 1 – Identity & Access Management (IAM)

IAM là trọng tâm của Security Pillar:

- Áp dụng **Least Privilege** triệt để.  
- Xóa **root access keys** sau khi thiết lập ban đầu.  
- Tránh dùng **wildcard permission (`*`)**.  

### Modern IAM Practices

- **IAM Users**: gần như không còn phù hợp → ưu tiên:
  - **Roles > Users**  
  - **SSO > Local credentials**  
  - **OIDC > Access Keys**  

- **IAM Identity Center (SSO)**:
  - Quản lý người dùng & quyền trong **multi-account environment**.  

- **Quyền tổ chức (Organizational controls)**:
  - Dùng **SCP (Service Control Policies)** để giới hạn quyền ở mức organization.  
  - Sử dụng **Permission Boundaries** để giới hạn phạm vi quyền của user/role.

- **Xác thực & giám sát**:
  - Bắt buộc **credential rotation** & **MFA**.  
  - Dùng **IAM Access Analyzer** để phát hiện policy quá rộng, public, sharing ngoài ý muốn.  
  - MFA với **TOTP** vs **FIDO2**: so sánh về bảo mật & khả năng phục hồi.

- **Secrets Management**:
  - Dùng **AWS Secrets Manager** với vòng đời xoay vòng:  
    `create → set → test → finalize`  
  - Không hard-code secrets trong code / môi trường.

---

##  Trụ cột 2 – Detection & Continuous Monitoring

### Multi-layer Observability

- **CloudTrail**:
  - Management Events: API calls, thay đổi cấu hình.  
  - Data Events: activity chi tiết trên S3 object, Lambda execution.  
  - Triển khai **organization-level CloudTrail** cho toàn bộ accounts.

- **Logging sources**:
  - **VPC Flow Logs**, **S3 access logs**, **ALB logs** để truy vết network & access patterns.

- **Amazon GuardDuty**:
  - Dịch vụ phát hiện mối đe dọa liên tục, phân tích:
    - CloudTrail events  
    - VPC Flow Logs  
    - DNS queries  
  - Phát hiện:
    - Tắt logging  
    - Lưu lượng bất thường  
    - Truy cập domain độc hại  
    - Malware scanning trên S3  
    - EKS audit logs  
    - RDS anomaly detection  
    - Lambda network behavior, runtime protection  
  - Liên hệ với **AWS Foundational Security Best Practices** & **CIS Benchmarks**.

- **Security Hub**:
  - Tổng hợp findings từ GuardDuty, IAM Access Analyzer, Config, v.v. vào một **dashboard trung tâm**.

### Alerting & Automation

- Dùng **EventBridge** để:
  - Gửi cảnh báo (SNS, email, chat…).  
  - Trigger **Lambda / Step Functions** cho tự động **remediation**.  
  - Hỗ trợ **cross-account event routing** cho mô hình security tập trung.

- **Detection-as-Code**:
  - Quản lý detection logic như IaC:
    - CloudTrail Lake queries  
    - Event patterns trên EventBridge  
  - Giúp review, test, deploy detection rules có kiểm soát.

> Case study: Nếu không có logs → không có bằng chứng → không thể điều tra incident.

---

## Trụ cột 3 – Infrastructure Protection

- **VPC Segmentation**:
  - Giảm **blast radius** khi hệ thống bị tấn công bằng cách chia nhỏ & cô lập môi trường.  

- **Subnet placement (Public vs Private)**:
  - Public: ALB, NAT Gateway, public bastion (nếu có).  
  - Private: EC2 app, databases, internal services.  

- **Security Group (SG) vs Network ACL (NACL)**:
  - **SG**: stateful, gắn vào instance, là “tường chính”.  
  - **NACL**: stateless, gắn vào subnet, là lớp bổ trợ.

- **Edge Protection**:
  - **AWS WAF**, **Shield Advanced**, **AWS Network Firewall** cho lớp phòng thủ biên.  
  - Tích hợp threat intel từ **GuardDuty** để tự động chặn.

- **Workload Hardening**:
  - Patching thường xuyên EC2/ECS/EKS.  
  - Giảm thiểu quyền IAM cho workload.  
  - Image scanning trước khi deploy.  
  - Runtime protections.

> Case study: Rất nhiều lỗi bảo mật đến từ việc đặt nhầm tài nguyên vào **public subnet** – luôn check placement trước khi deploy.

---

##  Trụ cột 4 – Data Protection

- **Encryption everywhere**:
  - Bật mã hóa at-rest cho S3, EBS, RDS, DynamoDB.  
  - Bắt buộc TLS/HTTPS khi truy cập S3, DynamoDB, RDS…

- **AWS KMS**:
  - Quản lý **CMK → Data Key**.  
  - Key policies, Grants, rotation.  
  - Dùng IAM conditions để kiểm soát hoạt động mã hóa/giải mã.

- **Secrets Management**:
  - **Secrets Manager** / **SSM Parameter Store**:
    - Secret rotation tự động.  
    - Tách biệt config & secret khỏi code.  

- **ACM (AWS Certificate Manager)**:
  - Cung cấp chứng chỉ miễn phí + auto-renew cho ALB, CloudFront, API Gateway.

- **Data classification & guardrails**:
  - Phân loại dữ liệu theo sensitivity (Public / Internal / Confidential / Restricted).  
  - Áp dụng guardrails tương ứng: IAM, encryption, network controls.

> Case study: Encrypt từ đầu giúp giảm đáng kể rủi ro khi xảy ra data breach.

---

##  Trụ cột 5 – Incident Response (IR)

- **AWS IR Lifecycle**:  
  **Prepare → Detect → Investigate → Respond → Recover**

### Playbooks (ví dụ)

- **IAM key bị compromise**  
- **S3 bucket bị public**  
- **EC2 dính malware / mining**

### Công cụ & kỹ thuật xử lý

- Tạo **Snapshot** (EBS / instance) để lưu evidence.  
- **Isolation**: thay đổi SG / NACL để cô lập instance.  
- Thu thập evidence phục vụ **forensics & audit**.

### IR Automation

- **Lambda**: chạy remediation nhỏ (revert policy, block IP, disable key…).  
- **Step Functions**: điều phối quy trình IR phức tạp nhiều bước.  
- **EventBridge**: trigger playbooks dựa trên sự kiện từ GuardDuty, CloudTrail, Security Hub…

> Kết luận: Incident Response không thể phụ thuộc 100% vào con người – cần tự động hóa càng nhiều càng tốt.

---

#  Những Gì Học Được

## Tư Duy Bảo Mật Hiện Đại

- **Zero Trust & Least Privilege**: không tin mặc định, mọi quyền đều tối thiểu.  
- **Defense in Depth**: nhiều lớp phòng thủ để giảm rủi ro khi một lớp bị vượt qua.  
- **Traceability & IaC**:
  - Mọi thay đổi phải **traceable**.  
  - Hạ tầng nên được triển khai bằng **IaC** để giảm misconfiguration.  
- Không tin vào cấu hình tay → ưu tiên automation + IaC + review.

## Kiến Trúc Kỹ Thuật Quan Trọng

- **IAM**:
  - Roles > Users  
  - SSO > Local credentials  
  - OIDC > Long-lived Access Keys  

- **Network**:
  - **Private-first**: mặc định đặt tài nguyên vào private subnet.  
  - SG là “tường chính” (stateful), NACL là lớp hỗ trợ (stateless).  
  - Outbound filtering quan trọng không kém inbound.

- **Data**:
  - Encrypt by default (S3, EBS, RDS, DynamoDB).  
  - Secret rotation theo policies.  
  - Giảm tối đa exposure cho S3/DB.

- **Detection**:
  - CloudTrail **ON**  
  - GuardDuty **ON**  
  - Logging đầy đủ để phục vụ điều tra sự cố.

- **Incident Response**:
  - Có playbook rõ ràng.  
  - Có automation cho remediation & rollback.  
  - Có snapshot/backup để phục hồi nhanh.

## Chiến Lược Hiện Đại Hóa

- Không làm ồ ạt, mà đi theo **phased approach**.  
- Dùng **multi-account architecture** để giảm blast radius và tách biệt môi trường.

---

#  Ứng Dụng Vào Công Việc

Trong dự án **AI Chatbot** của nhóm:

- Thiết kế IAM dựa trên **Roles + Permission Sets** thay vì user trực tiếp.  
- Áp dụng **VPC segmentation** và **private-first design** cho backend, DB, vector store.  
- Bật **GuardDuty + CloudTrail ở org-level** cho toàn bộ môi trường dev/prod.  
- Thiết lập **Alerting & IR automation**:
  - EventBridge → Lambda / Step Functions cho auto-remediation.  
- Dùng **Secrets Manager + rotation** thay vì hard-code secret trong code/ENV.  
- Triển khai hạ tầng bằng **Terraform/CDK** để giảm drift và sai sót cấu hình.

Kết quả kỳ vọng: hệ thống chatbot **ổn định hơn, an toàn hơn, dễ audit và dễ mở rộng**.

---

#  Trải Nghiệm Sự Kiện

- Sự kiện được tổ chức tốt, giúp tôi có cái nhìn **toàn diện về Security Pillar** trong AWS Well-Architected.  
- Học hỏi được cách AWS và các doanh nghiệp lớn:
  - Tổ chức mô hình multi-account.  
  - Xử lý incident & detection trong môi trường production thực tế.  

### Trải nghiệm kỹ thuật

- Thực hành phân tích policy bằng **IAM Simulator**.  
- Thấy được flow thực tế của **S3 public exposure → auto-remediation**.  
- Quan sát **IR automation** xử lý EC2 bị compromise.  

### Tư duy & kết nối

- Nhận ra cách doanh nghiệp lớn tổ chức bảo mật theo kiến trúc **multi-account**.  
- Thấm nhuần tư duy **“secure by design”** – không chờ bị tấn công mới vá.  
- Kết nối với các bạn cùng đam mê security/cloud, tạo nền tảng cho học tập & làm việc lâu dài.

### Bài học rút ra

- **Security = culture, not a feature.**  
- **Misconfiguration** là nguyên nhân lớn nhất → **IaC là cứu cánh**.  
- Không thể vận hành cloud an toàn nếu thiếu: **IAM tốt + Logging đầy đủ + IR rõ ràng**.

## Một số hình ảnh khi tham gia sự kiện
![ws Image](/images/ws3.jpg)

![ws Image](/images/ws3.1.jpg)

![ws Image](/images/ws3.2.jpg)