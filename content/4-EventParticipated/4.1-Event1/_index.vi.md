---
title: "Event 1"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 4.1 </b> "
---

## Bài thu hoạch “AWS Cloud Mastery Series #1 – AI/ML/GenAI trên AWS”

---

##  Mục Đích Của Sự Kiện

- Giới thiệu hệ sinh thái **AI/ML/GenAI trên AWS** và cách áp dụng trong các bài toán thực tế.  
- Hướng dẫn triển khai **ML end-to-end bằng Amazon SageMaker**.  
- Xây dựng ứng dụng **Generative AI** thông qua Amazon Bedrock, RAG, Agents, AgentCore.  
- Làm quen với **MLOps, IaC, CICD, container workflows** phục vụ AI/ML.  
- Xây dựng tư duy vận hành và thiết kế **kiến trúc AI trong môi trường doanh nghiệp**.

---

##  Danh Sách Diễn Giả

- **Lâm Tuấn Kiệt** – Sr DevOps Engineer, FPT Software  
- **Danh Hoàng Hiếu Nghị** – AI Engineer, Renova Cloud  
- **Đinh Lê Hoàng Anh** – Cloud Engineer Trainee, First Cloud AI Journey  
- **Văn Hoàng Kha** – Community Builder  

---

#  Nội Dung Nổi Bật

##  AWS AI/ML Services Overview

###  Amazon SageMaker — nền tảng ML end-to-end

**Data preparation:**
- **SageMaker Data Wrangler**  
- **Ground Truth** (data labeling)  
- **Feature Store** (quản lý feature tái sử dụng)

**Training & Tuning:**
- Training jobs với autoscaling GPU/CPU  
- Hỗ trợ distributed training  
- Hyperparameter tuning (Auto-tuning, Bayesian Optimization)

**Deployment Options:**
- Real-time endpoint  
- Serverless inference  
- Multi-model endpoint  
- Asynchronous (async) inference  

**MLOps:**
- Model registry  
- CI/CD pipelines bằng **SageMaker Pipelines**  
- Monitoring drift: data drift, feature drift, model drift  

**Live demo:**
- Trải nghiệm **SageMaker Studio**: notebook, xử lý dữ liệu, training và deploy model.

---

##  Generative AI với Amazon Bedrock

###  Foundation Models (FMs)

AWS cung cấp thư viện mô hình nền tảng được quản lý hoàn toàn từ nhiều nhà cung cấp hàng đầu (Anthropic, Meta, Amazon, v.v.):

- **Claude 3.5** – reasoning mạnh, context dài, phù hợp coding.  
- **Llama 3** – open-weight, dễ fine-tuning, chi phí tối ưu.  
- **Titan** – embedding chất lượng cao cho RAG.  
- **Mistral** – nhanh, nhẹ, phù hợp ứng dụng realtime.  

→ Giúp người dùng tùy chỉnh và tích hợp nhanh mà **không cần tự huấn luyện mô hình từ đầu**.

###  Prompt Engineering Techniques

Hiểu cách “hướng dẫn” mô hình qua nhiều chiến lược prompt:

- **Zero-shot** – mô hình chỉ nhận mô tả nhiệm vụ.  
- **Few-shot** – mô hình được cung cấp một vài ví dụ mẫu.  
- **Chain-of-Thought** – yêu cầu trình bày từng bước suy luận để tăng độ chính xác.  
- **Role prompting** – gán vai trò cụ thể cho mô hình.  
- **Multi-step reasoning** & **Prompt templates** – chia nhỏ suy luận, chuẩn hóa format.

###  Retrieval Augmented Generation (RAG)

Tăng chất lượng câu trả lời bằng cách bổ sung kiến thức bên ngoài:

- **R – Retrieval:** truy xuất thông tin liên quan từ knowledge base / data store.  
- **A – Augmentation:** đưa thông tin truy xuất vào prompt làm ngữ cảnh.  
- **G – Generation:** mô hình tạo câu trả lời **chính xác và có căn cứ hơn**.

**Use cases:**
- Chatbot doanh nghiệp theo ngữ cảnh  
- Tìm kiếm thông minh (contextual / semantic search)  
- Tóm tắt tài liệu, log, dữ liệu thời gian thực

###  Amazon Titan Embeddings

- Mô hình embedding nhẹ, chuyển văn bản thành vector dense.  
- Dùng trong similarity search, semantic search và RAG workflows.  
- Hỗ trợ đa ngôn ngữ, tối ưu cho các bài toán tri thức doanh nghiệp.

###  AWS AI Services – Dịch vụ AI dựng sẵn

- **Rekognition** – phân tích hình ảnh/video  
- **Translate** – dịch ngôn ngữ  
- **Textract** – trích xuất văn bản & layout từ tài liệu  
- **Transcribe** – chuyển giọng nói thành văn bản  
- **Polly** – chuyển văn bản thành giọng nói  
- **Comprehend** – phân tích ngôn ngữ tự nhiên  
- **Kendra** – tìm kiếm doanh nghiệp thông minh  
- **Lookout** – phát hiện bất thường  
- **Personalize** – gợi ý cá nhân hóa  

**Demo nổi bật:**  
Ứng dụng nhận diện khuôn mặt **AMZPhoto**, minh họa việc tích hợp AI/ML vào sản phẩm thực tế trên AWS.

---

##  Bedrock Agents & AgentCore

###  Bedrock Agents

