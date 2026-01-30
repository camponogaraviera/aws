<div align='center'>
  <h1> 2. Backend & Deployment </h1>
  <h2> 2.5 Serverless </h2>
  <h3> AWS Lambda </h3>
</div>

# Table of Contents

- [About](#about)
- [Use Cases and Best Practices](#use-cases-and-best-practices)
- [Scaling](#scaling)
- [Deployment](#deployment)

---

# About

"Compute service that runs your code in response to events and automatically manages the compute resources." —[AWS](https://aws.amazon.com/pm/lambda).

Unlike AWS EC2, which is maintained by AWS and the user, [AWS Lambda](https://aws.amazon.com/pm/lambda) is completely serverless (maintained by AWS). This service allows users to run their functions/code snippets (in JavaScript, Java, or Python) on the cloud.

Lambda triggers are then set up to watch for events and invoke/execute a Lambda function when an event occurs. This function can return a value, write/read and modify data of services such as S3 and DynamoDB, or connect to other services such as API Gateway, AppSync, SNS, and others.

- Events: an event is what triggers the execution of a Lambda function. The event object [is a JSON-formatted document that contains data for a Lambda function to process. The Lambda runtime converts the event to an object and passes it to your function code](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-concepts.html#gettingstarted-concepts-event). Examples of events are: API Gateway requests, S3 object uploads, and DynamoDB table updates.

- [Triggers](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-concepts.html#gettingstarted-concepts-trigger): a trigger is a specific configuration or rule that defines when a Lambda function should be invoked/executed. Triggers are defined and configured within the event source service, i.e., **in the AWS service that generates the event** (e.g., S3 bucket settings, DynamoDB stream configuration, etc.). **Lambda does not poll for events; the event source service pushes events to Lambda.**

# Use Cases and Best Practices

Lambda executes API logic. It is suitable for short-lived event-driven applications within Lambda's constraints (15-minute timeout, max [10GB RAM, and 6 vCPU cores](https://aws.amazon.com/about-aws/whats-new/2021/07/aws-lambda-supports-10-gb-memory-6-vcpu-cores-bahrain-osaka-hong-kong-regions/)). For that reason, **it is an anti-pattern to set up an Express.js/Fastify API with Lambda**, since Express.js/Fastify is a framework for long-running applications that continuously listen for requests. Each invocation spins up a new instance (cold start), making Express's persistent listeners redundant. **CRUD operations should be implemented directly on Lambda**.

As a best practice, a Lambda function should be designed to do a [single task per microservice](https://docs.aws.amazon.com/whitepapers/latest/serverless-multi-tier-architectures-api-gateway-lambda/microservices-with-lambda.html). For example:

- Lambda + API Gateway HTTP/WebSockets API to handle stateless API calls (e.g., RESTful and WebSocket).
- Lambda + AppSync to define GraphQL resolvers.
- Lambda + SNS for real-time notifications.
- Lambda + S3 to store the thumbnail of an image.
- Lambda + DynamoDB to store/retrieve data.

Note: HTTP APIs from API Gateway used to build RESTful APIs are up to [71% cheaper compared to REST APIs](https://aws.amazon.com/about-aws/whats-new/2019/12/amazon-api-gateway-offers-faster-cheaper-simpler-apis-using-http-apis-preview/), also available from API Gateway, but offer only API proxy functionality.

# Scaling

["By default, Lambda provides your account with a total concurrency limit of 1,000 concurrent executions across all functions in an AWS Region."](https://docs.aws.amazon.com/lambda/latest/dg/lambda-concurrency.html)

Lambda's scalability comes from **stateless, parallelizable workloads**, not raw compute power. For example, in large-scale apps (YouTube, Facebook), Lambda would handle the **API logic**, while heavy lifting (video encoding, etc.) goes to **specialized services** (e.g., EC2, MediaConvert).

# Deployment

Connect the API Gateway HTTP API to your Lambda function to handle incoming HTTP requests (RESTful-like).
