<div align='center'>
  <h1> 8. Storage (data lakes) </h1>
  <h2> Amazon S3 </h2>
</div>

# Table of Contents

- [About](#about)
- Amazon S3 Pricing
- Service Level Agreement (SLA) for AWS S3

---

# About

[Amazon Simple Storage Service (S3)](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html) is a data lake, i.e., a big bucket (distributed storage system) with support for [structured, semi-structured, and unstructured](https://docs.aws.amazon.com/whitepapers/latest/building-data-lakes/amazon-s3-data-lake-storage-platform.html#:~:text=Scalability%20and%20support%20for%20structured,store%20any%20type%20of%20data.) data with [schema-on-read](https://www.dell.com/en-us/blog/schema-read-vs-schema-write-started/), mostly raw static files (images, objects, HTML, CSS, SASS, logs, CSV files, etc.). Services such as [AWS Glue](https://aws.amazon.com/glue/) can be used to impart structure to this data. Data stored in an S3 bucket can be queried using [Amazon Athena](https://docs.aws.amazon.com/AmazonS3/latest/userguide/storage-inventory-athena-query.html) and [Amazon RedShift Spectrum](https://docs.aws.amazon.com/redshift/latest/dg/c-using-spectrum.html).

- Possible Workflow:
  - Amazon Simple Storage (S3) -> AWS Glue -> Amazon Athena or Amazon Redshift.

# S3 Storage Pricing

S3 is a pay-as-you-go service. It has three tiers:

1. Glacier: the cheaper one, used for archiving data such as legacy data. It takes a while to read from. Replication (redundancy) can be chosen.
2. Hot: fastest response time, more data distribution across servers, but more expensive.
3. Cool: slower data retrieval.
4. Cold: takes more time to retrieve data.

First 50 TB / Month: $0.023 per GB.

# S3 Data Transfer Pricing

| Transfer Direction                     | Cost                                 |
| -------------------------------------- | ------------------------------------ |
| **S3 → CloudFront**                    | ✅ Free                              |
| **S3 → Internet (without CloudFront)** | 💰 Charged (S3 egress rates)         |
| **CloudFront → Internet (end-users)**  | 💰 Charged (CloudFront egress rates) |

- From AWS S3 to the Internet (Typical Egress):

| Monthly Outbound Data (per Region) | Price per GB |
| ---------------------------------- | ------------ |
| First 100 GB                       | Free         |
| Up to 10 TB                        | \$0.09 / GB  |
| Next 40 TB                         | \$0.085 / GB |
| Next 100 TB                        | \$0.07 / GB  |
| Over 150 TB                        | \$0.05 / GB  |

## Service Level Agreement (SLA) for AWS S3

- Durability: 99.999999999% (11 9's).
- Latency: In S3, 99.9% of the requests will be returned within 100ms.
- 99% availability implies 3.65 days of downtime in a year.
- 99.9999% will result in 30 sec. of downtime.

Note: when using Amazon S3, your data is automatically replicated.
