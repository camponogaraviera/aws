<div align='center'>
  <h1> 2. Backend & Deployment </h1>
  <h2> 2.5 Serverless </h2>
  <h3> AWS Fargate with ECS or EKS </h3>
</div>

# Table of Contents

- [About](#about)
- [GPU Support](#gpu-support)
- [Deployment Pipeline](#deployment-pipeline)
- [References](#references)

---

# About

"AWS Fargate is a serverless, pay-as-you-go compute engine that lets you focus on building applications without managing servers." —AWS.

[AWS Fargate](https://aws.amazon.com/fargate/)
is a serverless compute engine specifically designed to work with containers. With Fargate, there is no need to manage or provision EC2 instances. AWS takes care of the underlying infrastructure (VMs, scaling, etc). You simply define your container requirements (CPU, memory, networking), and Fargate runs them. However, Fargate needs an orchestrator to schedule and coordinate containers.

- Elastic Container Service (ECS) is a container orchestration service that schedules and manages running containers (not images). ECS uses task definitions to specify which image to pull from a registry (e.g. ECR) to start and manage (scaling, restarting on failure, etc.) a container created from that image. ECS offers single-model deployment. You can still deploy many containers across tasks and services, but you are always using ECS's orchestration style. With ECS, containers can run on:
  - EC2 instances (you provision and manage the underlying EC2 instances).
  - Fargate (AWS provides the compute, fully serverless).

- Elastic Kubernetes Service (EKS) is a fully managed Kubernetes service by AWS. EKS offers multi-model deployment. With EKS, containers can run on:
  - EC2 instances (self-managed worker nodes).
  - Fargate (serverless Kubernetes pods).

---

# GPU Support 

Fargate does not support GPU resources. You cannot define GPU requirements in a Fargate task definition. Right now, you can only specify CPU and RAM.

"If you require greater control of your Amazon EC2 instances or broader customization options, then use Amazon ECS or Amazon EKS without AWS Fargate. Use Amazon EC2 for GPU workloads, which are not supported on AWS Fargate today." —[AWS Fargate FAQs](https://aws.amazon.com/fargate/faqs/).

To date, the [GitHub issue #2735](https://github.com/aws/containers-roadmap/issues/2735) is still open.

---

# Deployment Pipeline

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

---

# References

[1] [[CloudFormation] [GPU]: Easily provide GPU resources to Batch jobs with Fargate #2735](https://github.com/aws/containers-roadmap/issues/2735)

[2] [AWS Fargate FAQs: How should I choose when to use AWS Fargate](https://aws.amazon.com/fargate/faqs/).