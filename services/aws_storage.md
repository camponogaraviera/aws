<div align='center'>
  <h1>Storage</h1>
</div>

# Table of Contents

- [Amazon S3](#amazon-S3)

---

# [Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)

Amazon Simple Storage Service (S3) is a data lake, i.e., a big bucket (distributed storage system) with support for [structured, semi-structured, and unstructured](https://docs.aws.amazon.com/whitepapers/latest/building-data-lakes/amazon-s3-data-lake-storage-platform.html#:~:text=Scalability%20and%20support%20for%20structured,store%20any%20type%20of%20data.) data with [schema-on-read](https://www.dell.com/en-us/blog/schema-read-vs-schema-write-started/), mostly raw static files (images, objects, HTML, CSS, SASS, logs, CSV files, etc.). Services such as [AWS Glue](https://aws.amazon.com/glue/) can be used to impart structure to this data. Data stored in an S3 bucket can be queried using [Amazon Athena](https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage-inventory-athena-query.html) and [Amazon RedShift Spectrum](https://docs.aws.amazon.com/redshift/latest/dg/c-using-spectrum.html).

- Possible Workflow: 
  - Amazon Simple Storage (S3) -> AWS Glue -> Amazon Athena or Amazon Redshift.

## AWS S3 Pricing

S3 is a pay-as-you-go service. It has three tiers:

1. Glacier: the cheaper one, used for archiving data such as legacy data. It takes a while to read from. Replication (redundancy) can be chosen.
2. Hot: fastest response time, more data distribution across servers, but more expensive.
3. Cool: slower data retrieval.
4. Cold: takes more time to retrieve data.

First 50 TB / Month: $0.023 per GB.

## Service Level Agreement (SLA) for AWS S3

- Durability: 99.999999999% (11 9's). 
- Latency: In S3, 99.9% of the requests will be returned within 100ms.
- 99% availability implies 3.65 days of downtime in a year.
- 99.9999% will result in 30 sec. of downtime.

Note: when using Amazon S3, your data is automatically replicated.

---
