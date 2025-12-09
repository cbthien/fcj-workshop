---
title: "Event 3"
date: "`r Sys.Date()`"
weight: 3
chapter: false
pre: " <b> 4.3 </b> "
---

# Reflection Report: “AWS Cloud Mastery Series #3 – AWS Well-Architected Security Pillar Workshop”

---

##  Event Objectives

- Share and reinforce core knowledge in the **AWS Well-Architected Framework – Security Pillar**.  
- Equip a mindset and skills to build systems that are **secure, resilient, and compliant with AWS best practices**.  
- Dive into the 5 key security pillars:

  1. **Identity & Access Management (IAM)**  
  2. **Detection & Continuous Monitoring**  
  3. **Infrastructure Protection**  
  4. **Data Protection**  
  5. **Incident Response**

- Introduce the **AWS Cloud Clubs** initiative and community activities that support students learning cloud at universities.

---

##  Speakers

- **Le Vu Xuan An** – AWS Cloud Club Captain HCMUTE  
- **Tran Duc Anh** – AWS Cloud Club Captain SGU  
- **Tran Doan Cong Ly** – AWS Cloud Club Captain PTIT  
- **Danh Hoang Hieu Nghi** – AWS Cloud Club Captain HUFLIT  
- **Huynh Hoang Long** – AWS Community Builder  
- **Dinh Le Hoang Anh** – AWS Community Builder / Cloud Engineer Trainee  
- **Nguyen Tuan Thinh** – Cloud Engineer Trainee  
- **Nguyen Do Thanh Dat** – Cloud Engineer Trainee  
- **Van Hoang Kha** – Cloud Security Engineer, AWS Community Builder  
- **Thinh Lam** – FCJ Member  
- **Viet Nguyen** – FCJ Member  
- **Mendel Grabski (Long)** – Ex-Head of Security & DevOps, Cloud Security Solution Architect  
- **Trinh Truong** – Platform Engineer at TymeX, AWS Community Builder  

(Together with members from the **FCJ Team** and the AWS community.)

---

#  Key Highlights

##  Introduction to AWS Cloud Club & Security Foundation

The event started with:

- An introduction to **AWS Cloud Club**:
  - A platform that helps students develop cloud skills through **real-world scenarios**.  
  - Opportunities to receive **mentorship** from AWS experts and the community.  
  - Community building and networking among students from universities such as HCMUTE, SGU, PTIT, HUFLIT…

- **Security Foundation – Core AWS Security Concepts**:
  - **Least Privilege – Zero Trust – Defense in Depth**: three foundational principles for modern security systems.  
  - **Shared Responsibility Model**:
    - AWS secures **the cloud**.  
    - Customers secure **what runs in the cloud**.

- **Top Cloud Threats in Vietnam**:
  - Public S3 / databases / Redis  
  - Exposed access keys  
  - Misconfigured IAM  
  - EC2 compromised with malware (crypto mining)  
  - Lack of logging or GuardDuty not enabled  

Key message: **Security = culture, not a feature** – security is a culture, not just an add-on feature.

---

##  Pillar 1 – Identity & Access Management (IAM)

IAM is the core of the Security Pillar:

- Apply **Least Privilege** aggressively.  
- Remove **root access keys** after initial setup.  
- Avoid using **wildcard permissions (`*`)**.  

### Modern IAM Practices

- **IAM Users**: almost no longer recommended → prioritize:
  - **Roles > Users**  
  - **SSO > Local credentials**  
  - **OIDC > Access Keys**  

- **IAM Identity Center (SSO)**:
  - Manage users and permissions in a **multi-account environment**.  

- **Organizational controls**:
  - Use **SCP (Service Control Policies)** to limit permissions at the organization level.  
  - Use **Permission Boundaries** to restrict the maximum scope of what a user/role can do.

- **Authentication & monitoring**:
  - Enforce **credential rotation** & **MFA**.  
  - Use **IAM Access Analyzer** to detect overly permissive, public, or unintended sharing policies.  
  - Compare MFA options **TOTP** vs **FIDO2** in terms of security and recovery.

