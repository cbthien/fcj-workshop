---
title: "Week 11 Worklog"
date: "2025-11-17"
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

# WEEK 11 WORKLOG

## Week 11 Objectives

- Complete the **base infrastructure (M0)** including S3, DynamoDB, Cognito, ALB.  
- Begin implementing the **IDP Pipeline (M1)** — SQS, PDF Detection, PyPDF2 extraction.  
- Stabilize and optimize the previous **Analytics pipeline**: migrate from Glue Crawler to Athena DDL to reduce cost and simplify the architecture.  
- Standardize Lambda functions (AdminManager, Analytics Lambda) and ensure stable interactions with both Athena and RDS.  
- Optimize Cognito configuration to decouple backend logic from authentication.  
- Test the full end-to-end pipeline from **document upload → detection → extraction → DynamoDB → frontend**.

---

## Tasks to Implement This Week

| Day | Tasks | Start Date | Completion Date | Documentation |
| --- | ------ |------------|-----------------| -------------- |
| 2 | - Set up S3 bucket `arc-chatbot-documents-427995028618` <br> - Create DynamoDB tables (`metadata`, `chat-history`) <br> - Configure schema & indexes | 17/11/2025 | 17/11/2025      | https://docs.aws.amazon.com/dynamodb/ |
| 3 | - Configure Cognito User Pool `ap-southeast-1_8KB4JYvsX` <br> - Set up user authentication flow <br> - Test sign-up/sign-in process | 18/11/2025 | 18/11/2025      | https://docs.aws.amazon.com/cognito/ |
| 4 | - Set up ALB `arc-chatbot-dev-alb` with health checks <br> - Configure target groups & listeners <br> - Test routing | 19/11/2025 | 19/11/2025      | https://docs.aws.amazon.com/elasticloadbalancing/ |
| 5 | - Create SQS queue `arc-chatbot-dev-document-processing` <br> - Implement PDF detection (digital vs scanned) <br> - Write unit tests for PDF detector | 20/11/2025 | 20/11/2025      | https://docs.aws.amazon.com/sqs/ |
| 6 | - Implement PyPDF2 extraction for digital PDFs <br> - Handle edge cases (encrypted, corrupted) <br> - Write tests (30 tests passed) | 21/11/2025 | 21/11/2025      | https://pypdf2.readthedocs.io/ |

---

## Week 11 Achievements

### **1. Completed Base Infrastructure (M0)**  
- S3 bucket `arc-chatbot-documents-427995028618` created for document storage.  
- DynamoDB tables:  
  - `metadata`: stores document metadata  
  - `chat-history`: stores conversation logs  
- Cognito User Pool `ap-southeast-1_8KB4JYvsX` — used for authentication & authorization.  
- ALB `arc-chatbot-dev-alb` — handles API traffic routing with health checks.

### **2. Initiated & Optimized the IDP Pipeline (M1)**  
- SQS Queue `arc-chatbot-dev-document-processing` created for document processing flows.  
- PDF Detector service implemented: detects digital vs scanned PDFs (17 tests passed).  
- PDF Extractor (PyPDF2): extracts text from digital PDFs (30 tests passed).  
- Added handling for problematic PDFs: encrypted, corrupted, unsupported.

### **3. Stabilized & Improved the Analytics Pipeline (from previous week)**  
- Removed Glue Crawler → migrated to Athena DDL for better schema control.  
- Deleted Glue DB and Glue endpoint → reduced cost & simplified architecture.  
- Refactored Analytics Lambda to run outside VPC for Athena queries.  
- AdminManager Lambda now focuses solely on inserting data into RDS → simpler architecture.  
- Improved Cognito configuration to ensure the backend is no longer dependent on the DB.

### **4. Frontend & Authentication Progress**  
- Successfully deployed login page on CloudFront.  
- Completed `admin_handler` logic to allow stable data insertion into RDS through the frontend.  

---

## Lessons Learned

- Designing DynamoDB schema for a RAG/Chatbot system.  
- Understanding Cognito authentication flow, JWT tokens, and User Pool mechanics.  
- SQS message processing patterns & building an IDP pipeline.  
- Techniques for reading PDFs with PyPDF2 and handling various error cases.  
- Athena DDL architecture, differences from Glue Crawler, cost/performance best practices.  
- Optimizing Lambda for a serverless data-processing pipeline.

---

## Summary

Week 11 successfully achieved key objectives: **completed M0**, **initiated M1**, stabilized the analytics pipeline, and standardized Lambda and Cognito authentication flows. These improvements establish a strong foundation for continuing the RAG pipeline and expanding document-processing modules in the following weeks.
