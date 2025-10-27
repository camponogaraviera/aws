<div align='center'>
  <h1> AWS Roadmap </h1>
  <h1> Interview Questions </h1>
</div>

# 1) Which AWS services should be used to implement user authentication (sign-up/sign-in) and authorization?

**Answer**:

- Use `AWS Cognito` (has built-in JWT) for user authentication and `IAM` for authorization.

---

# 2) Which AWS services should be used to save user data to a database and fetch protected content?

**Answer**:

- Use `AWS S3` to store static files (images, videos, etc.) and `DynamoDB` to store metadata (links to S3 objects).
- Use `AWS Cognito` to manage user authentication and integrate it with `IAM` for authorization.
- Use [API Gateway](https://aws.amazon.com/api-gateway/) + [AWS Lambda](https://aws.amazon.com/pm/lambda) (HTTP API) to implement a RESTful API that can handle CRUD operations for fetching protected content. Alternatively, use AppSync to implement a GraphQL API to avoid over-fetching and under-fetching data.

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

# 6) Which AWS services should be used to design an app that requires 1M+ concurrent connections (e.g., chat apps, multiplayer games, etc.) and high throughput?

**Answer:**

- For 1M+ long-lived concurrent connections and high throughput (millions of requests per second), set up a [Network Load Balancer (NLB)](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html) to distribute TCP traffic to backend workloads (such as containers running in ECS or EKS, or applications on EC2 instances). An [Application Load Balancer (ALB)](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html) also supports WebSockets and adds Layer 7 features like routing and WAF, but NLB generally scales better for extreme concurrency and throughput.

- For large-scale workloads requiring millions of concurrent connections, configure the Network Load Balancer to use the [IP target type](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/load-balancer-target-groups.html#target-type) instead of the [instance target type](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/load-balancer-target-groups.html#target-type). This enables more granular load balancing across containerized services or multiple Elastic Network Interface (ENI) backends, improving scalability and connection distribution.
  
- If using WebSocket, implement a custom WebSocket API with either `uWebSockets.js`, `Colyseus`, or `Socket.IO`, instead of using the [API Gateway WebSocket API](https://docs.aws.amazon.com/zh_tw/apigateway/latest/developerguide/apigateway-websocket-api.html) (see the [notes section](#notes)).

---

# 7) Which AWS services should be used to design a multiplayer game app that requires low latency (< 50ms delay), high frequency updates (20 to 120Hz), and persistent connections? 

**Answer:**

- Use [Amazon GameLift](https://aws.amazon.com/gamelift/) to handle the real-time gameplay loop with persistent connections. Alternatively, build a custom WebSocket server using either `uWebSockets.js`, `Colyseus`, or `Socket.IO`.

- The communication API (for non-game logic: authentication, player profile, leaderboards, game history, inventory, etc.) can be a serverless `RESTful API` implemented with [API Gateway](https://aws.amazon.com/api-gateway/) + [AWS Lambda](https://aws.amazon.com/pm/lambda).
 
- If using a custom WebSocket, deploy the containerized application directly on stateless servers/nodes (e.g., `EC2 instances`), or use [AWS Fargate](https://aws.amazon.com/fargate/) to run containers managed by ECS/EKS.

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

- The frontend can always be hosted (stored on S3 and served through CloudFront) using Amplify. The backend of lightweight apps can be deployed with Amplify, which uses **CloudFormation** under the hood to integrate different backend services. However, the backend of long-running apps should be deployed on EC2 instances (directly or via Fargate).

- AWS API Gateway + Lambda is not a suitable choice for building APIs that require persistent connections (stateful servers), because of their timeout constraints: [~29 seconds timeout for API Gateway](https://aws.amazon.com/tw/about-aws/whats-new/2024/06/amazon-api-gateway-integration-timeout-limit-29-seconds/), and [15 minutes timeout for AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/configuration-timeout.html).

- API Gateway WebSockets does not offer high-throughput connections, has a Max of 2 hours duration per connection (not persistent), and a default (can be extended) limit of 10k concurrent connections per account, per region.

- If you just need a stateless request/response, API Gateway + Lambda works great.

- If you need persistent connections, low-latency stateful communication, or streaming, Express.js (or another long-running server) is a suitable choice.

- Fan-In: number of components that call into a service.

- Fan-Out: number of outgoing requests or connections a service/component makes to other components to fulfill a single task or request.

- Frequency: how often data is sent. Typically measured in updates per second (Hz) per connection.

- Throughput: can refer to either data throughput (bytes/second) or request throughput (requests/second).

- STUN (Session Traversal Utilities for NAT) and TURN (Traversal Using Relays around NAT) are protocols used in real-time communication over the internet, particularly in WebRTC (Web Real-Time Communication) and similar technologies that require peer-to-peer connectivity (e.g., video calls, file sharing).