- **Secrets Management**:
  - Use **AWS Secrets Manager** with the rotation lifecycle:  
    `create → set → test → finalize`  
  - Do not hard-code secrets in code / environment variables.

---

##  Pillar 2 – Detection & Continuous Monitoring

### Multi-layer Observability

- **CloudTrail**:
  - Management Events: API calls, configuration changes.  
  - Data Events: detailed activity on S3 objects, Lambda executions.  
  - Deploy **organization-level CloudTrail** across all accounts.

- **Logging sources**:
  - **VPC Flow Logs**, **S3 access logs**, **ALB logs** to trace network and access patterns.

- **Amazon GuardDuty**:
  - A continuous threat detection service that analyzes:
    - CloudTrail events  
    - VPC Flow Logs  
    - DNS queries  
  - Detects:
    - Logging being disabled  
    - Suspicious or abnormal traffic  
    - Access to malicious domains  
    - Malware scanning on S3  
    - EKS audit logs  
    - RDS anomaly detection  
    - Lambda network behavior and runtime protection  
  - Mapped to **AWS Foundational Security Best Practices** & **CIS Benchmarks**.

- **Security Hub**:
  - Aggregates findings from GuardDuty, IAM Access Analyzer, Config, etc. into a **central dashboard**.

### Alerting & Automation

- Use **EventBridge** to:
  - Send alerts (SNS, email, chat, …).  
  - Trigger **Lambda / Step Functions** for automatic **remediation**.  
  - Support **cross-account event routing** for centralized security operations.

- **Detection-as-Code**:
  - Manage detection logic as IaC:
    - CloudTrail Lake queries  
    - Event patterns on EventBridge  
  - Enables controlled review, testing, and deployment of detection rules.

> Case study: If there are no logs → there is no evidence → you cannot investigate an incident.

---

## Pillar 3 – Infrastructure Protection

- **VPC Segmentation**:
  - Reduce the **blast radius** when the system is compromised by segmenting and isolating environments.  

- **Subnet placement (Public vs Private)**:
  - Public: ALB, NAT Gateway, public bastion (if any).  
  - Private: EC2 app instances, databases, internal services.  

- **Security Group (SG) vs Network ACL (NACL)**:
  - **SG**: stateful, attached to instances, the “primary firewall”.  
  - **NACL**: stateless, attached to subnets, an additional protection layer.

- **Edge Protection**:
  - **AWS WAF**, **Shield Advanced**, **AWS Network Firewall** for edge defense.  
  - Integrate threat intelligence from **GuardDuty** for automated blocking.

- **Workload Hardening**:
  - Regular patching for EC2/ECS/EKS.  
  - Minimize IAM permissions for workloads.  
  - Image scanning before deployment.  
  - Runtime protections.

> Case study: Many security issues come from placing resources in the **wrong public subnet** – always check placement before deployment.

---

##  Pillar 4 – Data Protection

- **Encryption everywhere**:
  - Enable at-rest encryption for S3, EBS, RDS, DynamoDB.  
  - Enforce TLS/HTTPS when accessing S3, DynamoDB, RDS, etc.

- **AWS KMS**:
  - Manage **CMK → Data Key**.  
  - Key policies, Grants, rotation.  
  - Use IAM conditions to control encrypt/decrypt operations.

- **Secrets Management**:
  - **Secrets Manager** / **SSM Parameter Store**:
    - Automatic secret rotation.  
    - Separate config & secrets from application code.  

- **ACM (AWS Certificate Manager)**:
  - Provides free certificates + auto-renew for ALB, CloudFront, API Gateway.

- **Data classification & guardrails**:
  - Classify data by sensitivity (Public / Internal / Confidential / Restricted).  
  - Apply matching guardrails: IAM, encryption, network controls.

> Case study: Encrypting from the beginning significantly reduces risk in case of a data breach.

---

##  Pillar 5 – Incident Response (IR)

- **AWS IR Lifecycle**:  
  **Prepare → Detect → Investigate → Respond → Recover**

