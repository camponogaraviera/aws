<div align='center'>
  <h1> 15. Integration & Saga Pattern </h1>
  <h2> Amazon EventBridge </h2>
</div>

# Table of Contents

- [About](#about)
- [Typical AWS Event-Driven Architecture](#typical-aws-event-driven-architecture)
- [Order Processing at Scale](#order-processing-at-scale)

---

# About

[Amazon EventBridge](https://aws.amazon.com/eventbridge/) is a service designed for building event-driven applications at scale using events. It operates with an [event bus](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-bus.html) that can [receive, filter, transform, route, and deliver](https://aws.amazon.com/eventbridge/event-bus/#:~:text=How%20it%20works-,Amazon%20EventBridge%20Event%20Bus%20is%20a%20serverless%20event%20bus%20that,%2C%20route%2C%20and%20deliver%20events.&text=The%20diagram%20shows%20how%20Amazon%20EventBridge%20Event%20Bus%20works.) events from many sources (an AWS service, a custom application, or a SaaS provider) to many targets (AWS Lambda, Step Functions, and other AWS services).

It is suitable to decouple microservices (see [Choreography-based Saga](https://github.com/camponogaraviera/full-stack-ai-sw-roadmap/blob/main/system_design/patterns.md)) by allowing different services to communicate asynchronously.

# Typical AWS Event-Driven Architecture

In AWS, event-driven systems are typically built using Lambda services as event producers and consumers, EventBridge as the event bus, SNS for notifications, and SQS for asynchronous processing. A microservice publishes an event such as `OrderCreated`, which multiple downstream services like payment, inventory, and shipping can consume independently.

```bash
User Request 
    ↓
API Gateway (Load Balancer)
    ↓
Lambda (Producer)
    ↓
DynamoDB (Database)
    ↓
EventBridge (Event Bus)
    ↓
Multiple services react
---------------------------------------
| Payment | Inventory | Shipping |
---------------------------------------
    ↓
SNS (Notification Service)
```

# Order Processing at Scale

Order processing is built using an event-driven architecture. The Order Service stores the order state in a DynamoDB table and emits an `OrderCreated` event through EventBridge. Downstream services like Payment, Inventory, Fraud Detection, and Shipping consume events asynchronously through queues. Each service updates its own database and publishes new events such as `PaymentCompleted` or `ShipmentCreated`. SQS provides buffering and retries, and SNS handles notifications. This architecture allows independent scaling, fault isolation, and high throughput.


```bash
                         Client
                           │
            API Gateway (Load Balancer..)
                           │
               Lambda (Order Service)
                           │
                DynamoDB (Order State)
                           │
                  EventBridge Bus
                           │ ┌───────────────────────┼────────────────┐
   │                       │                │
Payment Service         Inventory       Fraud
   │                       │                │
PaymentCompleted   InventoryReserved        FraudCheck
          │                │
          └─────────────┬─────────────┘
                           │
                    Shipping Service
                           │
                    ShipmentCreated
                           │
                 Notification Service
```