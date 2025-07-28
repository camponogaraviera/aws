<div align='center'>
  <h1> When to Use a Backend? </h1>
</div>

# Intro

- **No Backend Required** if the app is static and runs entirely on the client side. One can **store it on S3 and serve it via CloudFront**, or use **AWS Amplify**. Static websites means HTML/CSS/JavaScript files with no backend logic and possibly APIs called from elsewhere.

- **Backend Required** if the app: 

  - Needs short-lived processes that call APIs.  Example: saving user data to a database or fetching protected content. 
    - Use Cognito (has built-in JWT) for user authentication (sign-up/sign-in) and DynamoDB for data storage.
    - For CRUD operations, implement a serverless RESTful API with AWS Lambda and API Gateway (HTTP API). Alternatively, implement a GraphQL API with AppSync to avoid over-fetching and under-fetching data.

  - Needs low throughput, low-frequency, and real-time synchronization. Example: a chat app with 1-10k concurrent users and a delay of 100ms-2s.
    - For low-frequency, real-time communication (send/receive messages), and events (typing receipt, presence), implement a WebSocket API with either AWS API Gateway WebSockets or AWS AppSync.
    - For CRUD operations (e.g., delete a chat, create a group, etc.), implement a serverless RESTful or GraphQL API. WebSockets can also be used, but it is not recommended unless all operations are designed around it. A RESTful or GraphQL API is also suitable for uploading media (images and videos) via HTTP, as well as for analytics dashboard, and bootstrapping, i.e., for fetching profile, group list, etc., without keeping the WebSocket connection open.
    - Use [AppSync subscriptions](https://docs.aws.amazon.com/appsync/latest/devguide/aws-appsync-real-time-data.html) for real-time fan-out (live application updates, push notifications, etc.).
      
  - Needs either long-running processes (e.g., custom video processing outside MediaConvert, audio/video call, LLM inference, etc.), or 10k+ concurrent connections (e.g., chat apps, multiplayer games, etc.), or low-latency/high-frequency updates (e.g., multiplayer games that sync at 20 to 120Hz with < 50ms delay, audio/video calls, etc.), or high-throughput (e.g., video uploading/downloading service, video calls, etc.).
    - For long-running processes that exceed AWS Lambda's 15-minute timeout or require greater control over execution, it is better to implement a server-based RESTful API (e.g., using Express.js or Fastify) running on a container (e.g., ECS with EC2 instances). AWS Lambda can still be used to initiate or coordinate these jobs, but it is not suitable for executing them directly if they are long-running.
    - For 10k+ long-lived concurrent connections, high-frequency updates, and real-time communication, build a custom WebSocket server using either uWebSockets.js, Colyseus, or Socket.IO. 
    - For high-throughput, use [Elastic Load Balancer (ELB)](https://aws.amazon.com/elasticloadbalancing/features/) to route users to WebSocket servers running on containers (ECS). One such kind of ELB is the [Network Load Balancer (NLB)](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html) that supports TCP-level forwarding required by WebSocket connections.
    - For real-time, audio/video communication, use Amazon Chime. It has a WebRTC under the hood and includes built-in network address translation (NAT) using the ICE framework, without the need to set up STUN or TURN servers.
    - Deploy to EC2 instances within an ECS container, or directly on EC2, for scalable and stateless APIs.

## Notes

- The frontend can always be hosted (stored on S3 and served through CloudFront) using Amplify. The backend of lightweight apps can be deployed with Amplify, which uses **CloudFormation** under the hood to integrate different backend services. However, the backend of long-running apps should be deployed on ECS/EKS or directly on EC2 instances.

- AWS API Gateway and Lambda are not suitable for building RESTful APIs that involve long-running tasks, because of their timeout constraints: [~29 seconds for API Gateway](https://aws.amazon.com/tw/about-aws/whats-new/2024/06/amazon-api-gateway-integration-timeout-limit-29-seconds/), and 15 minutes for Lambda.

- API Gateway WebSockets does not offer high-throughput connections, has a Max of 2 hours duration per connection (not persistent), and a default (can be extended) limit of 10k concurrent connections per account, per region.

- Fan-In: number of components that call into a service.

- Fan-Out: number of outgoing requests or connections a service/component makes to other components to fulfill a single task or request.

- Frequency: how often data is sent. Typically measured in updates per second (Hz).

- Throughput: can refer to either data throughput (bytes/second) or request throughput (requests/second).

- STUN (Session Traversal Utilities for NAT) and TURN (Traversal Using Relays around NAT) are protocols used in real-time communication over the internet, particularly in WebRTC (Web Real-Time Communication) and similar technologies that require peer-to-peer connectivity (e.g., video calls, file sharing).
