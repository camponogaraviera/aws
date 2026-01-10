<div align='center'>
  <h1> 5. GraphQL & WebSocket APIs </h1>
  <h1> AWS AppSync </h1>
</div>

# Table of Contents

- [AWS AppSync](#appsync)

---

# [AWS AppSync](https://aws.amazon.com/appsync/)

AWS AppSync is a fully managed service designed to build serverless **GraphQL** APIs with `AppSync GraphQL` and **WebSocket** APIs with `AppSync Events`.

AppSync is suitable for event-driven, subscription-style updates (real-time dashboards, collaborative editing, chat, low-frequency IoT).

AppSync automatically scales with traffic, and there is no need to manage the infrastructure. AppSync supports microservice architectures with [Saga pattern](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/system_design_and_infrastructure/10_patterns.md).

Each microservice can have its own GraphQL API, and AppSync can act as a gateway to query and aggregate data from those services.

Note: [WebSockets](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/backend/api/web_sockets.md) use TCP and do not handle media (which requires UDP). For media, use [WebRTC](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/backend/api/webrtc.md).
