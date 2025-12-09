---
title: "Week 2 Worklog"
date: "2025-09-15"
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* Understand AWS Budgets and how to use them to manage and monitor AWS costs.
* Learn different types of AWS Budgets: Cost Budget, Usage Budget, RI Budget, Savings Plans Budget.
* Practice creating budgets using templates and custom settings, and cleaning up resources.
* Understand AWS Support: support plans, how to access AWS Support, and how to create and manage support requests.
* Build awareness of cost control and how to get help from AWS when issues occur.

---

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                  | Start Date | Completion Date | Reference Material                         |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------------- | ------------------------------------------ |
| 1   | - Study **AWS Budgets** overview <br>&emsp; + What is AWS Budgets? <br>&emsp; + Why use budgets to control costs? <br>&emsp; + Types of budgets (Cost, Usage, RI, Savings Plans)                                                     | 09/15/2025 | 09/15/2025       | <https://000007.awsstudygroup.com/>        |
| 2   | - **Hands-on with Budgets (1):** <br>&emsp; + Create Budget by Template <br>&emsp; + Create a Cost Budget with alert thresholds <br>&emsp; + Review budget details and notification settings                                         | 09/16/2025 | 09/16/2025       | <https://000007.awsstudygroup.com/>        |
| 3   | - **Hands-on with Budgets (2):** <br>&emsp; + Create a Usage Budget for a specific service (e.g., EC2) <br>&emsp; + Create RI Budget <br>&emsp; + Understand when to use each type of budget                                        | 09/17/2025 | 09/17/2025       | <https://000007.awsstudygroup.com/>        |
| 4   | - **Hands-on with Budgets (3):** <br>&emsp; + Create Savings Plans Budget <br>&emsp; + Review alerts and examples of cost overrun scenarios <br>&emsp; + Clean up budgets and related resources after the lab                       | 09/18/2025 | 09/18/2025       | <https://000007.awsstudygroup.com/>        |
| 5   | - Study **AWS Support**: <br>&emsp; + AWS Support Plans and their differences <br>&emsp; + How to access AWS Support Center <br> - **Hands-on:** <br>&emsp; + Navigate to Support Center <br>&emsp; + Create a support case <br>&emsp; + View / update / close support requests | 09/19/2025 | 09/19/2025       | <https://000009.awsstudygroup.com/>        |

---

### Week 2 Achievements

Week 2 focused on building a solid foundation in **cost management** and **support processes** on AWS. Instead of only learning services, I learned how to keep an AWS environment sustainable and under control.

* **Understanding the role of AWS Budgets in cost management**  
  I gained a clear understanding of:
  * What **AWS Budgets** is and how it differs from just looking at the Billing dashboard.  
  * Why proactive budget configuration is important to avoid unexpected cost spikes.  
  * How budgets fit into an overall cost management strategy for workloads on AWS.

* **Differentiating between multiple budget types**  
  I learned to distinguish the use cases and strengths of each budget type:
  * **Cost Budget** – controls total spending (e.g., all services in a month).  
  * **Usage Budget** – tracks consumption of specific resources (e.g., EC2 hours, S3 storage).  
  * **RI Budget** – monitors Reserved Instances utilization and coverage.  
  * **Savings Plans Budget** – tracks Savings Plans spend and helps ensure commitments are used effectively.  
  This helped me understand that “one budget type does not fit all” and each workload may require a different combination.

* **Hands-on experience creating and configuring budgets**  
  I didn’t just read documentation – I practiced:
  * Creating budgets using **templates** for faster setup.  
  * Creating **custom Cost Budgets** with specific thresholds and time periods.  
  * Reviewing detailed budget configuration, including scope, period, and filters.  
  Through this, I became more confident working inside the Billing & Cost Management console rather than being hesitant to touch it.

* **Setting up budget alerts and notification channels**  
  I configured email alerts so that:
  * Notifications are sent when **actual costs** exceed a defined threshold.  
  * Notifications are also sent when **forecasted costs** are expected to exceed the budget.  
  This gave me a realistic view of how budgets can be used in real environments to catch issues before they turn into actual overspending.

* **Cleaning up budgets and remaining resources after the lab**  
  After finishing the hands-on work:
  * I reviewed existing budgets and deleted those no longer needed.  
  * I double-checked that no unnecessary alerts or test configurations remained.  
  This reinforced the habit of cleaning up after experiments to keep the account tidy and easier to manage.

* **Understanding AWS Support and when to use it**  
  I learned:
  * The differences between various **AWS Support Plans** (Basic, Developer, Business, Enterprise).  
  * Which features are available under the **Basic** plan (e.g., documentation, forums) and which require paid plans.  
  * Realistic scenarios where opening an AWS support case is the right approach instead of trying to fix everything alone.

* **Hands-on practice with AWS Support Center**  
  I practiced:
  * Navigating to the **AWS Support Center** from the console.  
  * Creating a **support case**, choosing the right category and severity level.  
  * Viewing, updating, and closing support requests.  
  This helped demystify the support process and made me more comfortable asking for help in a structured way when needed.

* **Building stronger awareness of cost control and support processes**  
  Overall, Week 2 helped me realize that:
  * Using AWS responsibly is not only about deploying resources, but also about actively monitoring costs.  
  * Knowing **how and when to contact AWS Support** is an important skill, especially when working in production-like environments.  
  This mindset will be very valuable as future weeks move on to more complex architectures and services.

---

#### 1. Self-assessment

* **More confident working with the Billing console**  
  At the beginning, I was still a bit hesitant to touch the Billing page due to fear of misconfiguring something. By the end of the week, after creating, editing, and deleting multiple budgets, I became more comfortable navigating and understanding cost-related information.

* **Improved understanding of cost visibility and alerts**  
  I started to think in terms of:
  * “What will happen if I forget to stop some resources?”  
  * “How can I know in advance if my costs are going out of control?”  
  This is a big improvement compared to only thinking about technical functionality.

* **Better structured approach to learning**  
  I followed a clear sequence:
  * Learn concepts → do hands-on labs → review results → clean up resources.  
  This helped me retain knowledge longer and avoid just “clicking around” without understanding.

#### 2. Challenges encountered

* **Understanding when to use each type of budget**  
  At first, I found it a bit confusing:
  * When should I use a **Cost Budget** vs. a **Usage Budget**?  
  * In what scenarios are **RI** and **Savings Plans** budgets really necessary?  
  I overcame this by mapping each budget type to realistic usage scenarios (e.g., long-term EC2 usage, committed usage plans, or student/free-tier environments).

* **Interpreting forecast vs. actual metrics**  
  It took some time to understand:
  * The difference between **actual** and **forecasted** cost/usage.  
  * Why alerts can be triggered even when current spending is still below the budget (due to forecast).  
  This required careful reading of the console and experimenting with different thresholds.

* **Getting used to the support case creation flow**  
  When first creating a support case, I struggled a bit with:
  * Choosing the correct **category** and **severity** level.  
  * Writing a clear and concise problem description.  
  With practice, I learned how to describe issues more effectively, which is an important skill in real projects.

---

Overall, Week 2 strengthened my understanding of **cost management** and **support workflows** on AWS. These skills are essential for operating real workloads in the cloud, not just for passing labs or tutorials. The knowledge I gained will help me avoid common pitfalls like unexpected bills and feeling “stuck” when something breaks in a cloud environment.
