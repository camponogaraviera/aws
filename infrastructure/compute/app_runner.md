<div align='center'>
  <h1> Compute </h1>
  <h2> Application Platform </h2>
  <h3> AWS App Runner </h3>
</div>

# Table of Contents

- [Introduction](#introduction)

---

# Introduction

[AWS App Runner](https://aws.amazon.com/apprunner/) is a serverless compute service that **automatically builds, deploys, and runs** containerized web applications and API services.

- Pros: Handles TLS, load balancing, and auto-scaling. It runs on AWS Fargate under the hood, so there is no need to manage servers or clusters.

- Cons: Supports HTTP/HTTPS but not WebSockets, i.e., there is **no support for long-running processes**. If WebSockets is a must, use **AWS API Gateway WebSockets** or deploy a custom WebSocket API on EC2.

Comparison table between AWS App Runner and AWS Elastic Beanstalk: https://aws.amazon.com/compare/app-runner-and-elastic-beanstalk/
