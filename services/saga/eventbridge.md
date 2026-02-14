<div align='center'>
  <h1> 15. Integration & Saga Pattern </h1>
  <h2> Amazon EventBridge </h2>
</div>

# Table of Contents

- [About](#about)

---

# About

[Amazon EventBridge](https://aws.amazon.com/eventbridge/) is a service designed for building event-driven applications at scale using events. It operates with an [event bus](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-bus.html) that can [receive, filter, transform, route, and deliver](https://aws.amazon.com/eventbridge/event-bus/#:~:text=How%20it%20works-,Amazon%20EventBridge%20Event%20Bus%20is%20a%20serverless%20event%20bus%20that,%2C%20route%2C%20and%20deliver%20events.&text=The%20diagram%20shows%20how%20Amazon%20EventBridge%20Event%20Bus%20works.) events from many sources (an AWS service, a custom application, or a SaaS provider) to many targets (AWS Lambda, Step Functions, and other AWS services).

It is suitable to decouple microservices (see [Choreography-based Saga](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/system_design_and_infrastructure/10_patterns.md#saga-pattern)) by allowing different services to communicate asynchronously.
