<div align='center'>
  <h1> 8. Storage (data lakes) </h1>
  <h2> Amazon S3 </h2>
</div>

# Table of Contents

- [About](#about)
- [S3 Storage Pricing](#s3-storage-pricing)
- [S3 Data Transfer Pricing](#s3-data-transfer-pricing)
- [Service Level Agreement (SLA) for AWS S3](#service-level-agreement-sla-for-aws-s3)

# About

[Amazon Simple Storage Service (S3)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html) is a data lake, i.e., a big bucket (distributed storage system) with support for [structured, semi-structured, and unstructured](https://docs.aws.amazon.com/whitepapers/latest/building-data-lakes/amazon-s3-data-lake-storage-platform.html#:~:text=Scalability%20and%20support%20for%20structured,store%20any%20type%20of%20data.) data with [schema-on-read](https://github.com/camponogaraviera/full-stack-ai-sw-roadmap/blob/main/backend/database/core/01_lake_vs_warehouse.md), mostly raw static files (images, objects, HTML, CSS, SASS, logs, CSV files, etc.). Services such as [AWS Glue](https://aws.amazon.com/glue/) can be used to impart structure to this data. Data stored in an S3 bucket can be queried using [Amazon Athena](https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage-inventory-athena-query.html) and [Amazon RedShift Spectrum](https://docs.aws.amazon.com/redshift/latest/dg/c-using-spectrum.html).

Note: Amazon S3 automatically scales for massive traffic and replicates data across multiple availability zones. 

Examples:

```bash
Website Traffic:
User -> CloudFront (CDN for caching content at edge locations) -> S3 (storage of static files: JS, HTML, CSS, images, logs).

Log Storage:
CloudFront -> Access Logs -> S3 (log bucket).

Log Analytics:
AWS Glue Data Catalog (defines table schema) -> Amazon Athena (SQL query on log files in S3).

Newsletter Workflow:
User -> CloudFront (CDN) -> S3 (serves website) -> API Gateway (form submission endpoint) -> Lambda (backend logic) -> Email API or Database (email storage).
```

---

# S3 Storage Pricing

S3 is a pay-as-you-go service. It has the following storage classes:

1. S3 Standard:
2. S3 Intelligent-Tiering:
3. Amazon S3 Standard-Infrequent Access (S3 Standard-IA):
4. Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA):
5. S3 Glacier Instant Retrieval:
6. S3 Glacier Flexible Retrieval (formerly S3 Glacier):
7. Amazon S3 Glacier Deep Archive:
8. S3 Express One Zone:

| Monthly Data Storage (S3 Standard) | Price per GB (Taipei) |
| ---------------------------------  | --------------------- |
| First 5 GB  / Month                | Free                  |
| First 50 TB / Month                | $0.0225 / GB          |
| Next 450 TB / Month                | $0.0216 / GB          |
| Over 500 TB / Month                | $0.0207 / GB          |

---

# S3 Data Transfer Pricing

| Transfer Direction                      | Cost                                 |
| --------------------------------------  | ------------------------------------ |
| **S3 -> CloudFront**                    | Free                                 |
| **S3 -> Internet (without CloudFront)** | 💰 Charged (S3 egress rates)         |
| **CloudFront -> Internet (end-users)**  | 💰 Charged (CloudFront egress rates) |

- From AWS S3 to the Internet (Typical Egress):

|  S3 to Internet (Taipei)  |  Price per GB  |
| --------------------------| -------------- |
| First 100 GB / Month      | Free           |
| First 10 TB / Month       | $0.1083 / GB   |
| Next 40 TB / Month        | $0.08455 / GB  |
| Next 100 TB / Month       | $0.0817 / GB   |
| Over 150 TB / Month       | $0.0798 / GB   |

---

# Service Level Agreement (SLA) for AWS S3

- Durability: 99.999999999% (11 9's).
- Latency: In S3, 99.9% of the requests will be returned within 100ms.
- 99% availability implies 3.65 days of downtime in a year.
- 99.9999% will result in 30 sec. of downtime.

# References

[1] https://aws.amazon.com/s3/pricing/
