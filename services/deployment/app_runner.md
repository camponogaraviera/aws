<div align='center'>
  <h1> 2. Backend & Deployment </h1>
  <h2> 2.5 Serverless Deployment </h2>
  <h3> AWS App Runner </h3>
</div>

# Table of Contents

- [AWS App Runner](#app-runner)

# [AWS App Runner](https://aws.amazon.com/apprunner/)

AWS App Runner **automatically builds/deploys** your container from a GitHub repo. There is no need to manage ECS/Fargate, just push code.

Pros: simpler than Fargate (no cluster management). Auto-scaling included. Still uses containers under the hood (just abstracts it).

Cons: it supports HTTP/HTTPS but not WebSockets, i.e., there is **no support for long-running processes**.

If WebSockets is a must, use **API Gateway WebSockets + Lambda** or **ECS Fargate**.
