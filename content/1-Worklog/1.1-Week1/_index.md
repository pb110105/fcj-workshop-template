---
title: "Week 1 Worklog"
date: 2026-10-05
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives

- Become familiar with the AWS Management Console and AWS resource management tools.
- Learn about basic services for cost management, access management, and networking.
- Practice building a VPC network, deploying EC2 instances, and establishing a Site-to-Site VPN connection.

### Tasks Performed

| Day | Tasks | Start Date | Completion Date | References |
| --- | --- | --- | --- | --- |
| Monday | Learn how to use the AWS Management Console.<br>Create an AWS account and explore AWS Budgets, AWS Support, IAM, VPCs, and subnets. | 05/10/2026 | 05/10/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| Tuesday | Create an Internet Gateway, route tables, and security groups.<br>Enable VPC Flow Logs to capture network traffic information. | 06/10/2026 | 06/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |
| Wednesday | Deploy EC2 instances and test connectivity.<br>Create a NAT Gateway and use Reachability Analyzer and EC2 Instance Connect Endpoint.<br>Practice accessing EC2 through AWS Systems Manager Session Manager. | 07/10/2026 | 07/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |
| Thursday | Create the VPN environment and establish an AWS Site-to-Site VPN connection.<br>Configure the Customer Gateway and customize VPN tunnel options. | 08/10/2026 | 08/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |
| Friday | Explore alternative VPN configurations and the IKEv2 protocol.<br>Research ideas for an individual project. | 09/10/2026 | 09/10/2026 | [Networking Essentials with VPC](https://000003.awsstudygroup.com/) |

### Achievements

#### 1. AWS Account and Cost Management

- Created an AWS account and successfully signed in to the AWS Management Console.
- Became familiar with Console Home and the service search feature.
- Created **My Zero-Spend Budget** to monitor costs.
- At the time of checking, the budget status was **OK**, with a cost of **USD 0**; the notification email was still awaiting verification.
- Submitted an AWS Support case regarding the budget notification email verification issue.

**AWS Budget screenshot:**

![AWS Budget created; notification email verification is pending](/images/week1/budget.png)

**AWS Support case screenshot:**

![Submitting a support case to AWS Support](/images/week1/support.png)

#### 2. Access Management with IAM

- Practiced granting permissions using the **AdministratorAccess** policy.

![Practicing permission management with AWS IAM](/images/week1/iam.png)

#### 3. Building a VPC Network

Practiced configuring network components in the **Networking Essentials with Amazon VPC** lab:

- Created a VPC and subnets.
- Created an Internet Gateway and attached it to the VPC.
- Configured route tables.
- Created security groups.
- Enabled VPC Flow Logs.

**Creating a VPC:**

![Creating a VPC](/images/week1/createVPC.png)

**Creating subnets:**

![Creating subnets](/images/week1/subnet.png)

**Creating an Internet Gateway:**

![Creating an Internet Gateway](/images/week1/ig.png)

**Configuring route tables:**

![Configuring route tables](/images/week1/route.png)

**Creating security groups:**

![Creating security groups](/images/week1/sg.png)

**Enabling VPC Flow Logs:**

![Enabling VPC Flow Logs](/images/week1/flowlog.png)

#### 4. Deploying EC2 Instances and Testing Connectivity

- Deployed EC2 Public and EC2 Private instances.
- Practiced connecting through SSH and testing connectivity between the instances.
- Created a NAT Gateway to allow EC2 Private to access the Internet.
- Practiced using Reachability Analyzer.
- Practiced accessing EC2 Private through EC2 Instance Connect Endpoint and AWS Systems Manager Session Manager.

**Deploying EC2 instances:**

![Deploying EC2 instances](/images/week1/ec2.png)

**Testing connectivity:**

![Testing EC2 connectivity](/images/week1/testConnection.png)

**Creating a NAT Gateway:**

![Creating a NAT Gateway](/images/week1/nat.png)

**Using Reachability Analyzer:**

![Using Reachability Analyzer](/images/week1/ra.png)

**Accessing EC2 through Session Manager:**

![Accessing EC2 through AWS Systems Manager Session Manager](/images/week1/manager.png)

#### 5. Establishing a Site-to-Site VPN

- Created a VPC to simulate an on-premises environment and an EC2 instance to act as the Customer Gateway.
- Created a Virtual Private Gateway, a Customer Gateway, and a VPN connection.
- Configured Libreswan on the Customer Gateway instance.
- Customized VPN tunnel options and explored IKEv2 configuration.

**Creating the VPN environment:**

![Creating a VPC for the VPN environment](/images/week1/vpcvpn.png)

![Creating an EC2 instance to act as the Customer Gateway](/images/week1/ec2vpn.png)

**Creating connection components:**

![Creating a Virtual Private Gateway](/images/week1/vpg.png)

![Creating a Customer Gateway](/images/week1/customergateway.png)

![Creating a VPN connection](/images/week1/createVPNconnection.png)

**Configuring and Testing the VPN:**

![Configuring the Customer Gateway](/images/week1/customerGatewayConfiguration.png)

![Customizing AWS VPN tunnel options](/images/week1/vpntunnel.png)

![Practicing IKEv2 configuration](/images/week1/ikiev2.png)

### Challenges and Solutions

| Issue Encountered | Resolution |
| --- | --- |
| The budget notification email verification link displayed “Page not found”. | Checked the account, tried resending the verification email, and submitted an AWS Support case. Resolution of the issue has not yet been confirmed. |
| The SSH connection failed with “Connection timed out”. | Checked the security group and updated the SSH rule source to the current My IP address. |
| EC2 Private did not respond to ping requests from the Customer Gateway network. | Added an ICMP rule allowing traffic from `10.11.0.0/16` to the EC2 Private security group, then tested connectivity again. |
| StrongSwan was not available in the software repository being used on Amazon Linux 2023. | Practiced IKEv2 using the installed Libreswan software; deployment with StrongSwan has not been practiced. |

### Lessons Learned

- Understood the roles of VPCs, subnets, route tables, Internet Gateways, and NAT Gateways.
- Learned to troubleshoot connectivity by checking security groups, routing configurations, and VPN tunnel status.
- Distinguished between EC2 access methods: SSH, EC2 Instance Connect Endpoint, and Session Manager.
- Understood that AWS Budgets provides cost alerts and does not automatically stop all resources.
- Recognized the importance of protecting SSH keys and pre-shared keys (PSKs), and keeping sensitive information out of reports and repositories.