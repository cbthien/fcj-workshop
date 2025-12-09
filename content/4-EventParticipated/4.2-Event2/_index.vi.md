---
title: "Event 2"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 4.2 </b> "
---

# Bài thu hoạch: “AWS Cloud Mastery Series #2 – DevOps on AWS”

---

##  Mục Đích Của Sự Kiện

- Giới thiệu về các dịch vụ **DevOps trên AWS** và cách thiết kế **pipeline CI/CD**.  
- Trang bị **tư duy DevOps hiện đại** và cách áp dụng trên hệ sinh thái AWS.  
- Khám phá các khái niệm về **Infrastructure as Code (IaC)** và các công cụ liên quan (CloudFormation, CDK, Terraform).  
- Trình bày tổng quan về các **workload dạng container** trên AWS (ECR, ECS, EKS, App Runner).  
- Minh họa cách đạt được **giám sát và quan sát (monitoring & observability)** hiệu quả bằng các dịch vụ gốc của AWS.  
- Tối ưu **tốc độ phát triển, chất lượng release và độ tin cậy** của hệ thống.

---

##  Danh Sách Diễn Giả

- **Trương Quang Tình** – AWS Community Builder, Platform Engineer (TymeX)  
- **Bảo Huỳnh** – AWS Community Builder  
- **Nguyễn Khánh Phúc Thịnh** – AWS Community Builder  
- **Trần Đại Vĩ** – AWS Community Builder  
- **Huỳnh Hoàng Long** – AWS Community Builder  
- **Phạm Hoàng Quý** – AWS Community Builder  
- **Nghiêm Lê** – AWS Community Builder  
- **Đinh Lê Hoàng Anh** – Cloud Engineer Trainee, First Cloud AI Journey  

(Cùng với các anh/chị trong **FCJ Team**, **AWS Developer Advocate Team** và khách mời cộng đồng.)

---

#  Nội Dung Nổi Bật

##  Xây dựng nền tảng tư duy DevOps

Các diễn giả nhấn mạnh: **DevOps không chỉ là job title** mà là **tư duy + thói quen làm việc**:

- Tự động hóa (automation) các tác vụ lặp đi lặp lại.  
- Chia sẻ kiến thức giữa các vai trò (Dev, Ops, QA, Security…).  
- Liên tục thử nghiệm, học hỏi và cải tiến (continuous learning).  
- Quyết định dựa trên **số liệu đo lường được**, không chỉ dựa vào cảm tính.  

Những lỗi phổ biến của người mới:

- Chỉ “đi theo tutorial” mà không tự làm dự án thực tế.  
- Quá so sánh bản thân với người khác thay vì tập trung vào **tiến bộ nhỏ nhưng đều đặn**.  

Thông điệp lặp lại nhiều lần:  
> *Không có CI/CD → không có DevOps.*  
> *Không IaC → không DevOps.*

---

##  Infrastructure as Code (IaC)

Các công cụ/approach được so sánh và phân tích:

- **CloudFormation**  
  - Dịch vụ gốc của AWS, mô hình khai báo (declarative).  
  - Phù hợp cho nhiều team enterprise, muốn sử dụng dịch vụ native.  

- **AWS CDK**  
  - Cho phép định nghĩa hạ tầng bằng ngôn ngữ lập trình (TypeScript, Python, Java,…).  
  - Mô hình: **Constructs → Stacks → Apps**.  
  - Dễ modular hóa, tái sử dụng, test, phù hợp Agile teams / developer-friendly.

- **Terraform**  
  - Phù hợp multi-cloud / hybrid.  
  - Quản lý state file, hỗ trợ nhiều provider.  

Các khái niệm được giải thích bằng ví dụ thực tế:

- Stack, Construct, State file, template YAML (Resources, Parameters, Outputs, Mappings)…  

**Thông điệp quan trọng:**

- Hạ tầng được định nghĩa bằng IaC sẽ **nhất quán, có version control, dễ review, dễ rollback** hơn rất nhiều so với cấu hình thủ công bằng click-ops.

---

##  AWS DevOps Services – CI/CD Pipeline

Nội dung xoay quanh cách xây dựng pipeline chuẩn AWS:

- **CI/CD với AWS:**
  - **CodePipeline** – orchestration cho toàn bộ pipeline.  
  - **CodeBuild** – build, test, lint, static analysis (buildspec.yml, build caching, parallel tests).  
  - **CodeDeploy** – triển khai ứng dụng (blue/green, canary, rolling).  

- **Demo pipeline end-to-end:**
  - Commit → Build → Test → Deploy → Monitor.  
  - Nhấn mạnh: **deployment phải tự động hóa 100%**, không “click deploy” thủ công trên console.

- **Chiến lược DevOps:**
  - Bắt đầu từ **small pipeline**, sau đó mở rộng dần.  
  - Dùng **blue/green** và **canary deployment** để giảm rủi ro.  
  - Kết hợp **IaC + GitOps** cho môi trường nhiều team.

---

##  Container và mô hình triển khai trên AWS

### Docker fundamentals

- **Dockerfile → Build → Image → Registry → Run container**  
- Registry: **Docker Hub** hoặc **Amazon ECR**

### Amazon ECR

- Lưu trữ container image.  
- Hỗ trợ **image scanning**, lifecycle policies, phân quyền theo repository.

### Amazon ECS

- Orchestrate container với **Fargate** hoặc **EC2**.  
- Tích hợp **Application Load Balancer**, autoscaling theo CPU, memory, queue length.  

### Amazon EKS

- **Managed Kubernetes service** trên AWS.  
- Phù hợp với **large-scale, multi-team**, yêu cầu portability, cần K8s ecosystem.