### Playbooks (examples)

- **Compromised IAM key**  
- **Public S3 bucket**  
- **EC2 infected with malware / crypto mining**

### Tools & techniques

- Create **Snapshots** (EBS / instance) to preserve evidence.  
- **Isolation**: modify SG / NACL to isolate compromised instances.  
- Collect evidence for **forensics & audit**.

### IR Automation

- **Lambda**: run small remediation tasks (revert policy, block IPs, disable keys, …).  
- **Step Functions**: orchestrate multi-step, complex IR workflows.  
- **EventBridge**: trigger playbooks based on events from GuardDuty, CloudTrail, Security Hub…

> Conclusion: Incident Response cannot rely 100% on humans – as much as possible should be automated.

---

#  Key Learnings

## Modern Security Mindset

- **Zero Trust & Least Privilege**: no implicit trust, every permission is minimized.  
- **Defense in Depth**: multiple protective layers to reduce risk when one layer is bypassed.  
- **Traceability & IaC**:
  - Every change must be **traceable**.  
  - Infrastructure should be deployed using **IaC** to reduce misconfigurations.  
- Do not trust manual configuration → favor automation + IaC + peer reviews.

## Key Technical Architecture

- **IAM**:
  - Roles > Users  
  - SSO > Local credentials  
  - OIDC > Long-lived Access Keys  

- **Network**:
  - **Private-first**: by default, place resources in private subnets.  
  - SG as the “main wall” (stateful), NACL as a supporting layer (stateless).  
  - Outbound filtering is as important as inbound filtering.

- **Data**:
  - Encrypt by default (S3, EBS, RDS, DynamoDB).  
  - Implement secret rotation according to policies.  
  - Minimize exposure for S3/DB.

- **Detection**:
  - CloudTrail **ON**  
  - GuardDuty **ON**  
  - Sufficient logging to support incident investigations.

- **Incident Response**:
  - Clear playbooks.  
  - Automation for remediation and rollback.  
  - Snapshots/backups for fast recovery.

## Modernization Strategy

- Avoid “big bang” changes, follow a **phased approach**.  
- Use **multi-account architecture** to reduce blast radius and separate environments.

---

#  Applying to Work

In the team’s **AI Chatbot** project:

- Design IAM based on **Roles + Permission Sets** instead of direct users.  
- Apply **VPC segmentation** and a **private-first design** for backend, databases, and vector stores.  
- Enable **GuardDuty + org-level CloudTrail** across all dev/prod environments.  
- Set up **Alerting & IR automation**:
  - EventBridge → Lambda / Step Functions for auto-remediation.  
- Use **Secrets Manager + rotation** instead of hard-coding secrets in code/ENV.  
- Deploy infrastructure using **Terraform/CDK** to reduce drift and configuration errors.

Expected outcome: a chatbot system that is **more stable, more secure, easier to audit, and easier to scale**.

---

#  Event Experience

- The event was well-organized and gave me a **comprehensive view of the Security Pillar** in the AWS Well-Architected Framework.  
- I learned how AWS and large enterprises:
  - Organize security using a multi-account model.  
  - Handle incident & detection in real-world production environments.  

### Technical experience

- Practiced analyzing policies using **IAM Simulator**.  
- Observed the real flow of **S3 public exposure → auto-remediation**.  
- Saw **IR automation** in action for a compromised EC2 instance.  

### Mindset & networking

- Understood how large organizations structure security around **multi-account architectures**.  
- Internalized the mindset of **“secure by design”** – not waiting for an attack to start fixing things.  
- Connected with peers passionate about security/cloud, creating a strong foundation for future learning and work.

### Takeaways

- **Security = culture, not a feature.**  
- **Misconfiguration** is the biggest root cause → **IaC is the lifesaver**.  
- You cannot operate safely in the cloud without: **strong IAM + comprehensive logging + clear IR processes**.
## Some photos from the event
![ws Image](/images/ws3.jpg)

![ws Image](/images/ws3.1.jpg)

![ws Image](/images/ws3.2.jpg)