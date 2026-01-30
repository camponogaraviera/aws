<div align='center'>
  <h1> 15. Integration & Saga Pattern </h1>
  <h2> AWS Step Functions </h2>
</div>

# Table of Contents

- [About](#about)

---

# About

[AWS Step Functions](https://aws.amazon.com/step-functions/) is a service that makes it easier to build distributed applications, automate processes, orchestrate microservices, and create data and machine learning (ML) pipelines.

It is well-suited as a central serverless orchestrator to coordinate and manage complex workflows such as the [Saga Pattern](https://github.com/camponogaraviera/full-stack-roadmap/blob/main/system_design_and_infrastructure/10_patterns.md#saga-pattern), which is used to manage distributed transactions in a microservice architecture. For example, in the Saga Pattern, a long-running transaction is split into smaller, atomic transactions, i.e., into a sequence of steps (orchestrated sagas) defined using AWS Step Functions, along with compensating actions (rollbacks) that can be triggered automatically in the event of a transaction failure.

- Step functions are charged by state transitions.
- A state transition is the movement from one state to another within a step function workflow (also called a state machine).
- Each state represents a specific task, choice, or operation, and the transitions define how the workflow progresses from one state to the next.

Key aspects of state transitions:

- They are defined using the "Next" field.
- Can be conditional using Choice state.
- Can be parallel using the Parallel state.
- Can end using "End": true.
- Must form a valid directed acyclic graph (no infinite loops).

Free tier: 4000 state transitions.

See: [Implement the serverless saga pattern by using AWS Step Functions](https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/implement-the-serverless-saga-pattern-by-using-aws-step-functions.html).
