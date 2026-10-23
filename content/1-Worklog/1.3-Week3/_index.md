---
title: "Week 3 Worklog"
date: 2026-10-19
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives

- Explore electricity data sources from EIA Open Data.
- Build a data collection, quality validation, and analysis pipeline using PowerShell.
- Separate configuration from code to support different data ranges.
- Study serverless architecture and outline an AWS deployment approach.
- Prepare a cost estimate for the project.

### Weekly Activities

| Day | Activities | Start Date | Completion Date | References |
| --- | --- | --- | --- | --- |
| Monday | - Explore the EIA API Dashboard and select hourly electricity demand data from the California Independent System Operator (CISO).<br>- Call the API using PowerShell and retrieve 25 Demand (D) records.<br>- Check required fields, duplicate records, numeric values, and hourly completeness.<br>- Create and run `check_data.ps1`, exporting `data_quality_summary.json`. | 19/10/2026 | 19/10/2026 | [EIA Open Data](https://www.eia.gov/opendata/), [EIA API Documentation](https://www.eia.gov/opendata/documentation.php) |
| Tuesday | - Build and test the EIA data pipeline locally using PowerShell.<br>- Collect 2,160 CISO records for September 2026 covering D, DF, and NG.<br>- Validate data quality and test duplicate and missing record detection.<br>- Develop an analysis script to compare actual demand with EIA-provided forecasts.<br>- Integrate the steps into a pipeline executed with a single command; complete successfully with exit code `0`. | 20/10/2026 | 20/10/2026 | [EIA API Documentation](https://www.eia.gov/opendata/documentation.php), [EIA Electric Grid Monitor](https://www.eia.gov/electricity/gridmonitor/) |
| Wednesday | - Study serverless data analytics pipeline architecture on AWS and approaches to data quality validation.<br>- Review data lake applications in electricity analytics to guide the project architecture. | 21/10/2026 | 21/10/2026 | [AWS Serverless Data Analytics Pipeline](https://aws.amazon.com/blogs/big-data/aws-serverless-data-analytics-pipeline-reference-architecture/), [AWS Smart Meter Data Analytics](https://aws.amazon.com/blogs/industries/aws-releases-smart-meter-data-analytics-platform/) |
| Thursday | - Back up the current pipeline scripts.<br>- Move collection and processing settings into a JSON configuration file.<br>- Update the collection, validation, and analysis scripts to use a shared configuration.<br>- Successfully test one-month and one-week datasets, confirming that the time range can be changed without modifying the code. | 22/10/2026 | 22/10/2026 | [EIA API Documentation](https://www.eia.gov/opendata/documentation.php) |
| Friday | - Create separate weekly and monthly configurations; test the `-ConfigPath` parameter and missing configuration file handling.<br>- Push source code and README to GitHub and configure `.gitignore`.<br>- Install and verify AWS CLI and AWS SAM CLI versions.<br>- Outline the AWS architecture for the project.<br>- Prepare a Singapore-region cost estimate for Lambda, S3, Athena, CloudWatch, Glue Data Catalog, EventBridge Scheduler, Parameter Store, and KMS.<br>- Define assumptions for storage, executions, queries, and monitoring; save the shared estimate link. | 23/10/2026 | 23/10/2026 | [Project Repository](https://github.com/pb110105/electricity-data-pipeline), [AWS SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html), [AWS Cost Estimate](https://calculator.aws/#/estimate?id=b15d336bada5c522a1ed6521fac734952eeb4469) |

### Week 3 Achievements

#### Data Collection and Quality Validation

- Successfully call the EIA API and save data in JSON and CSV formats.
- Collect hourly CISO electricity data in UTC for three metrics:
  - **D — Demand:** Actual electricity demand.
  - **DF — Day-ahead demand forecast:** Electricity demand forecast for the following day.
  - **NG — Net generation:** Net electricity generation.
- Implement checks for required fields, duplicate keys, valid numeric values, respondent, metrics, units, and hourly completeness.
- Test duplicate and missing records; confirm that the validator detects errors and returns `FAIL` with exit code `1`.

#### Configurable Pipeline Development

- Complete four scripts:
  - `collect_data.ps1`: Collect data.
  - `check_data.ps1`: Validate data quality.
  - `analyze_data.ps1`: Analyze forecast errors.
  - `run_pipeline.ps1`: Coordinate the processing steps.
- Integrate the complete workflow into a single command.
- Ensure the pipeline stops when a step fails and returns exit code `0` upon successful completion.
- Move settings into JSON configuration files and support configuration selection through `-ConfigPath`.
- Successfully test one-month and one-week datasets without modifying the code.

#### Analysis Results

| Data Range | Records | Hours Compared for D and DF | Quality Validation | MAE (MWh) | WAPE |
| --- | ---: | ---: | --- | ---: | ---: |
| 01–30/09/2026 | 2,160 | 720 | PASS | 2,580.79 | 8.53% |
| 01–07/09/2026 | 504 | 168 | PASS | 2,567.07 | 8.92% |

- Export hourly comparisons of actual demand and forecast demand.
- Identify the hours with the largest absolute errors.
- Export summary reports containing MAE and WAPE.
- Evaluate forecasts provided by EIA; no custom forecasting model has been developed.

#### AWS Deployment Preparation

- Manage source code using Git and host it on GitHub.
- Configure `.gitignore` to exclude generated data, backups, and sensitive files.
- Install and verify AWS CLI and AWS SAM CLI versions.
- Outline the serverless architecture and identify the roles of the AWS services.
- Prepare an estimated cost of approximately **USD 0.32/month**, equivalent to **USD 3.84 over 12 months**, based on the configured workload and Free Tier allowances applied by the Calculator.
- Save the [shared cost estimate](https://calculator.aws/#/estimate?id=b15d336bada5c522a1ed6521fac734952eeb4469) for reference in the proposal.

### End-of-Week Status

The pipeline runs successfully on the local computer. The AWS architecture and cost estimate have been prepared; AWS resources for the project have not yet been deployed.