<div align='center'>
  <h1> 2. Backend & Deployment </h1>
  <h2> 2.3 Infrastructure as a Service (IaaS) </h2>
  <h3> Amazon Elastic Compute Cloud (EC2) </h3>
</div>

# Table of Contents

- [About](#about)
- [Deployment](#deployment)

---

# About

[Amazon Elastic Compute Cloud (EC2)](https://aws.amazon.com/pt/ec2/) is the Enterprise level for systems that will likely scale with multiple web servers. Each EC2 instance is a virtual machine in the cloud that shares the RAM memory of a single physical machine that can run multiple sandboxed virtual machines. A virtual machine provides full control over the operating system.

EC2 allows one to manage everything on the instance, including OS updates, CPU/GPU scaling, load balancing, monitoring, and security. A single EC2 instance can host and manage multiple containers. There is **no cold-start** (ideal for WebSockets).

Note 1: A container is a lightweight, isolated runtime environment for applications, built from an image, that shares the host OS kernel but packages everything the app needs to run consistently anywhere.

Note 2: A containerized application is an application that is packaged along with its dependencies, libraries, and configurations into a container, which can then run consistently across different environments.

# Deployment

Deploy long-running applications on an EC2 instance if you prefer to manage the infrastructure yourself. Containerization is optional.
