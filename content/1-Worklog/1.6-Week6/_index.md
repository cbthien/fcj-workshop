---
title: "Week 6 Worklog"
date: "2025-10-14"
weight: 6
chapter: false
pre: " <b> 1.6 </b> "
---

### Week 6 Objectives:

* Learn how to deploy and manage Amazon RDS MySQL in a secure VPC architecture.
* Understand how EC2 instances connect to RDS in private subnets.
* Deploy an application that interacts with RDS and practice backup/restore operations.
* Learn how to deploy and manage applications using Amazon Lightsail.
* Practice cost optimization techniques using snapshots, scaling, alarms, and resource cleanup.

---

### Tasks to be carried out this week:

| Day | Task                                                                                                                                                                                                                                            | Start Date | Completion Date | Reference Material                         |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |------------| ---------------- | ------------------------------------------ |
| 1   | - Study RDS overview & prerequisites <br>&emsp; + Supported engines <br>&emsp; + VPC design for RDS (public EC2 → private RDS)                                                                            | 13/10/2025 | 13/10/2025       | <https://000005.awsstudygroup.com/>        |
| 2   | - **Hands-on RDS:** <br>&emsp; + Launch EC2 instance in public subnet <br>&emsp; + Create RDS MySQL instance in private subnet <br>&emsp; + Configure security groups for connectivity                    | 14/10/2025  | 14/10/2025        | <https://000005.awsstudygroup.com/>        |
| 3   | - **Application Deployment:** <br>&emsp; + Deploy application that queries the RDS database <br>&emsp; + Test CRUD operations through EC2                                                                  | 15/10/2025  | 15/10/2025      | <https://000005.awsstudygroup.com/>        |
| 4   | - **Lightsail Workshop – Part 1:** <br>&emsp; + Deploy database on Lightsail <br>&emsp; + Deploy WordPress, Prestashop, and Akaunting instances                                                            | 16/10/2025 | 16/10/2025      | <https://000045.awsstudygroup.com/>        |
| 5   | - **Lightsail Workshop – Part 2:** <br>&emsp; + Configure application security <br>&emsp; + Create snapshots <br>&emsp; + Upgrade to larger instance <br>&emsp; + Create CloudWatch alarms <br>&emsp; + Resource cleanup | 17/10/2025 | 17/10/2025       | <https://000045.awsstudygroup.com/>        |

---

### Week 6 Achievements:

* Understood RDS architecture and how relational databases operate within AWS VPC.
* Successfully deployed EC2 and RDS MySQL with proper networking and security groups.
* Deployed an application connected to RDS and validated database operations.
* Performed RDS snapshot backup & restore operations.
* Gained experience deploying applications on Amazon Lightsail (WordPress, Prestashop, Akaunting).
* Learned how to secure Lightsail applications using best practices.
* Practiced cost optimization through snapshots, scaling instances, and alarms.
* Completed full cleanup of Lightsail and RDS resources to avoid unnecessary charges.