- Agents có thể tự thực thi **multi-step workflows**.  
- Kích hoạt **Lambda** để gọi API, database và các workflow bên ngoài.  
- Có thể thay thế một phần **backend business logic** trong nhiều use case.  
- Kết hợp chặt chẽ với **EventBridge** và **Step Functions** trong pipeline AI để **orchestrate** và **retry**.

###  Amazon Bedrock AgentCore

Framework mới hỗ trợ xây dựng **AI Agents sẵn sàng cho môi trường production**:

- Thực thi và mở rộng workflows của agent một cách an toàn.  
- Quản lý **bộ nhớ dài hạn (long-term memory)**.  
- Thiết lập **identity & access control** chi tiết.  
- Tích hợp với các công cụ như **Browser Tool**, **Code Interpreter**, **Memory Store**.  
- Cung cấp khả năng **observability & auditing**.  
- Hỗ trợ nhiều agent framework phổ biến: **CrewAI**, **LangGraph**, **LlamaIndex**, **OpenAI Agents SDK**, v.v.

---

##  CICD Workflow cho Containers (ECR + ECS)

Quy trình chuẩn AWS DevSecOps cho AI/ML containers:

1. Developer commit code → **CodeCommit**  
2. **CodeBuild** build image + chạy tests  
3. Push image lên **ECR**  
4. **ECS** pull image để deploy (Fargate / EC2)  
5. **CloudWatch** giám sát logs & metrics  
6. **CodePipeline** orchestrate toàn bộ quy trình  

**DevSecOps (bảo mật trong pipeline):**

- Validation trong **CodeBuild** (unit tests, static analysis)  
- Image scanning trong **ECR** (vulnerability scan)  
- Deployment policies / IAM controls để kiểm soát việc deploy  

→ Đây là **DevSecOps chuẩn AWS**.

---

#  Những Gì Học Được

##  Kiến Thức AI/ML Nền Tảng & GenAI

- Hiểu rõ **ML lifecycle**.  
- Nắm được **feature engineering**, model deployment & monitoring.  
- Biết cách tối ưu **chi phí training/inference**.  
- Cách chọn **Foundation Model** phù hợp với từng use case.  
- Kỹ thuật **prompt engineering nâng cao** (CoT, role, multi-step, RAG-aware prompting).  
- Thiết kế **RAG architecture** theo chuẩn production.  
- Xây dựng **Agents** để tự động thực thi workflows phức tạp.  

##  Kiến Trúc Kỹ Thuật Quan Trọng

- **IaC (Infrastructure as Code):** Terraform vs CloudFormation vs CDK.  
- **Container inference workflow:** ECS / ECR cho AI inference container.  
- **Monitoring & Observability:** giám sát AI workloads bằng CloudWatch + X-Ray.  

---

#  Ứng Dụng Vào Công Việc

- Build **chatbot doanh nghiệp** với Bedrock + RAG (retrieval-augmented generation).  
- Thiết kế kiến trúc AI end-to-end (data → ML → app).  
- Dùng **Lambda + Step Functions** để điều phối RAG pipeline.  
- Dùng **Terraform / CDK** để xây dựng hạ tầng GenAI chuẩn enterprise.  
- Triển khai inference containers qua **ECS / Fargate**.  
- Áp dụng kiến thức về **AgentCore** và Agents cho các dự án GenAI nội bộ trong tương lai.

---

#  Trải Nghiệm Trong Event

- Tham gia workshop **“AWS Cloud Mastery Series #1”** giúp tôi thấy rõ cách AWS triển khai AI/ML thực tế, hiểu sự khác nhau giữa **ML truyền thống và GenAI**, và nâng cao tư duy thiết kế **AI architecture**.  
- Học hỏi từ các diễn giả có chuyên môn cao, hiểu chi tiết cách AWS xây dựng hệ sinh thái **AI/ML/GenAI** toàn diện.  
- Thực hành sử dụng các công cụ hiện đại:
  - **SageMaker**: từ chuẩn bị dữ liệu → training → tuning → deployment → MLOps.  
  - **Bedrock**: dùng Claude, Llama, Titan, RAG + Agents để xây chatbot và workflow AI nhanh.  
  - **IaC & DevOps**: CloudFormation, CDK, Terraform, CodePipeline để triển khai AI/ML có kiểm soát và tự động.  
  - **Data & ETL Tools**: Glue, S3 (Data Lake), EventBridge, Step Functions cho data pipeline.  
  - **Monitoring**: CloudWatch cho logging & drift detection.  

- Về networking và tư duy:
  - Học cách suy nghĩ theo hướng **AI system** thay vì chỉ tập trung vào một mô hình ML.  
  - Nắm bắt xu hướng AI/ML tại Việt Nam và cách doanh nghiệp đang ứng dụng.

### Bài học rút ra

- **GenAI và ML truyền thống** kết hợp để tạo nên các giải pháp AI mạnh trong thực tế.  
- **Bedrock** là nền tảng GenAI doanh nghiệp: an toàn, triển khai nhanh, không cần tự train model.  
- **MLOps + IaC** là bắt buộc để hệ thống AI chạy ổn định trong production.  
- **RAG** là cách hiệu quả nhất để “đưa kiến thức doanh nghiệp vào mô hình”.

---

> Tổng thể, sự kiện không chỉ mang lại kiến thức kỹ thuật mà còn giúp tôi xây dựng tư duy kiến trúc hệ thống AI/ML hoàn chỉnh, từ dữ liệu → mô hình → triển khai → vận hành, tạo nền tảng vững chắc cho các dự án AI/GenAI thực tế trong tương lai.

## Một số hình ảnh khi tham gia sự kiện
![ws Image](/images/ws1.png)