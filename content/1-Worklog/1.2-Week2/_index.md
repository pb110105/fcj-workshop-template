---
title: "Week 2 Worklog"
date: 2026-10-12
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives

- Review the AWS environment.
- Explore project topics and develop an initial plan.

### Tasks for This Week

| Day | Tasks | Start Date | Completion Date | References |
| --- | --- | --- | --- | --- |
| Monday | - Explore project ideas and topics on AWS.<br>- Read documentation on deploying serverless applications with AWS SAM. | 12/10/2026 | 12/10/2026 | [AWS SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) |
| Tuesday | - Continue exploring suitable project topics.<br>- Research electricity trends and potential data sources for the project. | 13/10/2026 | 13/10/2026 | [IEA Electricity 2026](https://www.iea.org/reports/electricity-2026) |
| Wednesday | - Review active AWS resources.<br>- Identify unused resources and plan cleanup to reduce costs. | 14/10/2026 | 14/10/2026 | [AWS Free Tier](https://aws.amazon.com/free/) |
| Thursday | - Explore and compare data pipeline and automated file processing topics.<br>- Identify core functionality and potential AWS services. | 15/10/2026 | 15/10/2026 | [Amazon Athena](https://docs.aws.amazon.com/athena/latest/ug/what-is.html), [AWS SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) |
| Friday | - Select electricity data as the project focus; explore EIA Open Data, API documentation, and Grid Monitor.<br>- Outline the project implementation plan and potential AWS services.<br>- Clean up resources from previous labs and check the remaining AWS credits. | 16/10/2026 | 16/10/2026 | [EIA Open Data](https://www.eia.gov/opendata/), [EIA API](https://www.eia.gov/opendata/documentation.php), [Grid Monitor](https://www.eia.gov/electricity/gridmonitor/) |

### Achievements

- Explored and compared project topics involving data pipelines, automated file processing, monitoring, and backups.
- Selected the project direction: building a pipeline for API-based electricity data ingestion, data quality validation, and analytics on AWS with automated deployment.
- Defined the proposed functional scope: scheduled data collection, raw and clean data storage, data quality checks, deduplication, error handling, analytics, and monitoring.
- Began exploring EIA Open Data, API documentation, and Electric Grid Monitor.
- Studied the roles of potential AWS services and AWS SAM for infrastructure as code deployment.
- Reviewed AWS costs and resources from previous labs; stopped three EC2 instances, deleted the VPN connection, NAT Gateway, three Interface Endpoints, and the VPC Flow Logs configuration; released the Elastic IP address.
- Set CloudWatch Logs retention to one day and retained three EBS volumes to preserve lab data and configurations.
- Outlined the project implementation approach with a focus on cost control.