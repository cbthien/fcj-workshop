---
title: "Week 1 Worklog"
date: "2025-09-08"
weight: 1
chapter: false
pre: " <b> 1.1 </b> "
---

### Week 1 Objectives:

* Understand the structure of an AWS account and the role of the Root User.
* Learn how to create and secure an AWS account.
* Set up IAM Users, IAM Groups and attach permission policies.
* Enable MFA and configure cost alerts.
* Get familiar with the AWS Management Console interface.

### Tasks carried out during the week:

| Day | Tasks                                                                                                                                                                                                                                       | Start Date  | Completion Date  | Reference                                |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ---------------- | ---------------------------------------- |
| 1   | - Overview of the AWS account and responsibilities of the Root User <br> - Understand IAM concepts (User, Group, Policy)                                                                                                                   | 08/09/2025  | 08/09/2025       | <https://000001.awsstudygroup.com/>      |
| 2   | - Create an AWS account <br> - Add a payment method <br> - Verify email & phone number <br> - First login and explore the AWS Console                                                                                                       | 09/09/2025  | 09/09/2025       | <https://000001.awsstudygroup.com/>      |
| 3   | - Secure the Root account <br>&emsp; + Enable MFA <br>&emsp; + Configure password policy <br>&emsp; + Minimize Root User usage <br> - Configure Billing Preferences & monitor Free Tier                                                   | 10/09/2025  | 10/09/2025       | <https://000001.awsstudygroup.com/>      |
| 4   | - Create IAM Group (Administrators) <br> - Attach AdministratorAccess policy <br> - Create IAM User <br> - Configure sign-in for the user and enable MFA                                                                                   | 11/09/2025  | 11/09/2025       | <https://000001.awsstudygroup.com/>      |
| 5   | - Create Budget and Billing Alerts <br> - Review the account security checklist <br> - Practice logging in using IAM User <br> - Explore the AWS Console interface <br> - Summarize lessons learned & issues encountered                   | 12/09/2025  | 12/09/2025       | <https://000001.awsstudygroup.com/>      |

---

### Week 1 Achievements

Week 1 was the phase where I “laid the foundation” for my entire journey with AWS, so I tried to do everything carefully and systematically:

* **Mastering the AWS account structure**  
  I understood clearly the difference between:
  * **Root User** – only used for high-level, sensitive administrative tasks.  
  * **IAM User / IAM Group / Policy** – used for day-to-day access management following best practices.  
  Thanks to that, I no longer thought in a simplistic way like “just log in with root and it’s done”, but became aware of long-term security considerations.

* **Creating and securing the AWS account in a structured way**  
  I did not stop at just creating an AWS account, but also:
  * Set up full payment information, verified email and phone number.  
  * Double-checked each step to ensure the account was operating stably.  
  This helped me feel more confident when using the account for labs and later projects.

* **Protecting the Root account and IAM Users according to best practices**  
  * Enabled **MFA** for the Root User and for the main IAM User that I use daily.  
  * Configured a **password policy** with strict rules (length, special characters, password lifetime, etc.).  
  * Minimized logging in as Root and used only IAM Users for operations.  
  Through this, I realized the importance of security from the very beginning, instead of only caring about “making the service run”.

* **Setting up cost management and early alerts**  
  * Configured **Billing Preferences** to receive emails when there are changes.  
  * Created **Budgets** and **Billing Alerts** to avoid exceeding the Free Tier.  
  Thanks to these steps, I felt more at ease when doing hands-on exercises because I knew that if any unusual costs occurred, I would be notified early.

* **Applying IAM based on best practices instead of doing it superficially**  
  * Created an **IAM Group (Administrators)** and attached **AdministratorAccess** properly.  
  * Created a separate **IAM User** and added it to the group instead of attaching policies directly to the user.  
  * Tried logging in with the IAM User, checked permissions and tested enabling MFA.  
  These actions helped me understand that IAM is not just theory, but an important tool for operating a secure system.

* **Getting familiar with the AWS Management Console and service-oriented thinking**  
  * Spent time exploring the interface, searching for services through the search bar.  
  * Took notes of services that appeared often in documentation (EC2, S3, IAM, CloudWatch, etc.).  
  After Week 1, the initial feeling of being “overwhelmed” by the AWS interface decreased significantly, replaced by familiarity and a clearer picture when reading documentation/architecture.

---

### Self-assessment and difficulties encountered in Week 1

Although Week 1 did not involve much “building systems”, it was the week where I had to change my mindset about using a cloud account in a professional manner.

#### 1. Self-assessment

* **Being proactive and seeing tasks through step by step**  
  I didn’t just complete the checklist, but tried to understand “why this step is necessary”, especially the parts related to Root User, IAM and Billing. When there was something unclear, I actively looked up documentation, asked my mentor, and took notes.

* **Following processes and focusing on security from the start**  
  Instead of skipping parts such as MFA or Budget (which are often underestimated), I seriously completed them all. This helped me form good habits for later weeks, when the system becomes more complex.

* **Able to structure and systematize knowledge**  
  At the end of each day, I summarized: what I learned today, which steps were completed, what I was still stuck on. This habit helped me avoid “losing track” and allowed me to review quickly when needed.

#### 2. Difficulties encountered

* **Confusion with account & permission concepts**  
  At first, I was quite confused in distinguishing:
  * When to use Root, when to use IAM User?  
  * What is the difference between assigning permissions to a Group vs. assigning directly to a User?  
  After reading more AWS documentation and trying several times, I understood the permission model more clearly.

* **Concerns about costs and billing**  
  Because I had to add a payment method (card/bank), I was quite worried about being charged unexpectedly. This made me more cautious, but also cost me extra time to:
  * Read the Billing & Free Tier sections carefully.  
  * Learn how to create Budgets and Alerts.  
  In the long run, this is a “good difficulty”, because it helped me understand cost control more deeply.

* **Too much new information in a short time**  
  Right from the first week I had to get used to:
  * Concepts around accounts, security, and billing.  
  * The Console interface with many services.  
  Sometimes I felt a bit overwhelmed, but I handled it by:
  * Breaking down the content by day (as in the task table).  
  * Focusing only on what was directly related to account & security in Week 1.

---

Overall, although Week 1 was mainly about “laying the groundwork”, I tried to do everything carefully and thoughtfully instead of just doing it for the sake of completion. This is an important foundation so that in Week 2 and Week 3 I can focus more on services and architecture without having to go back and fix basic issues related to the account and security.
