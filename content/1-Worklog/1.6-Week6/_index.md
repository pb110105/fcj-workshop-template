---
title: "Week 6 Worklog"
date: 2026-11-09
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives

- Strengthen understanding of AWS infrastructure and AWS CLI configuration.
- Explore data storage and permissions for the electricity data pipeline project.
- Review the architecture before deployment.

### Weekly Activities

| Day | Activities | Start Date | Completion Date | References |
| --- | --- | --- | --- | --- |
| Monday | - Study the differences between AWS Regions and Availability Zones.<br>- Review the reasons for selecting Singapore for the project. | 09/11/2026 | 09/11/2026 | [AWS Regions and Availability Zones](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html) |
| Tuesday | - Review the use of multiple AWS CLI profiles.<br>- Learn how to specify a profile and region when running commands. | 10/11/2026 | 10/11/2026 | [AWS CLI Configuration Files](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html) |
| Wednesday | - Learn how to organize Amazon S3 objects using prefixes.<br>- Review the proposed `raw/`, `clean/`, and `quarantine/` data zones for the project. | 11/11/2026 | 11/11/2026 | [Organizing Objects Using Prefixes](https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-prefixes.html) |
| Thursday | - Read documentation about AWS Lambda execution roles.<br>- Identify the permissions Lambda is expected to need for writing data to S3 and sending logs. | 12/11/2026 | 12/11/2026 | [AWS Lambda Execution Role](https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html) |
| Friday | - Review the architecture diagram and document the role of each service.<br>- Summarize the preparation steps required before deployment with AWS SAM. | 13/11/2026 | 13/11/2026 | [AWS SAM Developer Guide](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html) |

### Week 6 Achievements

- Understand the differences between Regions and Availability Zones and the considerations for selecting a deployment region.
- Strengthen understanding of AWS CLI profiles and region configuration.
- Define the proposed S3 data zones:
  - `raw/`: Original data from the EIA API.
  - `clean/`: Validated and transformed data.
  - `quarantine/`: Data that fails validation.
- Understand the purpose of Lambda execution roles and the principle of granting only necessary permissions.
- Review the architecture and identify the remaining preparation tasks before AWS deployment.

### Challenges and Next Steps

- Distinguish deployment permissions from Lambda runtime permissions.
- Continue reviewing documentation and list the permissions required by each component before writing the infrastructure configuration.

### End-of-Week Status

The week focused on strengthening knowledge and reviewing the design. No additional AWS resources were recorded as deployed for the project during this week.