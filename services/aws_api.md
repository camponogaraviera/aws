<div align='center'>
  <h1> GraphQL & WebSocket APIs </h1>
</div>

# Table of Contents

- [AppSync](#appsync)
- [GraphQL with AppSync and DynamoDB](#graphql-with-appsync-and-dynamoDB)

# [AppSync](https://aws.amazon.com/appsync/)

AppSync is a fully managed service designed to build serverless **GraphQL** and **WebSocket** APIs that can also be used to integrate multiple microservices. 
Each microservice can have its own GraphQL API, and AppSync can act as a gateway to query and aggregate data from those services. 
AppSync automatically scales with traffic, and there is no need to manage the infrastructure.

AppSync supports microservice architectures with [Saga pattern](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/system_design_and_infrastructure/10_patterns.md).

Note: [WebSockets](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/backend/api/web_sockets.md) use TCP and do not handle media (which requires UDP). For media, use [WebRTC](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/backend/api/webrtc.md).

# GraphQL with AppSync and DynamoDB

When using AppSync and DynamoDB to design your GraphQL API, the GraphQL [Schema and resolvers](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/backend/api/grahql.md#graphql-syntax) need to align with the DynamoDB access patterns.

- Single-table design in DynamoDB with GraphQL:
  - Improved performance and lower latency.
  - More complex and less flexible.

- Multi-table design in DynamoDB with GraphQL:
  - Less performant.
  - Less complex and more flexible.

# References

[1] [DynamoDB design patterns with GraphQL APIs and AppSync - AWS Online Tech Talks](https://youtu.be/HkbeKhKjEDU?feature=shared)
