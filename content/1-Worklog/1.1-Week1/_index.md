
---
title: "Week 1 Worklog"
date: 2026-10-05
weight: 1
chapter: false
pre: "<b>1.1.</b>"
---

### Week 1 Objectives:

- Become familiar with the AWS Management Console and basic AWS services.
- Learn about AWS cost management, Identity and Access Management (IAM), and cloud networking.
- Understand the core components of Amazon VPC, including subnets, route tables, Internet Gateways, NAT Gateways, and security groups.
- Practice deploying Amazon EC2 instances and troubleshooting network connectivity.
- Explore AWS Site-to-Site VPN and secure communication between networks.

### Tasks to be carried out this week:

| Day | Tasks | Start Date | Completion Date | References |
|---|---|---|---|---|
| 2 | Explore the AWS Management Console. Create an AWS account and learn about AWS Budgets, AWS Support, IAM, VPCs, and subnets. | 05/10/2026 | 05/10/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3 | Create an Internet Gateway, configure route tables and security groups, and enable VPC Flow Logs. | 06/10/2026 | 06/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |
| 4 | Deploy public and private EC2 instances, configure a NAT Gateway, test connectivity, and explore Reachability Analyzer, EC2 Instance Connect Endpoint, and Session Manager. | 07/10/2026 | 07/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |
| 5| Create a simulated on-premises environment and configure AWS Site-to-Site VPN, Virtual Private Gateway, Customer Gateway, and VPN tunnels. | 08/10/2026 | 08/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |
| 6 | Explore IKEv2 and alternative VPN configurations. Research potential ideas for an individual project. | 09/10/2026 | 09/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |

### Week 1 Achievements:

**1. AWS Account Setup and Cost Management**

- Created an AWS account and successfully accessed the AWS Management Console.
- Explored essential AWS services and resource management tools.
- Created **My Zero-Spend Budget** to monitor AWS spending.
- Confirmed that the budget status was **OK**, with a recorded cost of **USD 0** at the time of checking.
- Submitted an AWS Support case regarding an email verification issue.

**2. Identity and Access Management (IAM)**

- Explored AWS IAM users, roles, and policies.
- Practiced assigning permissions using the **AdministratorAccess** policy.
- Gained a basic understanding of AWS access management and security.

**3. Amazon VPC Networking**

- Created a VPC with public and private subnets.
- Configured Internet Gateways, route tables, and security groups.
- Enabled VPC Flow Logs to capture network traffic metadata.
- Understood the roles of different networking components in AWS.

**4. Amazon EC2 Deployment and Connectivity**

- Launched EC2 instances in public and private subnets.
- Practiced connecting to EC2 instances using SSH.
- Configured a NAT Gateway for outbound Internet access from private instances.
- Explored Reachability Analyzer for network troubleshooting.
- Practiced accessing private instances using EC2 Instance Connect Endpoint and AWS Systems Manager Session Manager.
- Resolved an SSH connection timeout by updating the security group rule.

**5. AWS Site-to-Site VPN**

- Created a simulated on-premises network environment.
- Configured Virtual Private Gateway, Customer Gateway, and AWS Site-to-Site VPN.
- Installed and configured Libreswan on an EC2 instance acting as the Customer Gateway.
- Explored VPN tunnel options and IKEv2 configuration.
- Practiced troubleshooting ICMP connectivity by updating security group rules.

**6. Knowledge and Experience Gained**

- Developed foundational knowledge of AWS cloud infrastructure and networking.
- Improved practical skills in deploying and configuring AWS resources.
- Learned to troubleshoot network connectivity using routing and security group configurations.
- Understood the importance of AWS cost monitoring and resource security.
- Gained hands-on experience with EC2 access methods and VPN configurations.
