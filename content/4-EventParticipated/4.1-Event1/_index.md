---
title: "Event 1"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 4.1 </b> "
---

# Reflection Report “AWS Cloud Mastery Series #1 – AI/ML/GenAI on AWS”

---

##  Event Objectives

- Introduce the **AI/ML/GenAI ecosystem on AWS** and how it can be applied to real-world use cases.  
- Guide participants through **end-to-end ML deployment with Amazon SageMaker**.  
- Build **Generative AI applications** using Amazon Bedrock, RAG, Agents, and AgentCore.  
- Get familiar with **MLOps, IaC, CICD, and container workflows** for AI/ML workloads.  
- Develop operational thinking and **AI architecture design** in enterprise environments.

---

##  Speakers

- **Lam Tuan Kiet** – Sr DevOps Engineer, FPT Software  
- **Danh Hoang Hieu Nghi** – AI Engineer, Renova Cloud  
- **Dinh Le Hoang Anh** – Cloud Engineer Trainee, First Cloud AI Journey  
- **Van Hoang Kha** – Community Builder  

---

#  Key Highlights

##  AWS AI/ML Services Overview

###  Amazon SageMaker — end-to-end ML platform

**Data preparation:**
- **SageMaker Data Wrangler**  
- **Ground Truth** (data labeling)  
- **Feature Store** (managing reusable features)

**Training & Tuning:**
- Training jobs with GPU/CPU autoscaling  
- Supports distributed training  
- Hyperparameter tuning (Auto-tuning, Bayesian Optimization)

**Deployment Options:**
- Real-time endpoint  
- Serverless inference  
- Multi-model endpoint  
- Asynchronous (async) inference  

**MLOps:**
- Model registry  
- CI/CD pipelines with **SageMaker Pipelines**  
- Monitoring drift: data drift, feature drift, model drift  

**Live demo:**
- Hands-on with **SageMaker Studio**: notebooks, data processing, training, and model deployment.

---

##  Generative AI with Amazon Bedrock

###  Foundation Models (FMs)

AWS provides a fully managed library of foundation models from leading providers (Anthropic, Meta, Amazon, etc.):

- **Claude 3.5** – strong reasoning, long context, great for coding.  
- **Llama 3** – open-weight, easy to fine-tune, cost-effective.  
- **Titan** – high-quality embeddings for RAG.  
- **Mistral** – fast, lightweight, suitable for realtime applications.  

→ Enables quick customization and integration **without having to train models from scratch**.

###  Prompt Engineering Techniques

Understanding how to “guide” the model through various prompting strategies:

- **Zero-shot** – the model only receives the task description.  
- **Few-shot** – the model is given a few example inputs/outputs.  
- **Chain-of-Thought** – ask the model to show step-by-step reasoning for higher accuracy.  
- **Role prompting** – assign a specific role to the model.  
- **Multi-step reasoning** & **Prompt templates** – break down reasoning and standardize format.

###  Retrieval Augmented Generation (RAG)

Improving answer quality by injecting external knowledge:

- **R – Retrieval:** fetch relevant information from a knowledge base / data store.  
- **A – Augmentation:** include the retrieved information in the prompt as context.  
- **G – Generation:** the model produces answers that are **more accurate and well-grounded**.

**Use cases:**
- Context-aware enterprise chatbots  
- Intelligent search (contextual / semantic search)  
- Summarizing documents, logs, and real-time data

###  Amazon Titan Embeddings

- Lightweight embedding model that converts text into dense vectors.  
- Used for similarity search, semantic search, and RAG workflows.  
- Multilingual support, optimized for enterprise knowledge use cases.

###  AWS AI Services – Pre-built AI APIs

- **Rekognition** – image/video analysis  
- **Translate** – language translation  
- **Textract** – extract text & layout from documents  
- **Transcribe** – speech-to-text  
- **Polly** – text-to-speech  
- **Comprehend** – natural language processing  
- **Kendra** – intelligent enterprise search  
- **Lookout** – anomaly detection  
- **Personalize** – personalized recommendations  

**Highlight demo:**  
The **AMZPhoto** face recognition app, showcasing how to integrate AI/ML into real-world products on AWS.

---

##  Bedrock Agents & AgentCore

###  Bedrock Agents

- Agents can autonomously execute **multi-step workflows**.  
- Trigger **Lambda** to call APIs, databases, and external workflows.  
- Can replace parts of **backend business logic** in many use cases.  
- Integrates tightly with **EventBridge** and **Step Functions** for **orchestration** and **retry** within AI pipelines.

