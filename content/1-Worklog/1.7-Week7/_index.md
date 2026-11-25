---
title: "Week 7 Worklog"
date: 2026-11-16
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives

- Learn how to adapt the Python pipeline for AWS Lambda.
- Define an approach for API key management and scheduled data collection.
- Prepare the deployment structure using AWS SAM.

### Weekly Activities

| Day | Activities | Start Date | Completion Date | References |
| --- | --- | --- | --- | --- |
| 2 | - Study the structure of a Python Lambda function.<br>- Identify the changes required to convert local scripts into a Lambda handler. | 16/11/2026 | 16/11/2026 | [Lambda Handler in Python](https://docs.aws.amazon.com/lambda/latest/dg/python-handler.html) |
| 3 | - Learn how to store an API key using Parameter Store SecureString.<br>- Document how the application should retrieve the parameter and avoid exposing the API key in source code or logs. | 17/11/2026 | 17/11/2026 | [Parameter Store SecureString](https://docs.aws.amazon.com/systems-manager/latest/userguide/secure-string-parameter-kms-encryption.html) |
| 4 | - Read the EventBridge Scheduler documentation.<br>- Define a daily pipeline schedule and plan to keep it disabled during testing. | 18/11/2026 | 18/11/2026 | [EventBridge Scheduler](https://docs.aws.amazon.com/scheduler/latest/UserGuide/what-is-scheduler.html) |
| 5 | - Learn how Lambda sends logs to CloudWatch Logs.<br>- Identify information to record: execution time, record count, validation results, and errors. | 19/11/2026 | 19/11/2026 | [Lambda Logging with Python](https://docs.aws.amazon.com/lambda/latest/dg/python-logging.html) |
| 6 | - Study the basic structure of an AWS SAM template.<br>- Compile a list of resources and configuration values required for the initial deployment. | 20/11/2026 | 20/11/2026 | [AWS SAM Template Anatomy](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-specification-template-anatomy.html) |

### Week 7 Achievements

- Understand the purpose of the Lambda handler and its `event` and `context` parameters.
- Identify the required changes to the Python pipeline:
  - Replace manual API key entry with authorized parameter retrieval.
  - Replace local file paths with an appropriate AWS storage approach.
  - Return execution results and record logs for monitoring.
- Define an approach for storing the EIA API key using Parameter Store SecureString.
- Understand how EventBridge Scheduler invokes Lambda on a schedule.
- List the information to monitor in CloudWatch Logs.
- Gain an initial understanding of the main SAM template sections, including `Parameters`, `Globals`, `Resources`, and `Outputs`.

### Challenges and Next Steps

- The current pipeline uses local files and requires manual API key entry, so it needs adjustments before running automatically.
- Adapt individual functions for Lambda and test each step before enabling the schedule.

### End-of-Week Status

Further develop the approach for migrating the Python pipeline to AWS and prepare the deployment structure. This week focused on learning and design; no additional AWS resources were recorded as deployed for the project.