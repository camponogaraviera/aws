<div align='center'>
  <h1>ETL (Extract, Transform, Load) Framework</h1>
</div>

# Table of Contents

- [ETL Pipeline](#etl-pipeline)
- [Amazon Kinesis](#amazon-kinesis)
- [Amazon Athena](#amazon-athena)
- [Amazon Redshift](#amazon-redshift)
- [AWS Glue](#aws-glue)

---

# ETL Pipeline

The simplest ETL pipeline can be designed as follows:

```bash
Raw CSV file -> Amazon S3 (stores raw data) -> AWS Glue Data Catalog (Glue Crawler + Glue Database) -> Amazon S3 (stores post-processed data) -> Amazon Athena (data analysis)
```

- [AWS Glue Crawler](https://docs.aws.amazon.com/glue/latest/dg/add-crawler.html): scans and infers schema definitions from data stored in Amazon S3. It creates or updates metadata tables in the AWS Glue Data Catalog.

- [AWS Glue Database](https://docs.aws.amazon.com/glue/latest/dg/define-database.html): a logical container in the AWS Glue Data Catalog that stores metadata (schema, table definitions, file locations in S3, etc.) inferred by the Glue Crawler or manually defined.

- [Amazon Athena](https://aws.amazon.com/athena/): a query looks up the schema and table definitions from AWS Glue Data Catalog, then reads and processes the post-processed data stored in Amazon S3.

---

# [Amazon Kinesis](https://aws.amazon.com/kinesis/)

Kinesis is a fully managed, serverless [streaming data](https://aws.amazon.com/what-is/streaming-data/) platform used to load and analyze real-time data streams. Kinesis provides three services: `Kinesis Data Streams`, `Kinesis Data Firehose`, and `Amazon Managed Streaming for Apache Kafka` (Amazon MSK). Use cases include real-time application monitoring, data analytics, [video streaming](https://aws.amazon.com/en/kinesis/video-streams/), and fraud detection.

- [Kinesis Data Streams](https://aws.amazon.com/kinesis/data-streams/) (data ingestion) can be used to continuously store terabytes (TB) of data. Also used as a separation layer for the speed layer and batch layer of a [Lambda architecture](https://github.com/camponogaraviera/full-stack-roadmap/blob/dev/mock_design/data_pipeline.md).

- [Amazon Kinesis Data Firehose](https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html) (data delivery) can be used to batch, compress, transform, and encrypt data streams before loading them into data services such as Amazon S3, Amazon Redshift, Amazon OpenSearch (a fork of Elasticsearch), Splunk, and other third-party service provider endpoints (e.g., Datadog, Dynatrace, LogicMonitor, MongoDB, New Relic, Coralogix, and Elastic). Kinesis Data Firehose can be used in the batch layer of a [Lambda architecture](https://github.com/camponogaraviera/full-stack-roadmap/blob/dev/mock_design/data_pipeline.md).

Ps: Although [Kinesis Video Streams](https://aws.amazon.com/en/kinesis/video-streams/) supports playback for live and on-demand viewing, it is primarily built for analytics and processing rather than video content delivery at scale. If you want to build a live streaming service you should use the following pipeline:

```bash
Raw Video Source → MediaLive (to encode/compress) → MediaPackage (to convert to a streaming format) → CloudFront (content delivery network) → End Users
```

---

# [Amazon Athena](https://aws.amazon.com/athena/)

Athena is an analytics service that provides a way to query large datasets stored in AWS S3 and other sources, including Microsoft Azure Synapse Databases, through [Amazon Athena Federated Queries](https://docs.aws.amazon.com/athena/latest/ug/connect-to-a-data-source.html), for analysis and visualization with Amazon QuickSight.

While Athena itself is primarily used for querying, its ability to transform data (using SQL queries to clean, filter, aggregate, and format data) directly in S3 (without loading it into a database first) makes it a valuable tool for the Transform stage in ETL. 

Use cases: 

- [Perform multi-cloud analytics using Amazon QuickSight, Amazon Athena Federated Query, and Microsoft Azure Synapse](https://aws.amazon.com/blogs/business-intelligence/perform-multi-cloud-analytics-using-amazon-quicksight-amazon-athena-federated-query-and-microsoft-azure-synapse/).
- [How to perform advanced analytics and build visualizations of your Amazon DynamoDB data by using Amazon Athena
](https://aws.amazon.com/blogs/database/how-to-perform-advanced-analytics-and-build-visualizations-of-your-amazon-dynamodb-data-by-using-amazon-athena/).

---

# [Amazon Redshift](https://aws.amazon.com/redshift/)

Amazon Redshift is a fully managed data warehouse ([schema-on-write](https://www.dell.com/en-us/blog/schema-read-vs-schema-write-started/)) service based in PostgreSQL. It can be used as an OLAP database with support for structured and semi-structured data. It is designed to handle large-scale data analytics workloads and is optimized for high-performance SQL queries.

---

# [AWS Glue](https://aws.amazon.com/glue/)

"AWS Glue is a serverless data integration service that makes it easier to discover, prepare, move, and integrate data from multiple sources for analytics, machine learning (ML), and application development." —AWS.

For instance, it can be used to impart structure (create a schema) to data stored in an S3 bucket. It then stores that schema into an AWS Glue database.
