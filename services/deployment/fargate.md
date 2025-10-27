<div align='center'>
  <h1> 2. Backend & Deployment </h1>
  <h2> 2.5 Serverless Deployment </h2>
  <h3> AWS Fargate with ECS or EKS </h3>
</div>

# Table of Contents

- [AWS Fargate](#fargate)
  - About
  - Deployment

---

# [AWS Fargate](https://aws.amazon.com/fargate/)

## About

"AWS Fargate is a serverless, pay-as-you-go compute engine that lets you focus on building applications without managing servers." —AWS.

AWS Fargate is a serverless compute engine specifically designed to work with containers. With Fargate, there is no need to manage or provision EC2 instances. AWS takes care of the underlying infrastructure (VMs, scaling, etc). You simply define your container requirements (CPU, memory, networking), and Fargate runs them. However, Fargate needs an orchestrator to schedule and coordinate containers.

- Elastic Container Service (ECS) is a container orchestration service that schedules and manages running containers (not images). ECS uses task definitions to specify which image to pull from a registry (e.g. ECR) to start and manage (scaling, restarting on failure, etc.) a container created from that image. ECS offers single-model deployment. You can still deploy many containers across tasks and services, but you are always using ECS's orchestration style. With ECS, containers can run on:

  - EC2 instances (you provision and manage the underlying EC2 instances).
  - Fargate (AWS provides the compute, fully serverless).

- Elastic Kubernetes Service (EKS) is a fully managed Kubernetes service by AWS. EKS offers multi-model deployment. With EKS, containers can run on:
  - EC2 instances (self-managed worker nodes).
  - Fargate (serverless Kubernetes pods).

## Deployment

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
