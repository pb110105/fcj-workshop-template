---
title: "Workshop"
date: 2026-10-23
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Electricity Data Ingestion, Quality Validation, and Analytics Pipeline on AWS

## Introduction

This workshop guides the development of a pipeline that collects data from the EIA Open Data API, validates its quality, and analyzes electricity data.

The project begins with a PowerShell implementation running locally to verify the data source and processing logic. The next phase will port the logic to Python, deploy it on AWS using AWS SAM, and introduce automated scheduling.

## Objectives

- Collect electricity data by respondent, metric, and time range.
- Manage parameters using JSON configuration files.
- Validate data quality before analysis.
- Detect duplicate records, missing records, and invalid values.
- Compare actual demand with the day-ahead forecast.
- Execute collection, validation, and analysis with one command.
- Deploy the pipeline on AWS using infrastructure as code.
- Monitor execution and control costs.

## Data Source

Data is retrieved from the following EIA Open Data API route:

`electricity/rto/region-data/data/`

Initial scope:

| Attribute | Value |
| --- | --- |
| Respondent | CISO — California Independent System Operator |
| Frequency | Hourly |
| Time zone | UTC |
| Source unit | Megawatthours — MWh |
| D | Actual electricity demand |
| DF | Day-ahead electricity demand forecast |
| NG | Net electricity generation |

DF is a forecast supplied by EIA. This workshop has not developed a separate forecasting model.

## Workshop Sections

| Section | Content | Status |
| --- | --- | --- |
| 1 | Overview, scope, and solution design | Initial scope defined; AWS architecture being finalized |
| 2 | Environment preparation and EIA API key | PowerShell, Git, Python, AWS CLI, and SAM CLI available; AWS CLI authentication not yet confirmed |
| 3 | Collecting data from the EIA API | Completed locally |
| 4 | Data quality validation | Completed locally |
| 5 | Electricity demand and forecast error analysis | Completed locally |
| 6 | Pipeline configuration and orchestration | Completed locally |
| 7 | AWS deployment using SAM | Not yet implemented |
| 8 | Scheduling, monitoring, and Athena queries | Not yet implemented |
| 9 | AWS testing and resource cleanup | Not yet implemented |

Detailed instructions will be updated as each section is implemented.

## Local Implementation

### Components

| File | Purpose |
| --- | --- |
| `collect_data.ps1` | Call the EIA API and save JSON and CSV data |
| `check_data.ps1` | Validate data quality and completeness |
| `analyze_data.ps1` | Compare actual demand with the forecast |
| `run_pipeline.ps1` | Execute the steps in order and stop on failure |
| `config_week1.json` | Configure a one-week dataset |
| `config_month.json` | Configure a one-month dataset |

### Running the Pipeline

Run the commands from the source repository root.

**One-week dataset:**

    powershell -NoProfile -ExecutionPolicy Bypass -File .\run_pipeline.ps1 -ConfigPath .\config_week1.json

**One-month dataset:**

    powershell -NoProfile -ExecutionPolicy Bypass -File .\run_pipeline.ps1 -ConfigPath .\config_month.json

Enter the EIA API key when prompted. Do not store the key in source code or upload it to GitHub.

## Data Quality Validation

Business key:

`period + respondent + type`

Implemented checks:

- Required fields are present.
- Values are finite numbers.
- Respondents, metrics, and units match expectations.
- Timestamps fall within the configured range.
- Business keys are unique.
- Every expected hour, respondent, and metric combination is present.
- No unexpected combinations occur.

Validation results are exported to a JSON report.

## Local Test Results

| Period | Records | Compared hours | Quality | MAE — MWh | WAPE |
| --- | --- | --- | --- | --- | --- |
| September 1–30, 2026 | 2,160 | 720 | PASS | 2,580.79 | 8.53% |
| September 1–7, 2026 | 504 | 168 | PASS | 2,567.07 | 8.92% |

These metrics were calculated from the data available at execution time. Results may change if EIA revises the source data.

### Verified Failure Scenarios

| Scenario | Result |
| --- | --- |
| Add one duplicate record | Detect one duplicate group and return FAIL |
| Remove one record | Detect one missing hour–metric combination and return FAIL |
| Select a nonexistent configuration file | Stop the pipeline before collection |
| Submit an empty API key | Stop collection without running subsequent steps |

Successful pipeline runs finish with exit code `0`. The tested failure scenarios return exit code `1`.

## Planned AWS Implementation

Proposed services:

- Amazon EventBridge Scheduler: scheduled execution.
- AWS Lambda: collection, validation, and standardization.
- Amazon S3: original data, clean data, and reports.
- AWS Glue Data Catalog: table metadata.
- Amazon Athena: data queries.
- Amazon CloudWatch: logs, metrics, and alarms.
- AWS Systems Manager Parameter Store: API key storage as a SecureString.
- AWS IAM: access permissions.

Infrastructure is expected to be defined using AWS SAM and deployed in Singapore (`ap-southeast-1`).

AWS deployment is not yet complete. The architecture diagram, cost estimate, and execution evidence will be added during implementation.

## Source Code and References

- [Source repository](https://github.com/pb110105/electricity-data-pipeline)
- [EIA Open Data](https://www.eia.gov/opendata/)
- [EIA API Documentation](https://www.eia.gov/opendata/documentation.php)
- [EIA Electric Grid Monitor](https://www.eia.gov/electricity/gridmonitor/)
- [AWS SAM Documentation](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html)