<div align='center'>
  <h1>Data Streaming & Processing</h1>
</div>

# Table of Contents

- [Amazon Kinesis](#amazon-kinesis)

---

# [Amazon Kinesis](https://aws.amazon.com/kinesis/)

Kinesis is a fully managed, serverless [streaming data](https://aws.amazon.com/what-is/streaming-data/) platform used to load and analyze real-time data streams. Kinesis provides three services: `Kinesis Data Streams`, `Kinesis Data Firehose`, and `Amazon Managed Streaming for Apache Kafka` (Amazon MSK). Use cases include real-time application monitoring, data analytics, video streaming, and fraud detection.

- [Kinesis Data Streams]() can be used to continuously store terabytes (TB) of data. Also used as a separation layer for the speed layer and batch layer of a [Lambda architecture](https://github.com/camponogaraviera/full-stack-roadmap/blob/dev/mock_design/data_pipeline.md).

- [Amazon Kinesis Data Firehose](https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html) can be used to batch, compress, transform, and encrypt data streams before loading them into data services such as Amazon S3, Amazon Redshift, Amazon OpenSearch (a fork of Elasticsearch), Splunk, and other third-party service provider endpoints including Datadog, Dynatrace, LogicMonitor, MongoDB, New Relic, Coralogix, and Elastic. Kinesis Data Firehose can be used in the batch layer of a [Lambda architecture](https://github.com/camponogaraviera/full-stack-roadmap/blob/dev/mock_design/data_pipeline.md).

Ps: kinesis is not used for content delivery. If you want to build a live streaming service you should use the following pipeline:

```bash
Raw Video Source → MediaLive (to encode/compress) → MediaPackage (to convert to a streaming format) → CloudFront (content delivery network) → End Users
```
