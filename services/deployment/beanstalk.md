<div align='center'>
  <h1> 2. Backend & Deployment </h1>
  <h2> 2.4 Platform-as-a-Service (PaaS) </h2>
  <h3> AWS Elastic Beanstalk </h3>
</div>

# Table of Contents

- [AWS Elastic Beanstalk](#elastic-beanstalk)
  - About
  - Deployment

---

# [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk)

## About

"Elastic Beanstalk is a service for deploying and scaling web applications and services." —AWS.

Beanstalk is a Platform as a Service (PaaS) that automates much of the infrastructure management, including provisioning, load balancing, scaling, and monitoring. It abstracts away the underlying EC2 instances and lets you focus on your application. AWS manages the underlying EC2 instances, but it is not fully serverless.

## Deployment

Elastic Beanstalk (EB) is a good choice for applications with **long-running processes** (e.g., custom video processing outside MediaConvert, WebSockets, etc.) since it supports **always-on** compute (unlike Lambda, which has a 15-minute timeout).

`Beanstalk + Express.js` works well for building RESTful APIs of **monolithic architectures**, but is **less optimal for microservices** compared to `Fargate + ECS/EKS`.
