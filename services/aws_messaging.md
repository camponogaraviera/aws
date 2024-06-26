<div align='center'>
  <h1>Messaging</h1>
</div>

# [Amazon SES](https://aws.amazon.com/ses/)

Amazon Simple Email Service (SES) allows sending high-volume email notifications without relying on an on-premises Simple Mail Transfer Protocol (SMTP), instead, it uses the Amazon SES API or SMTP interface.

---

# [Amazon SNS](https://aws.amazon.com/sns/)

Amazon Simple Notification Service (SNS) is a messaging service used to publish event changes that applications can subscribe to.

---

# [Amazon SQS](https://aws.amazon.com/sqs/)

Amazon SQS is a cloud-based first-in-first-out (FIFO) message queuing solution that ensures that messages are published in the order they are sent and received by the queue.

It facilitates decoupling producers/publishers (those who send messages to the queue) and consumers (those who retrieve messages from the queue) so that they can operate independently. This decoupling is crucial in microservices architectures, distributed systems, and serverless applications, as it enables scalability and reliability.

It works as a buffer between producers and consumers to prevent data backlog, ensuring that messages are not lost even if one part of the system is overloaded or temporarily unavailable.

Use cases: a system that needs to process orders for fraud detection.