### AWS App Runner

- Dịch vụ “deploy container như deploy lên Vercel/Netlify” cho backend/web.  
- Phù hợp team muốn **giảm tối đa việc quản lý hạ tầng / cluster**.

**Case study & so sánh ECS, EKS, App Runner:**

- ECS: dễ dùng, native AWS, phù hợp đa số workload container trên AWS.  
- EKS: tối ưu khi đã dùng K8s hoặc cần multi-cloud portability.  
- App Runner: phù hợp team nhỏ, startup, feature team muốn tập trung vào code.

---

##  Monitoring & Observability

Phần này tập trung vào **CloudWatch** và **X-Ray**:

### Amazon CloudWatch

- Thu thập **Metrics, Logs, Dashboards**.  
- Composite alarms, log filters, custom metrics cho business KPIs.  

### AWS X-Ray

- **Distributed tracing**: vẽ service map, trace end-to-end request.  
- Rất hữu ích để debug **latency, bottlenecks** trong microservices.  

**Best practices:**

- Thiết kế alert hợp lý để tránh “alert noise”.  
- Xây dựng **on-call workflow và runbook** rõ ràng.  
- Dựa vào **Golden Signals**: Latency, Traffic, Errors, Saturation.  

Thông điệp được nhấn mạnh:  
> *Không observability = không biết hệ thống đang chết như thế nào.*

---

#  Những Gì Học Được

- DevOps **không chỉ là chức danh** mà là tư duy + tập hợp thói quen: automation, sharing, measurable outcomes.  
- **IaC** giúp hạ tầng:
  - Nhất quán  
  - Có thể lặp lại  
  - Dễ bảo trì, dễ audit, dễ rollback  
- Lựa chọn công cụ IaC (CloudFormation / CDK / Terraform) phải dựa trên:
  - Nhu cầu đội nhóm  
  - Yêu cầu dự án  
  - Mức độ phức tạp & môi trường (AWS-only hay multi-cloud).  
- Hiểu rõ sự khác biệt giữa các dịch vụ container (ECR, ECS, EKS, App Runner) giúp:
  - Chọn đúng dịch vụ cho đúng loại workload.  
- **Monitoring & Observability** không phải “add-on cuối cùng” mà phải được thiết kế **ngay từ đầu**.  
- Nắm thêm nhiều khái niệm như:
  - **DORA metrics**, CI → CD → Continuous Learning  
  - Blue/green, canary deployment  
  - GitOps, incident workflow, MTTR…

---

#  Ứng Dụng Vào Công Việc

### Ví dụ: Dự án Chatbot AI trên AWS

Nếu có cơ hội xây dựng một **Chatbot AI trên AWS**, tôi dự định áp dụng:

- **Thiết kế pipeline CI/CD:**
  - Dùng **CodePipeline + CodeBuild + CodeDeploy** để tự động hóa build, test, deploy.  
  - Mỗi lần commit code cho chatbot (backend, Lambda, API) đều được test và deploy tự động.  

- **Infrastructure as Code:**
  - Dùng **AWS CDK** để định nghĩa toàn bộ hạ tầng:  
    - Lambda, API Gateway, DynamoDB, S3, IAM, EventBridge,…  
  - Mọi thứ được version control trên Git, dễ tái sử dụng và mở rộng.

- **Container hóa & triển khai:**
  - Đóng gói một số service (ví dụ: RAG API, vector DB interface) thành Docker image.  
  - Deploy lên **ECS (Fargate)** hoặc **App Runner** tùy nhu cầu scale.

- **Monitoring & Incident handling:**
  - Dùng **CloudWatch metrics + logs + dashboards** để quan sát chatbot.  
  - Áp dụng **X-Ray** nếu kiến trúc là microservices.  
  - Thiết lập **incident workflow**: alert → investigate → fix → postmortem (runbook, on-call).

Nhờ áp dụng DevOps + AWS, hệ thống chatbot AI có thể:

- Phát triển nhanh hơn (dev velocity cao).  
- Triển khai thường xuyên nhưng vẫn an toàn.  
- Dễ bảo trì, dễ mở rộng khi lượng người dùng tăng.

---

#  Trải Nghiệm Sự Kiện

- Sự kiện giúp tôi có cái nhìn **thực tế hơn** về cách các tổ chức hiện đại triển khai DevOps trên AWS.  
- Các diễn giả không chỉ nói lý thuyết mà còn chia sẻ **rất nhiều ví dụ thật**, từ IaC, CI/CD đến container orchestration.  
- Được xem demo:
  - Pipeline từ **commit → deploy live**.  
  - **Drift detection**, `cdk synth/deploy`.  
  - Triển khai container real-time trên **ECS/ECR**.  
- Cơ hội **kết nối với các bạn cùng chí hướng**, trao đổi kinh nghiệm học DevOps, AWS, Cloud.  

### Bài học rút ra

- **Không có CI/CD → không có DevOps.**  
- **IaC là điều kiện tiên quyết** để automation thực sự hiệu quả.  
- **Containers = scalability + portability + speed**.  
- **Observability = reliability** – nếu không quan sát được, không thể tin hệ thống sẽ sống khỏe trong production.  

> Tổng kết lại, “AWS Cloud Mastery Series #2 – DevOps on AWS” không chỉ giúp tôi nắm vững khái niệm DevOps trên lý thuyết, mà còn định hình rõ hơn cách xây dựng hệ thống **tự động hóa – có thể mở rộng – dễ quan sát** trên AWS, từ đó tạo nền tảng vững chắc cho các dự án Cloud & DevOps trong tương lai.

## Một số hình ảnh khi tham gia sự kiện
![ws Image](/images/ws2.png)