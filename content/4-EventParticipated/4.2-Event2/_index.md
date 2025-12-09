---
title: "Event 2"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 4.2 </b> "
---

# Reflection Report: “AWS Cloud Mastery Series #2 – DevOps on AWS”

---

##  Event Objectives

- Introduce **DevOps services on AWS** and how to design a **CI/CD pipeline**.  
- Equip participants with a **modern DevOps mindset** and how to apply it in the AWS ecosystem.  
- Explore concepts of **Infrastructure as Code (IaC)** and related tools (CloudFormation, CDK, Terraform).  
- Provide an overview of **container-based workloads** on AWS (ECR, ECS, EKS, App Runner).  
- Demonstrate how to achieve effective **monitoring & observability** using native AWS services.  
- Optimize **development speed, release quality, and system reliability**.

---

##  Speakers

- **Truong Quang Tinh** – AWS Community Builder, Platform Engineer (TymeX)  
- **Bao Huynh** – AWS Community Builder  
- **Nguyen Khanh Phuc Thinh** – AWS Community Builder  
- **Tran Dai Vi** – AWS Community Builder  
- **Huynh Hoang Long** – AWS Community Builder  
- **Pham Hoang Quy** – AWS Community Builder  
- **Nghiem Le** – AWS Community Builder  
- **Dinh Le Hoang Anh** – Cloud Engineer Trainee, First Cloud AI Journey  

(Together with members from the **FCJ Team**, **AWS Developer Advocate Team**, and community guests.)

---

#  Key Highlights

##  Building a DevOps Mindset Foundation

The speakers emphasized that **DevOps is not just a job title** but a **mindset + set of working habits**:

- Automating repetitive tasks.  
- Sharing knowledge across roles (Dev, Ops, QA, Security…).  
- Continuously experimenting, learning, and improving (continuous learning).  
- Making decisions based on **measurable data**, not just gut feeling.  

Common mistakes for beginners:

- Only “following tutorials” without building real-world projects.  
- Comparing themselves too much with others instead of focusing on **small but consistent progress**.  

Key messages repeated throughout the session:  
> *No CI/CD → No DevOps.*  
> *No IaC → No DevOps.*

---

##  Infrastructure as Code (IaC)

The tools/approaches were compared and analyzed:

- **CloudFormation**  
  - Native AWS service, declarative model.  
  - Suitable for many enterprise teams wanting to stay fully AWS-native.  

- **AWS CDK**  
  - Define infrastructure using programming languages (TypeScript, Python, Java, …).  
  - Model: **Constructs → Stacks → Apps**.  
  - Easy to modularize, reuse, and test; very developer-friendly and fits Agile teams.

- **Terraform**  
  - Suitable for multi-cloud / hybrid scenarios.  
  - Manages state files and supports many providers.  

Concepts were explained through practical examples:

- Stack, Construct, State file, YAML template structure (Resources, Parameters, Outputs, Mappings)…  

**Important message:**

- Infrastructure defined as IaC becomes **consistent, version-controlled, easy to review, and easy to roll back**, much better than manual click-ops in the console.

---

##  AWS DevOps Services – CI/CD Pipeline

The content focused on building an AWS-standard pipeline:

- **CI/CD on AWS:**
  - **CodePipeline** – orchestrates the entire pipeline.  
  - **CodeBuild** – builds, tests, linting, static analysis (buildspec.yml, build caching, parallel tests).  
  - **CodeDeploy** – deploys applications (blue/green, canary, rolling).  

- **End-to-end pipeline demo:**
  - Commit → Build → Test → Deploy → Monitor.  
  - Emphasis: **deployment must be 100% automated**, no manual “click deploy” in the console.

- **DevOps strategy:**
  - Start with a **small pipeline**, then expand gradually.  
  - Use **blue/green** and **canary deployments** to reduce risk.  
  - Combine **IaC + GitOps** for multi-team environments.

---

##  Containers and Deployment Models on AWS

### Docker fundamentals

- **Dockerfile → Build → Image → Registry → Run container**  
- Registries: **Docker Hub** or **Amazon ECR**

### Amazon ECR

- Stores container images.  
- Supports **image scanning**, lifecycle policies, and per-repository permissions.

### Amazon ECS

- Orchestrates containers with **Fargate** or **EC2**.  
- Integrates with **Application Load Balancer**, autoscaling based on CPU, memory, and queue length.  

### Amazon EKS

- **Managed Kubernetes service** on AWS.  
- Suitable for **large-scale, multi-team** environments requiring portability and the full Kubernetes ecosystem.

