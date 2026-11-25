---
title: "Week 8 Worklog"
date: 2026-11-23
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives

- Learn how to organize clean data for querying.
- Clarify the roles of AWS Glue Data Catalog and Amazon Athena.
- Prepare analytical queries and an AWS testing plan.

### Weekly Activities

| Day | Activities | Start Date | Completion Date | References |
| --- | --- | --- | --- | --- |
| 2 | - Study the Parquet format and its benefits for querying data stored in S3.<br>- Identify the fields to retain in the project's clean dataset. | 23/11/2026 | — | [Columnar Storage Formats in Athena](https://docs.aws.amazon.com/athena/latest/ug/columnar-storage.html) |
| 3 | - Learn how to partition data by respondent and date.<br>- Outline the S3 path structure for the `clean/` data zone. | 24/11/2026 | — | [Partitioning Data in Athena](https://docs.aws.amazon.com/athena/latest/ug/partitions.html) |
| 4 | - Study the role of AWS Glue Data Catalog in Athena.<br>- Draft the table schema for the electricity dataset. | 25/11/2026 | — | [AWS Glue Data Catalog](https://docs.aws.amazon.com/glue/latest/dg/catalog-and-crawler.html) |
| 5 | **Planned:** Learn how to write Athena queries to identify peak demand hours and compare actual demand with forecasts. | 26/11/2026 (planned) | — | [Amazon Athena SELECT](https://docs.aws.amazon.com/athena/latest/ug/select.html) |
| 6 | **Planned:** Compile test cases for AWS deployment and review the corresponding workshop documentation. | 27/11/2026 (planned) | — | [Testing Lambda Functions](https://docs.aws.amazon.com/lambda/latest/dg/testing-functions.html) |

### Expected Week 8 Outcomes

- Understand how Parquet can reduce the amount of data scanned during queries.
- Propose a clean-data partitioning structure based on respondent and UTC date.
- Define a dataset schema containing the following main fields:
  - `period`: The timestamp associated with the record.
  - `respondent`: The region identifier.
  - `type`: The D, DF, or NG metric.
  - `value`: The electricity value.
  - `value_units`: The unit of measurement.
- Distinguish the responsibilities of S3, Glue Data Catalog, and Athena:
  - **S3:** Store the data.
  - **Glue Data Catalog:** Store schemas and metadata.
  - **Athena:** Query the data.
- Prepare an approach for querying peak electricity demand and forecast errors.
- List test cases for valid data, missing records, duplicate records, and pipeline reruns.

### Challenges and Next Steps

- Finalize the schema and partitioning structure before creating the Athena table.
- Test with a small data range before expanding the scope.

### Weekly Status

Data design and the AWS querying approach are being prepared. Completion dates and results will be updated after each activity is performed.