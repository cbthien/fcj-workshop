---
title: "Week 7 Worklog"
date: "2025-10-20"
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Learn how to deploy and optimize AWS architecture for a real project.
* Review core AWS fundamentals.
* Experiment with deploying a Text-to-SQL chatbot and evaluate extension directions.
* Analyze database security and data-processing logic in the system.
* Strengthen the ability to reason about cost, reliability, and security when evolving an existing architecture.

---

### Tasks to carry out this week:

| Day | Tasks | Start date | Completion date | Reference Material |
| --- | ----- | ---------- | ---------------- | ------------------ |
| 2 | - Study how to downscale the project. <br> - Learn how to implement an architecture on AWS. <br> - Note a rare incident: **AWS outage in us-east-1**, affecting many systems. | 20/10/2025 | 20/10/2025 | Internal AWS reports, incident reports |
| 3 | - Review core AWS knowledge to prepare for assessments. | 21/10/2025 | 21/10/2025 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Redraw the overall architecture and estimate pricing for the project. <br> - Define the initial direction for the project chatbot. <br> - Direction document (Notion). | 22/10/2025 | 22/10/2025 | Draw.io |
| 5 | - Study **database security** and **safe data logic** to prevent invalid user operations (incorrect update/insert/delete). <br> - **Deploy the Text2SQL chatbot** following the AWS Blog guide. <br> - AWS Blog: *Build an AI-powered Text-to-SQL Chatbot*. | 23/10/2025 | 23/10/2025 | AWS Blog |
| 6 | - Read and understand the **Text2SQL chatbot source code**. <br> - Meeting notes on Notion. <br> - Team meeting: clarify how the chatbot interacts with the database, security measures, and **DB access restrictions**. <br> - Propose replacing **RAG with a DynamoDB cache** to reduce costs compared to OpenSearch. | 24/10/2025 | 24/10/2025 | Notion, AWS Blog |

---

### Week 7 Achievements

Week 7 marked a transition from basic hands-on practice to **working with a more realistic, production-oriented architecture**. Instead of only following tutorials, I had to think about how the system should scale, how much it costs, and how to keep it safe while integrating a Text2SQL chatbot.

* **Improved understanding of project downscaling and resource optimization**  
  At the beginning of the week, I focused on how to **downscale the existing project** to match realistic constraints (student environment, limited budget, and controlled workload).  
  * Reviewed which components truly needed to be running 24/7 and which could be scaled down or turned off when idle.  
  * Considered options like reducing instance sizes, using fewer AZs where acceptable, and removing non-essential test resources.  
  This helped me see that optimization is not always about “adding more services”, but often about **removing or simplifying** what is unnecessary.

* **Reinforced AWS architectural foundation through review and application**  
  I revisited **core AWS concepts** (networking, compute, storage, IAM, security, fault tolerance) not only to prepare for assessments but also to map them directly to the current project:  
  * Re-checked how VPC, subnets, security groups, and routing fit together in the existing design.  
  * Linked theory from the study material to concrete architectural decisions in the chatbot system.  
  This review made my understanding more solid and less “exam-style”; I could better explain why certain AWS services were chosen in the architecture.

* **Redesigned the overall architecture and produced a cost-aware version**  
  During the architecture redrawing task, I:  
  * Created a new version of the architecture diagram that reflected the **current project scope**, including the Text2SQL chatbot, database, and supporting components.  
  * Added cost-related thinking into the diagram (for example: which components incur steady monthly cost, which scale with usage, and where free tiers or serverless options could help).  
  * Documented the architecture and pricing assumptions in Notion so that the team can discuss and challenge them later.  
  This was an important step in moving from “lab architecture” to something that resembles a **real project design**.

* **Defined an initial direction for the Text2SQL chatbot**  
  I worked on clarifying how the chatbot should behave from both a **user experience** and **system design** perspective:  
  * Described the flow: from user question → model prompt → SQL generation → validation → execution → response formatting.  
  * Noted constraints such as maximum query complexity, timeout limits, and safety checks required before executing generated SQL.  
  * Wrote down open questions (e.g., how to log queries, how to monitor misuse, how to cap resource consumption).  
  This gave the project a clearer technical direction instead of just “we want a Text2SQL chatbot”.