### AWS App Runner

- A service to “deploy containers like deploying to Vercel/Netlify” for backend/web applications.  
- Suitable for teams that want to **minimize infrastructure/cluster management**.

**Case study & comparison of ECS, EKS, App Runner:**

- ECS: easy to use, AWS-native, suitable for most container workloads on AWS.  
- EKS: ideal when already using Kubernetes or requiring multi-cloud portability.  
- App Runner: great for small teams, startups, and feature teams who want to focus on code.

---

##  Monitoring & Observability

This part focused on **CloudWatch** and **X-Ray**:

### Amazon CloudWatch

- Collects **Metrics, Logs, Dashboards**.  
- Supports composite alarms, log filters, and custom metrics for business KPIs.  

### AWS X-Ray

- **Distributed tracing**: draws service maps and traces end-to-end requests.  
- Very useful for debugging **latency and bottlenecks** in microservices.  

**Best practices:**

- Design alerts carefully to avoid “alert noise”.  
- Build clear **on-call workflows and runbooks**.  
- Monitor using the **Golden Signals**: Latency, Traffic, Errors, Saturation.  

Highlighted message:  
> *No observability = no idea how your system is dying.*

---

#  Key Learnings

- DevOps **is not just a job title**; it’s a mindset and a set of habits: automation, sharing, and measurable outcomes.  
- **IaC** helps infrastructure become:
  - Consistent  
  - Repeatable  
  - Easy to maintain, audit, and roll back  
- Choosing IaC tools (CloudFormation / CDK / Terraform) should be based on:
  - Team requirements  
  - Project needs  
  - Complexity and environment (AWS-only vs multi-cloud).  
- Understanding the differences between container services (ECR, ECS, EKS, App Runner) helps:
  - Pick the right service for the right workload.  
- **Monitoring & Observability** are not “add-ons at the end” but must be designed **from day one**.  
- Gained more familiarity with concepts such as:
  - **DORA metrics**, CI → CD → Continuous Learning  
  - Blue/green and canary deployments  
  - GitOps, incident workflows, MTTR…

---

#  Applying to Work

### Example: AI Chatbot Project on AWS

If I have the opportunity to build an **AI Chatbot on AWS**, I plan to apply:

- **CI/CD pipeline design:**
  - Use **CodePipeline + CodeBuild + CodeDeploy** to automate build, test, and deployment.  
  - Every commit to the chatbot code (backend, Lambda, API) will be tested and deployed automatically.  

- **Infrastructure as Code:**
  - Use **AWS CDK** to define the entire infrastructure:  
    - Lambda, API Gateway, DynamoDB, S3, IAM, EventBridge, …  
  - Everything is version-controlled in Git, making it easy to reuse and scale.

- **Containerization & deployment:**
  - Package some services (e.g., RAG API, vector DB interface) into Docker images.  
  - Deploy to **ECS (Fargate)** or **App Runner**, depending on scaling needs.

- **Monitoring & Incident handling:**
  - Use **CloudWatch metrics + logs + dashboards** to monitor the chatbot.  
  - Apply **X-Ray** if the architecture is microservices-based.  
  - Set up an **incident workflow**: alert → investigate → fix → postmortem (runbook, on-call).

By applying DevOps practices and AWS services, an AI chatbot system can:

- Develop faster (higher dev velocity).  
- Deploy frequently while staying safe.  
- Be easier to maintain and scale as user traffic grows.

---

#  Event Experience

- The event gave me a **more realistic view** of how modern organizations implement DevOps on AWS.  
- The speakers not only covered theory but also shared **plenty of real-world examples**, from IaC and CI/CD to container orchestration.  
- I got to see demos of:
  - A pipeline from **commit → live deployment**.  
  - **Drift detection**, `cdk synth/deploy`.  
  - Real-time container deployments on **ECS/ECR**.  
- It was also a great opportunity to **connect with like-minded peers**, exchange DevOps, AWS, and Cloud learning experiences.  

### Takeaways

- **No CI/CD → No DevOps.**  
- **IaC is a prerequisite** for effective automation.  
- **Containers = scalability + portability + speed**.  
- **Observability = reliability** – if you can’t observe it, you can’t trust it to stay healthy in production.  

> In summary, “AWS Cloud Mastery Series #2 – DevOps on AWS” not only helped me solidify DevOps concepts in theory, but also clarified how to build **automated, scalable, and observable** systems on AWS, forming a strong foundation for future Cloud & DevOps projects.
## Some photos from the event
![ws Image](/images/ws2.png)