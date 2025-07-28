<div align='center'>
  <h1> Analytics </h1>
</div>

# Table of Contents

- [ETL Pipeline](#etl-pipeline)
- [Glue](#glue)
- [Athena](#athena)
- [Redshift](#redshift)

---

# ETL Pipeline 

The simplest Extract, Transform, Load (ETL) pipeline can be designed as follows:

```bash
Raw CSV file -> Amazon S3 (stores raw data) -> AWS Glue Data Catalog (Glue Crawler + Glue Database) -> Amazon S3 (stores post-processed data) -> Amazon Athena (data analysis)
```

- [Glue Crawler](https://docs.aws.amazon.com/glue/latest/dg/add-crawler.html): scans and infers schema definitions from data stored in Amazon S3. It creates or updates metadata tables in the AWS Glue Data Catalog.

- [AWS Glue Database](https://docs.aws.amazon.com/glue/latest/dg/define-database.html): a logical container in the AWS Glue Data Catalog that stores metadata (schema, table definitions, file locations in S3, etc.) inferred by the Glue Crawler or manually defined.

- [Amazon Athena](https://aws.amazon.com/athena/): a query looks up the schema and table definitions from AWS Glue Data Catalog, then reads and analyze/transform the post-processed data stored in Amazon S3.

---

# [Glue](https://aws.amazon.com/glue/)

"AWS Glue is a serverless data integration service that makes it easier to discover, prepare, move, and integrate data from multiple sources for analytics, machine learning (ML), and application development." —AWS.

For instance, it can be used to impart structure (create a schema) to data stored in an S3 bucket. It then stores that schema into an AWS Glue database.

---

# [Athena](https://aws.amazon.com/athena/)

Athena is an analytics service that provides a way to query large datasets stored in AWS S3 and other sources, including Microsoft Azure Synapse Databases, through [Amazon Athena Federated Queries](https://docs.aws.amazon.com/athena/latest/ug/connect-to-a-data-source.html), for analysis and visualization with Amazon QuickSight.

While Athena is primarily used for querying, its ability to transform data (using SQL queries to clean, filter, aggregate, and format data) directly in S3 (without loading it into a database first) makes it a valuable tool for the Transform stage in ETL. 

Use cases: 

- [Perform multi-cloud analytics using Amazon QuickSight, Amazon Athena Federated Query, and Microsoft Azure Synapse](https://aws.amazon.com/blogs/business-intelligence/perform-multi-cloud-analytics-using-amazon-quicksight-amazon-athena-federated-query-and-microsoft-azure-synapse/).
- [How to perform advanced analytics and build visualizations of your Amazon DynamoDB data by using Amazon Athena
](https://aws.amazon.com/blogs/database/how-to-perform-advanced-analytics-and-build-visualizations-of-your-amazon-dynamodb-data-by-using-amazon-athena/).

# [Redshift](https://aws.amazon.com/redshift/)

Amazon Redshift is a fully managed data warehouse ([schema-on-write](https://www.dell.com/en-us/blog/schema-read-vs-schema-write-started/)) service based on PostgreSQL. It can be used as an OLAP database with support for structured and semi-structured data. It is designed to handle large-scale data analytics workloads and is optimized for high-performance SQL queries.