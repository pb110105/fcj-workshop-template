---
title: "Week 4 Worklog"
date: 2026-10-26
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives

- Review project progress and completed activities.
- Set up an IAM user, MFA, and an AWS CLI profile for the project.
- Migrate the EIA data pipeline from PowerShell to Python.
- Test the data collection, quality validation, and analysis workflow.
- Design the AWS solution architecture diagram.
- Explore and complete activities to earn AWS credits.

### Weekly Activities

| Day | Activities | Start Date | Completion Date | References |
| --- | --- | --- | --- | --- |
| Monday | - Read documentation and review completed activities.<br>- Review pipeline progress, architecture documentation, and remaining tasks. | 26/10/2026 | 26/10/2026 | [AWS Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| Tuesday | - Create the IAM user `fcaj-project-user`, add it to the administrator group, and configure MFA.<br>- Sign in to AWS CLI using the `fcaj-project` profile; verify the identity and Singapore region.<br>- Migrate EIA data collection, quality validation, and analysis functions from PowerShell to Python.<br>- Test weekly and monthly datasets, including duplicate and missing record scenarios.<br>- Integrate the Python scripts into a pipeline executed with one command; verify that the pipeline stops when no API key is entered.<br>- Push architecture documentation to GitHub and prepare the Python scripts for commit. | 27/10/2026 | 27/10/2026 | [AWS CLI Sign-in](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sign-in.html), [EIA API Documentation](https://www.eia.gov/opendata/documentation.php) |
| Wednesday | - Review and refine the AWS project architecture.<br>- Identify the main components and relationships between services in the pipeline. | 28/10/2026 | 28/10/2026 | [AWS Architecture Center](https://aws.amazon.com/architecture/) |
| Thursday | - Explore and complete activities to earn additional AWS credits, working toward the program's maximum of USD 100.<br>- Track activity progress in the AWS account. | 29/10/2026 | 29/10/2026 | [AWS Free Tier](https://aws.amazon.com/free/) |
| Friday | - Build the solution architecture diagram using diagrams.net and AWS service icons.<br>- Illustrate EIA data collection, Lambda processing, S3 storage, and Athena queries.<br>- Add components for API key management, encryption, scheduling, monitoring, and infrastructure deployment.<br>- Review service labels, connection directions, and diagram layout; identify adjustments needed before including the diagram in the report. | 30/10/2026 | 30/10/2026 | [AWS Architecture Icons](https://aws.amazon.com/architecture/icons/), [diagrams.net](https://app.diagrams.net/) |

### Week 4 Achievements

#### 1. AWS Identity and CLI Setup

- Create the IAM user `fcaj-project-user` and configure MFA.
- Sign in to AWS Management Console using the IAM user.
- Configure a dedicated AWS CLI profile named `fcaj-project` using `aws login`.
- Verify that AWS CLI uses the correct IAM user and the `ap-southeast-1` region.
- Use temporary credentials without creating long-term Access Keys and Secret Keys for this setup.

#### 2. Pipeline Migration to Python

- Develop four scripts:
  - `collect_data.py`: Collect data from the EIA API.
  - `check_data.py`: Validate data quality.
  - `analyze_data.py`: Analyze differences between actual electricity demand and forecasts.
  - `run_pipeline.py`: Coordinate the processing steps.
- Use shared JSON configuration files and support the `--config` argument.
- Successfully run the complete Python pipeline with a one-week dataset using a single command.
- Save Python data and reports separately to support comparison with PowerShell results.

#### 3. Testing and Result Comparison

| Test Case | Result |
| --- | --- |
| Validate one month of data: 2,160 records | PASS, exit code `0` |
| Validate one week of data: 504 records | PASS, exit code `0` |
| Add one duplicate record | Detect 1 duplicate key group, FAIL, exit code `1` |
| Remove one record | Detect 1 missing hour/metric key, FAIL, exit code `1` |
| Leave the EIA API key empty | Pipeline stops at the collection step, exit code `1` |
| Run the Python pipeline with the weekly configuration | Collection, validation, and analysis succeed, exit code `0` |

Python analysis results match the PowerShell results:

| Data Range | Hours Compared for D and DF | MAE (MWh) | WAPE |
| --- | ---: | ---: | ---: |
| 01–30/09/2026 | 720 | 2,580.79 | 8.53% |
| 01–07/09/2026 | 168 | 2,567.07 | 8.92% |

These metrics evaluate forecasts provided by EIA; the project does not yet include a custom forecasting model.

#### 4. Solution Architecture Design

- Create an architecture diagram for the Singapore region.
- Identify the responsibilities of each component:
  - **EventBridge Scheduler:** Trigger the pipeline on a schedule.
  - **AWS Lambda:** Collect, validate, and transform data.
  - **Parameter Store and AWS KMS:** Store and protect the API key.
  - **Amazon S3:** Store raw data, clean data, data that fails validation, and reports.
  - **AWS Glue Data Catalog:** Manage schemas and metadata.
  - **Amazon Athena:** Query and analyze data stored in S3.
  - **Amazon CloudWatch:** Record logs, monitor execution, and provide alarms.
  - **AWS SAM/CloudFormation:** Deploy infrastructure as code.
- Review the diagram and identify adjustments needed before including it in the report.
- Push `ARCHITECTURE.md` to GitHub.

#### 5. AWS Credits Exploration

- Explore and complete activities to earn additional credits through the AWS program.
- Distinguish activity completion from credits actually awarded; receipt of the full USD 100 has not been confirmed.

### End-of-Week Status

The Python pipeline runs successfully on the local computer and has been tested with valid data, duplicate records, missing records, and an empty API key.

The IAM user, MFA, and AWS CLI profile have been configured, and a solution architecture diagram has been drafted. The project's processing and storage components have not yet been deployed to AWS.