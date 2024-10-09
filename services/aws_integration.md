<div align='center'>
  <h1>Integration</h1>
</div>

# Table of Contents

- [AWS CloudFormation](#aws-cloudformation)
- [AWS EventBridge](#aws-eventbridge)
- [AWS Step Functions](#aws-step-functions)
- [AWS Glue](#AWS-Glue)

---

# [AWS CloudFormation](https://aws.amazon.com/cloudformation/)

AWS CloudFormation is an infrastructure as code (IaC) service that allows you to easily model, provision, and manage AWS and third-party resources. [You create a template that describes all the AWS resources that you want (like Amazon EC2 instances or Amazon RDS DB instances), and CloudFormation takes care of provisioning and configuring those resources for you. You don't need to individually create and configure AWS resources and figure out what's dependent on what; CloudFormation handles that.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)

---

# [AWS EventBridge](https://aws.amazon.com/eventbridge/)

AWS EventBridge is a service designed for building event-driven applications at scale using events. It operates with an [event bus](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-bus.html) that can [receive, filter, transform, route, and deliver](https://aws.amazon.com/eventbridge/event-bus/#:~:text=How%20it%20works-,Amazon%20EventBridge%20Event%20Bus%20is%20a%20serverless%20event%20bus%20that,%2C%20route%2C%20and%20deliver%20events.&text=The%20diagram%20shows%20how%20Amazon%20EventBridge%20Event%20Bus%20works.) events from many sources (an AWS service, a custom application, or a SaaS provider) to many targets (AWS Lambda, Step Functions, and other AWS services).

It is suitable to decouple microservices by allowing different services to communicate asynchronously.

---

# [AWS Step Functions](https://aws.amazon.com/step-functions/)

AWS Step Functions is a service that makes it easier to build distributed applications, automate processes, orchestrate microservices, and create data and machine learning (ML) pipelines.

It is well suited as a central serverless orchestrator to coordinate and manage complex workflows such as the [Saga Pattern](https://github.com/camponogaraviera/full-stack-roadmap/blob/dev/system_design_and_infrastructure/10_patterns.md#saga-pattern), which is used to manage distributed transactions in a microservice architecture. For example, in the Saga Pattern, a long-running transaction is split into smaller, atomic transactions, i.e., into a sequence of steps (orchestrated sagas) defined using AWS Step Functions, along with compensating actions (rollbacks) that can be triggered automatically in the event of a transaction failure.

See: [Implement the serverless saga pattern by using AWS Step Functions](https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/implement-the-serverless-saga-pattern-by-using-aws-step-functions.html).

---

# [AWS Glue](https://aws.amazon.com/glue/)

"AWS Glue is a serverless data integration service that makes it easier to discover, prepare, move, and integrate data from multiple sources for analytics, machine learning (ML), and application development." —AWS. For instance, it can be used to impart structure to data stored in an Amazon S3 data lake.
