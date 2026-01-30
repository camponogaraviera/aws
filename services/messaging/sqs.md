<div align='center'>
  <h1> 6. Messaging & Streaming </h1>
  <h2> Amazon SQS </h2>
</div>

# Table of Contents

- [About](#about)

---

# About

[Amazon Simple Queue Service (SQS)](https://aws.amazon.com/sqs/) is a cloud-based first-in-first-out (FIFO) message queuing solution that ensures that messages are published in the order they are sent and received by the queue.

It facilitates decoupling producers/publishers (those who send messages to the queue) and consumers (those who retrieve messages from the queue) so that they can operate independently. This decoupling is crucial in microservices architectures, distributed systems, and serverless applications, enabling scalability and reliability.

It works as a buffer between producers and consumers to prevent data backlog, ensuring that messages are not lost even if one part of the system is overloaded or temporarily unavailable.

Use cases: a system that needs to process orders for fraud detection.
