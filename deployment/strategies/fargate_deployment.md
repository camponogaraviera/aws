<div align='center'>
  <h1> Deployment Strategies </h1>
  <h2> Fargate Deployment </h2>
</div>

# Table of Contents

- [Fargate Deployment Pipeline](#fargate-deployment-pipeline)

---

# Fargate Deployment Pipeline

Use AWS Fargate to deploy applications with **long-running containerized processes** that require more control over the infrastructure.

Common options for microservice architectures are **Fastify + Fargate** and **Express.js + Fargate**.

Pipeline:

```bash
Docker Image --> Container Registry --> ECS or EKS --> Fargate
```

- Write a Dockerfile that defines how to build your application image (including code, runtime, system tools, and dependencies). The result is a Docker image, which is a portable, immutable package. When run, it becomes a container.

- Push/store the Docker image in a container registry (e.g., Amazon Elastic Container Registry (ECR)). This makes the image versioned and retrievable by your orchestration service (e.g. ECS).

- Use ECS or EKS to define tasks/services that will pull the image from the registry and start a container from it.

- Run the container created from the image on Fargate.

- Use ECS to managed the live container.
