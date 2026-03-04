<div align='center'>
  <h1> 6. Messaging & Streaming </h1>
  <h2> Kinesis </h2>
</div>

# Table of Contents

- [About](#about)

---

# About

[Kinesis](https://aws.amazon.com/kinesis/) is a fully managed, serverless [streaming data](https://aws.amazon.com/what-is/streaming-data/) platform used to load and analyze real-time data streams. Kinesis provides three services: `Kinesis Data Streams`, `Kinesis Data Firehose`, and `Amazon Managed Streaming for Apache Kafka` (Amazon MSK). Use cases include real-time application monitoring, data analytics, [video streaming](https://aws.amazon.com/en/kinesis/video-streams/), and fraud detection.

- [Kinesis Data Streams](https://aws.amazon.com/kinesis/data-streams/) (data ingestion) can be used to continuously store terabytes (TB) of data. Also used as a separation layer for the speed layer and batch layer of a [Lambda architecture](https://aws.amazon.com/blogs/big-data/build-a-big-data-lambda-architecture-for-batch-and-real-time-analytics-using-amazon-redshift/).

- [Amazon Kinesis Data Firehose](https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html) (data delivery) can be used to batch, compress, transform, and encrypt data streams before loading them into data services such as Amazon S3, Amazon Redshift, Amazon OpenSearch (a fork of Elasticsearch), Splunk, and other third-party service provider endpoints (e.g., Datadog, Dynatrace, LogicMonitor, MongoDB, New Relic, Coralogix, and Elastic). Kinesis Data Firehose can be used in the batch layer of a [Lambda architecture](https://aws.amazon.com/blogs/big-data/build-a-big-data-lambda-architecture-for-batch-and-real-time-analytics-using-amazon-redshift/).

Although [Kinesis Video Streams](https://aws.amazon.com/en/kinesis/video-streams/) supports playback for live and on-demand viewing, it is primarily built for analytics and processing rather than video content delivery at scale. If one wants to build a live streaming service, one should use the following pipeline:

```bash
Raw Video Source → MediaLive (to encode/compress) → MediaPackage (to convert to a streaming format) → CloudFront (content delivery network) → End Users
```
