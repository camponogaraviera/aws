<div align='center'>
  <h1> Compute </h1>
  <h2> Serverless Compute </h2>
  <h3> AWS App Runner </h3>
</div>

# Table of Contents

- [Introduction](#introduction)

---

# Introduction

[AWS App Runner](https://aws.amazon.com/apprunner/) **automatically builds/deploys** your container from a GitHub repo.

- Pros: Simpler than Fargate (no cluster management). Auto-scaling included. Still uses containers under the hood.

- Cons: Supports HTTP/HTTPS but not WebSockets, i.e., there is **no support for long-running processes**.

If WebSockets is a must, use **AWS API Gateway WebSockets** or deploy a custom WebSocket API on EC2.