* **Deployed the Text2SQL chatbot by following the AWS Blog guide**  
  I followed the official AWS Blog tutorial to **deploy the AI-powered Text-to-SQL chatbot**:  
  * Set up the necessary infrastructure components (API, Lambda functions, database access, and Bedrock integration where applicable).  
  * Deployed the sample solution and verified that user questions were translated into SQL queries and executed correctly against the database.  
  * Checked logs and traces to ensure that failures (invalid queries, timeouts, or syntax errors) were handled gracefully.  
  Successfully deploying the chatbot boosted my confidence in integrating AI components into cloud architectures.

* **Analyzed database security and safe data-processing logic**  
  To make sure the chatbot does not break the system or damage data, I:  
  * Studied **safe data logic** patterns to prevent dangerous operations such as unintended UPDATE/DELETE/INSERT without proper conditions.  
  * Considered using **read-only database roles** for Text2SQL queries, limiting modification capabilities.  
  * Thought about validation layers to inspect or restrict generated SQL before execution.  
  This helped me recognize that AI-driven systems need even stricter security and validation than traditional applications.

* **Read and understood the Text2SQL chatbot source code**  
  I went through the **source code** provided in the solution:  
  * Analyzed how prompts are constructed, how SQL is generated, and how responses are mapped back to user-friendly messages.  
  * Noted how the code handles error cases, logging, and integration with AWS services.  
  * Linked specific code modules to architecture components (e.g., which Lambda function is responsible for which part of the flow).  
  This gave me a deeper, implementation-level understanding instead of treating the solution as a “black box”.

* **Evaluated replacing RAG with a DynamoDB-based cache to reduce costs**  
  In the team meeting, we discussed the trade-offs between using **RAG with OpenSearch** and a **DynamoDB cache**:  
  * Identified that for certain types of queries, a structured data store + cache could be cheaper and simpler than a full vector search solution.  
  * Proposed using DynamoDB as a cache for frequent queries or preprocessed results to reduce both latency and OpenSearch costs.  
  * Considered the impact on flexibility: DynamoDB cache is less “free-form” than RAG, but sufficient for well-defined query patterns.  
  This taught me how to reason about **cost vs. flexibility** and not default to over-engineering with more advanced services than necessary.

* **Learned from a real AWS outage (us-east-1 incident)**  
  By noting the **AWS outage in us-east-1**, I:  
  * Reflected on how regional failures can impact many systems at once.  
  * Thought about how our architecture would behave in a similar scenario and what mitigation strategies (multi-AZ, multi-region, fallbacks) could be considered in the future.  
  This experience strengthened my awareness of **resilience and fault tolerance** beyond just single-region designs.

---

#### 1. Self-assessment

* **More confident discussing architecture and trade-offs**  
  I became more comfortable explaining why certain services are used, how they connect, and what trade-offs exist in terms of cost, performance, and complexity.

* **Better at linking code to architecture**  
  Reading the Text2SQL chatbot source code and mapping it to the diagram helped me understand how high-level design decisions translate into actual implementation.

* **Improved security awareness for AI-driven systems**  
  I now think more carefully about data access when LLMs or automated SQL generation are involved, instead of only checking whether “it works”.

#### 2. Challenges encountered

* **Balancing complexity vs. cost**  
  It was challenging to decide when advanced components (like RAG + OpenSearch) are justified and when a simpler pattern (like DynamoDB cache) is enough. This required more judgment than simply following best practices.

* **Reasoning about outages and resilience**  
  Thinking about rare incidents such as regional outages is not intuitive at first. I had to stretch my thinking to consider “what if this entire region is not available?” instead of only focusing on normal operation.

* **Understanding all details of the Text2SQL flow**  
  Some parts of the source code and the interaction between AI model, SQL generation, and database execution were complex. I needed time to trace the full request path and understand each step clearly.

---

Overall, Week 7 helped me move closer to the mindset of a **cloud engineer working on a real project**: not just deploying components, but also optimizing architecture, controlling costs, protecting data, and planning for failures while integrating AI capabilities into the system.
