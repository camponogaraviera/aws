<div align='center'>
  <h1> Compute </h1>
  <h2> Platform-as-a-Service (PaaS) </h2>
  <h3> AWS Elastic Beanstalk </h3>
</div>

# Table of Contents

- [Introduction](#introduction)
- [References](#references)

---

# Introduction

"Elastic Beanstalk is a service for deploying and scaling web applications and services." —AWS.

[AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk) is a Platform as a Service (PaaS) that automates much of the infrastructure management, including provisioning, load balancing, scaling, and monitoring. It abstracts away the underlying EC2 instances and lets you focus on your application. AWS manages the underlying EC2 instances, but it is not fully serverless.

Elastic Beanstalk (EB) is ideal for applications with **long-running processes** (e.g., custom video processing outside MediaConvert, WebSockets, etc.) since it supports **always-on** compute (unlike Lambda, which has a 15-minute timeout).

AWS Elastic Beanstalk environments that use Auto Scaling groups rely on Amazon CloudWatch alarms to trigger scaling operations. Out of the box, Elastic Beanstalk configures scaling based on CPU utilization by default. Elastic Beanstalk itself does not natively understand GPU metrics, but it can scale on any CloudWatch metric that Auto Scaling supports.

EB works well for **monolithic architectures**, but is **less optimal for microservice architectures** compared to `Fargate + ECS/EKS`.

Containerization is optional in EB and it supports multiple containers per Amazon EC2 instance.

---

# References

[1] [Auto Scaling triggers for your Elastic Beanstalk environment](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environments-cfg-autoscaling-triggers.html).
