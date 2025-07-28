<div align='center'>
  <h1> Messaging & Streaming </h1>
</div>

# Table of Contents

- [SES](#ses)
- [SNS](#sns)
- [SQS](#sqs)
- [Kinesis](#kinesis)

# [SES](https://aws.amazon.com/ses/)

Amazon Simple Email Service (SES) allows sending high-volume email notifications without relying on an on-premises Simple Mail Transfer Protocol (SMTP), instead, it uses the Amazon SES API or SMTP interface.

---

# [SNS](https://aws.amazon.com/sns/)

Amazon Simple Notification Service (SNS) is a messaging service used to publish event changes that applications can subscribe to.

---

# [SQS](https://aws.amazon.com/sqs/)

Amazon SQS is a cloud-based first-in-first-out (FIFO) message queuing solution that ensures that messages are published in the order they are sent and received by the queue.

It facilitates decoupling producers/publishers (those who send messages to the queue) and consumers (those who retrieve messages from the queue) so that they can operate independently. This decoupling is crucial in microservices architectures, distributed systems, and serverless applications, enabling scalability and reliability.

It works as a buffer between producers and consumers to prevent data backlog, ensuring that messages are not lost even if one part of the system is overloaded or temporarily unavailable.

Use cases: a system that needs to process orders for fraud detection.

---

# [Kinesis](https://aws.amazon.com/kinesis/)

Kinesis is a fully managed, serverless [streaming data](https://aws.amazon.com/what-is/streaming-data/) platform used to load and analyze real-time data streams. Kinesis provides three services: `Kinesis Data Streams`, `Kinesis Data Firehose`, and `Amazon Managed Streaming for Apache Kafka` (Amazon MSK). Use cases include real-time application monitoring, data analytics, [video streaming](https://aws.amazon.com/en/kinesis/video-streams/), and fraud detection.

- [Kinesis Data Streams](https://aws.amazon.com/kinesis/data-streams/) (data ingestion) can be used to continuously store terabytes (TB) of data. Also used as a separation layer for the speed layer and batch layer of a [Lambda architecture](https://aws.amazon.com/blogs/big-data/build-a-big-data-lambda-architecture-for-batch-and-real-time-analytics-using-amazon-redshift/).

- [Amazon Kinesis Data Firehose](https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html) (data delivery) can be used to batch, compress, transform, and encrypt data streams before loading them into data services such as Amazon S3, Amazon Redshift, Amazon OpenSearch (a fork of Elasticsearch), Splunk, and other third-party service provider endpoints (e.g., Datadog, Dynatrace, LogicMonitor, MongoDB, New Relic, Coralogix, and Elastic). Kinesis Data Firehose can be used in the batch layer of a [Lambda architecture](https://aws.amazon.com/blogs/big-data/build-a-big-data-lambda-architecture-for-batch-and-real-time-analytics-using-amazon-redshift/).

Although [Kinesis Video Streams](https://aws.amazon.com/en/kinesis/video-streams/) supports playback for live and on-demand viewing, it is primarily built for analytics and processing rather than video content delivery at scale. If one wants to build a live streaming service, one should use the following pipeline:

```bash
Raw Video Source → MediaLive (to encode/compress) → MediaPackage (to convert to a streaming format) → CloudFront (content delivery network) → End Users
```