###  Amazon Bedrock AgentCore

A new framework for building **production-ready AI Agents**:

- Execute and scale agent workflows securely.  
- Manage **long-term memory**.  
- Provide detailed **identity & access control**.  
- Integrate with tools such as **Browser Tool**, **Code Interpreter**, **Memory Store**.  
- Provide **observability & auditing** capabilities.  
- Support many popular agent frameworks: **CrewAI**, **LangGraph**, **LlamaIndex**, **OpenAI Agents SDK**, etc.

---

##  CICD Workflow for Containers (ECR + ECS)

A standard AWS DevSecOps pipeline for AI/ML containers:

1. Developer commits code → **CodeCommit**  
2. **CodeBuild** builds the image and runs tests  
3. Push image to **ECR**  
4. **ECS** pulls the image to deploy (Fargate / EC2)  
5. **CloudWatch** monitors logs & metrics  
6. **CodePipeline** orchestrates the entire process  

**DevSecOps (security in the pipeline):**

- Validation in **CodeBuild** (unit tests, static analysis)  
- Image scanning in **ECR** (vulnerability scan)  
- Deployment policies / IAM controls to manage deployment  

→ This represents **AWS-standard DevSecOps**.

---

#  What I Learned

##  Core AI/ML & GenAI Knowledge

- A clear view of the **ML lifecycle**.  
- Understanding of **feature engineering**, model deployment & monitoring.  
- How to optimize **training/inference costs**.  
- How to choose the right **Foundation Model** for each use case.  
- **Advanced prompt engineering** techniques (CoT, role, multi-step, RAG-aware prompting).  
- How to design **RAG architectures** that are production-ready.  
- How to build **Agents** that can automatically execute complex workflows.  

##  Key Technical Architecture

- **IaC (Infrastructure as Code):** Terraform vs CloudFormation vs CDK.  
- **Container inference workflow:** ECS / ECR for AI inference containers.  
- **Monitoring & Observability:** monitoring AI workloads with CloudWatch + X-Ray.  

---

#  Applying to Work

- Build **enterprise chatbots** with Bedrock + RAG (retrieval-augmented generation).  
- Design end-to-end AI architectures (data → ML → app).  
- Use **Lambda + Step Functions** to orchestrate RAG pipelines.  
- Use **Terraform / CDK** to build enterprise-grade GenAI infrastructure.  
- Deploy inference containers using **ECS / Fargate**.  
- Apply knowledge of **AgentCore** and Agents to future internal GenAI projects.

---

#  Event Experience

- Attending the **“AWS Cloud Mastery Series #1”** workshop helped me clearly see how AWS deploys AI/ML in real-world scenarios, understand the differences between **traditional ML and GenAI**, and improve my **AI architecture design** mindset.  
- I learned from highly experienced speakers and gained a detailed understanding of how AWS builds a comprehensive **AI/ML/GenAI** ecosystem.  
- Hands-on with modern tools:
  - **SageMaker**: from data preparation → training → tuning → deployment → MLOps.  
  - **Bedrock**: using Claude, Llama, Titan, RAG + Agents to quickly build chatbots and AI workflows.  
  - **IaC & DevOps**: CloudFormation, CDK, Terraform, CodePipeline for controlled and automated AI/ML deployments.  
  - **Data & ETL Tools**: Glue, S3 (Data Lake), EventBridge, Step Functions for data pipelines.  
  - **Monitoring**: CloudWatch for logging & drift detection.  

- On networking and mindset:
  - Learned to think in terms of **AI systems**, not just standalone ML models.  
  - Gained insights into AI/ML trends in Vietnam and how enterprises are adopting them.

### Key Lessons

- **GenAI and traditional ML** complement each other to create powerful real-world AI solutions.  
- **Bedrock** is an enterprise-grade GenAI platform: secure, fast to deploy, no need to train models from scratch.  
- **MLOps + IaC** are essential for keeping AI systems stable in production.  
- **RAG** is one of the most effective ways to “bring enterprise knowledge into the model”.

---

> Overall, the event not only provided technical knowledge but also helped me build a complete AI/ML system design mindset, from data → model → deployment → operations, forming a solid foundation for future real-world AI/GenAI projects.

## Some photos from the event
![ws Image](/images/ws1.png)
