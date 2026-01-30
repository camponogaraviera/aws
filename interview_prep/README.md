<div align='center'>
  <h1> AWS Roadmap </h1>
  <h2> Interview Questions </h2>
</div>

# 1) Which AWS services should be used to implement user authentication (sign-up/sign-in) and authorization?

**Answer**:

- Use `AWS Cognito` (has built-in JWT) for user authentication and `IAM` for authorization.

---

# 2) Which AWS services should be used to save user data to a database and fetch content?

**Answer**:

- Use `AWS S3` to store static files (images, videos, etc.) and `DynamoDB` to store metadata (links to S3 objects).
- Use `AWS Cognito` to manage user authentication and integrate it with `IAM` for authorization.
- Use [API Gateway](https://aws.amazon.com/api-gateway/) + [AWS Lambda](https://aws.amazon.com/pm/lambda) to implement a serverless RESTful API that can handle CRUD operations and fetching of protected content via HTTP. Alternatively, use AppSync to implement a GraphQL API to avoid over-fetching and under-fetching data.

---

# 3) Which AWS services should be used to design a chat app with 1-10k concurrent users, low throughput (10 MB/second), and near-real-time synchronization?

**Answer**:

- Use `AWS API Gateway WebSockets` or `AWS AppSync` to implement a WebSocket API for near-real-time communication (send/receive messages), and events (typing receipt, presence).
- Use `AWS AppSync` to implement a GraphQL API that can handle CRUD operations (e.g., delete a chat, create a group, fetch profile, etc.).
- Use [AppSync subscriptions](https://docs.aws.amazon.com/appsync/latest/devguide/aws-appsync-real-time-data.html) for real-time fan-out (live application updates, push notifications, etc.)

- For data uploading, downloading, and deletion of static media files (images and videos), use `AWS API Gateway + Lambda` to wrap S3 operations.
  - To get an upload URL, the Client sends a GET request to an API Gateway endpoint that invokes a Lambda function.
  - The Lambda function generates a pre-signed S3 URL and returns it to the client.
  - The Client then directly uploads/downloads/deletes media to/from the S3 bucket via an HTTP POST/GET/Delete request using that URL.

---

# 4) Which AWS services should be used for general-purpose, long-running compute that exceed AWS Lambda's 15-minute timeout (e.g., video processing, ML training, and inference)?

**Answer**:

- Use [Amazon EC2](https://aws.amazon.com/ec2) instances to deploy custom long-running functions.

- Fargate is not suitable for LLM training because it does not support GPU instances. EC2 instances must be manually configured instead.

- AWS Lambda can still be used to initiate or coordinate these jobs, but it is not suitable for executing them directly if they are long-running.

---

# 5) Which AWS services should be used for batch-style long-running workloads (e.g., simulation, video processing, and ML training jobs)?

**Answer**:

- Use [AWS Batch](https://aws.amazon.com/batch/) for custom long-running simulations (e.g., robotics, autonomous vehicles), machine learning training/inference, and custom video transcoding as an alternative to MediaConvert.

- Use [Amazon SageMaker](https://aws.amazon.com/sagemaker) for machine learning training job and inference.

---

# 6) Which AWS services should be used to design an app that requires 1M+ long-lived concurrent connections (e.g., chat apps, multiplayer games, etc.) and high throughput?

**Answer:**

- For 1M+ long-lived concurrent connections and high throughput (millions of requests per second), set up a [Network Load Balancer (NLB)](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html) that operates at the transport layer 4 (TCP/UDP) to distribute TCP traffic to backend workloads (such as containers running on EC2 instances with ECS/EKS as the orchestration layer), then possibly an [Application Load Balancer (ALB)](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html) if application Layer 7 features are required further downstream (e.g., HTTP routing and WAF).

- For large-scale workloads requiring millions of concurrent connections, configure the Network Load Balancer to use the [IP target type](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/load-balancer-target-groups.html#target-type) instead of the [instance target type](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/load-balancer-target-groups.html#target-type). This enables more granular load balancing across containerized services or multiple Elastic Network Interface (ENI) backends, improving scalability and connection distribution.
- For real-time communication, implement a custom WebSocket API with either `uWebSockets.js`, `Colyseus`, or `Socket.IO`, instead of using [API Gateway WebSocket API](https://docs.aws.amazon.com/zh_tw/apigateway/latest/developerguide/apigateway-websocket-api.html) (see the [notes section](#notes)).

---

# 7) Which AWS services should be used to design a multiplayer game app that requires low latency (< 50ms delay), high frequency updates (20 to 120Hz), and persistent connections?

**Answer:**

- Build the game server, which is a project containing many source files, including the authoritative game loop that maintains world state and processes player input. For multiplayer features, implement a persistent real-time network layer (most commonly WebSocket) inside the game server using either `uWebSockets.js`, `Colyseus`, or `Socket.IO`.

- Containerize the entire game server application, push the Docker image to Amazon ECR, and run it on an always-on Amazon EC2 instance backed by ECS/EKS as the orchestration layer for scalability.

- Stateful Services (persistent demand):
  - Use a stateful TCP socket to connect clients directly to stateful game servers with long-running processes, such as world exploration and multiplayer interactivity. The player keeps the same long-lived (persistent) TCP connection open. Amazon EC2 instances keep in-memory game state, and maintain persistent connections.

- Stateless Services (on-demand):
  - The communication API for non-realtime workload (authentication/login, player profile, leaderboards, game history, updating inventory/stats, searching for games, etc.) can be a serverless `RESTful API` implemented with [API Gateway](https://aws.amazon.com/api-gateway/) + [AWS Lambda](https://aws.amazon.com/pm/lambda) + [Elastic Load Balancer](). Easier to scale horizontally since it is a stateless service.

- Alternatively, use [Amazon GameLift](https://aws.amazon.com/gamelift/).

- Check [this Amazon Guide](https://aws.amazon.com/blogs/gametech/stateful-or-stateless/).

---

# 8) Which AWS services should be used to design a real-time video conferencing app that requires low latency, high throughput (high data volume, such as video + audio streams), and persistent connections?

**Answer:**

- For real-time, audio/video communication, use [Amazon Chime](https://aws.amazon.com/chime/). The SDK provides a WebRTC under the hood (which maintains a persistent connection), includes built-in network address translation (NAT) using the ICE framework, and does not require users to manually set up STUN or TURN servers.
- The communication API (create meeting, add/delete attendees, etc.) can be a serverless `RESTful API` implemented with [API Gateway](https://aws.amazon.com/api-gateway/) + [AWS Lambda](https://aws.amazon.com/pm/lambda).
- The frontend can be hosted on Amplify, while the backend can be deployed on Elastic Beanstalk (monolithic) or Fargate through ECS/EKS (microservices).

---

# 9) Which AWS services should be used to implement a priority queue for a hospital reservation system?

**Answer:**

- If strict priority ordering is essential (e.g., emergency patients processed first), use [Amazon MQ](https://aws.amazon.com/amazon-mq/) with [RabbitMQ](https://www.rabbitmq.com/) message broker engine.

- If approximate priority handling (via multiple queues) is acceptable and you want simplicity + serverless scaling, [Amazon SQS](https://aws.amazon.com/sqs/) works fine.

- The communication API can be a serverless `RESTful API` implemented with [API Gateway](https://aws.amazon.com/api-gateway/) + [AWS Lambda](https://aws.amazon.com/pm/lambda).

# Notes

- The frontend can always be hosted (stored on S3 and served through CloudFront) using Amplify. The backend of lightweight apps can be deployed with Amplify, which uses **CloudFormation** under the hood to integrate different backend services. However, the backend of long-running apps should be deployed on EC2 instances directly or via Fargate.

- If a stateless request-response service is required, API Gateway + Lambda works fine for building a serverless RESTful API. However, this setup is not a suitable choice for building APIs that require low-latency (Lambda has cold start) and long-running workloads, because of their timeout constraints: [~29 seconds timeout for API Gateway](https://aws.amazon.com/tw/about-aws/whats-new/2024/06/amazon-api-gateway-integration-timeout-limit-29-seconds/), and [15 minutes timeout for Lambda](https://docs.aws.amazon.com/lambda/latest/dg/configuration-timeout.html). In such cases, a RESTful API built with Express.js running on an EC2 instance is a better architectural fit.

- While API Gateway does not enforce a quota on concurrent connections, API Gateway WebSockets has a [maximum connection duration (lifetime) of 2 hours](https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-execution-service-websocket-limits-table.html). For services that require low-latency, persistent connections, and stateful, bidirectional communication, ALB/NLB + a custom WebSocket server running on an EC2 instance is a better architectural fit.

- NLB is protocol agnostic, i.e., it does not interpret, parse, or modify application-layer protocols, it only forwards raw transport-layer traffic. It only looks at source/destination IP and port and does not care if bytes are HTTP requests, WebSocket frames, TLS, or raw binary.

- Fan-In: Number of components that call into a service.

- Fan-Out: Number of outgoing requests or connections a service/component makes to other components to fulfill a single task or request.

- Frequency: How often data is sent. Typically measured in updates per second (Hz), per connection.

- Throughput: Can refer to either data throughput (bytes/second) or request throughput (requests/second).

- STUN (Session Traversal Utilities for NAT) and TURN (Traversal Using Relays around NAT) are protocols used in real-time communication over the internet, particularly in WebRTC (Web Real-Time Communication) and similar technologies that require peer-to-peer connectivity (e.g., video calls, file sharing).
