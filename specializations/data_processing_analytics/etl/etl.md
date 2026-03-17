<div align='center'>
  <h1> 11. Data Processing & Analytics </h1>
  <h2> ETL Pipeline </h2>
</div>

# Table of Contents

- [About](#about)

---

# About

The simplest Extract, Transform, Load (ETL) pipeline can be designed as follows:

```bash
Raw CSV file -> Amazon S3 (stores raw data) -> AWS Glue Data Catalog (Glue Crawler + Glue Database) -> Amazon S3 (stores post-processed data) -> Amazon Athena (data analysis)
```

- Extract Stage:
  - Uses [Glue Crawler](https://docs.aws.amazon.com/glue/latest/dg/add-crawler.html) to scan and infer schema definitions from data stored in Amazon S3. It creates or updates metadata tables in the AWS Glue Data Catalog.
  - Uses [AWS Glue Database](https://docs.aws.amazon.com/glue/latest/dg/define-database.html), a logical container in the AWS Glue Data Catalog that stores metadata (schema, table definitions, file locations in S3, etc.) inferred by the Glue Crawler or manually defined.

- Transform Stage:
  - Uses [Amazon Athena](https://aws.amazon.com/athena/) to query the schema and table definitions from AWS Glue Data Catalog, read, and analyze/transform the post-processed data stored in Amazon S3.
