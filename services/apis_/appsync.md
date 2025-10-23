<div align='center'>
  <h1> 5. GraphQL & WebSocket APIs </h1>
  <h1> AWS AppSync </h1>
</div>

# Table of Contents

- [AWS AppSync](#appsync)

---

# [AWS AppSync](https://aws.amazon.com/appsync/)

AWS AppSync is a fully managed service designed to build serverless **GraphQL** and **WebSocket** APIs that can also be used to integrate multiple microservices.
Each microservice can have its own GraphQL API, and AppSync can act as a gateway to query and aggregate data from those services.
AppSync automatically scales with traffic, and there is no need to manage the infrastructure. AppSync supports microservice architectures with [Saga pattern](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/system_design_and_infrastructure/10_patterns.md).

AppSync is suitable for event-driven, subscription-style updates (real-time dashboards, collaborative editing, chat, low-frequency IoT). However, AWS AppSync CANNOT be used to build a WebSocket API for high-throughput (bytes/second or requests/second) and high-frequency updates (thousands of updates per second per connection). This requires a custom WebSocket server implemented with either uWebSockets.js, Colyseus, or Socket.IO, and deployed to ECS/EKS (via fargate) or directly on EC2 instances.

Note: [WebSockets](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/backend/api/web_sockets.md) use TCP and do not handle media (which requires UDP). For media, use [WebRTC](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/backend/api/webrtc.md).
