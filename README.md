<!-- Shields -->

[![Contributions](https://img.shields.io/badge/contributions-welcome-orange?style=flat-square)](https://github.com/camponogaraviera/aws/pulls)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/camponogaraviera/aws/graphs/commit-activity)

<!-- Dependencies -->

<a href="https://aws.amazon.com/" target="_blank" rel="noopener noreferrer"><img src="https://github.com/camponogaraviera/logos/blob/main/assets/aws.png" width="50"></a>
<br>
<br>

<!-- Title -->

<div align='center'>
  <h1> Amazon Web Services Roadmap </h1>
  <h2> + Technical Interview </h2>
</div>

# Table of Contents

- [1. Infrastructure](#infrastructure)
  - AWS Global Infrastructure
    - Regions & Availability Zones
  - Security & Identity
    - Authentication vs Authorization
    - Amazon Cognito
    - AWS Identity and Access Management (IAM)
  - Networking & Content Delivery
    - Amazon Route 53 (DNS)
    - AWS Certificate Manager (SSL/TLS)
    - Amazon CloudFront (CDN)
    - AWS Web Application Firewall (WAF)
  - Storage
    - Amazon S3
  - Compute
    - Infrastructure as a Service (IaaS)
      - Amazon EC2
    - Platform as a Service (PaaS)
      - AWS Elastic Beanstalk
      - AWS App Runner
    - Serverless Compute
      - AWS Lambda
    - Serverless Container Compute
      - AWS Fargate (ECS/EKS)
    - Additional Topics
      - About Serverless
      - Serverless Framework
  - Databases
    - Relational Databases
      - Amazon RDS (PostgreSQL)
      - Amazon Aurora
    - NoSQL Databases
      - Amazon DynamoDB
    - Graph Databases
      - Amazon Neptune

- [2. Frontend](#frontend)
  - Hosting
    - About Hosting
    - Hosting Options
      - Amazon S3 (Static Hosting)
      - AWS Amplify
      - Amazon CloudFront + S3
    - Hosting Pipeline
  - Local Storage
    - AWS Amplify DataStore

- [3. Backend](#backend)
  - About Backend
    - When to Use a Backend?
  - Backend APIs
    - Amazon API Gateway
    - AWS AppSync
      - GraphQL with AppSync and DynamoDB
  - Caching
    - Amazon ElastiCache
  - Messaging & Event-Driven Architecture
    - Amazon SQS
    - Amazon SNS
    - Amazon EventBridge
    - Amazon SES
  - Streaming
    - Amazon Kinesis
  - Workflow Orchestration
    - AWS Step Functions
  - Search
    - Amazon OpenSearch
    - Amazon CloudSearch
  - Data Processing & Analytics
    - ETL
      - AWS Glue
    - Analytics
      - Amazon Athena
      - Amazon Redshift
  - Business Intelligence
    - Amazon QuickSight
  - Machine Learning & AI
    - Amazon SageMaker
    - Amazon Bedrock
  - Media Services & WebRTC
    - AWS Elemental MediaLive
    - AWS Elemental MediaConvert
    - AWS Elemental MediaPackage
    - Amazon IVS
    - Amazon Chime SDK
    - On-demand Streaming AWS Pipeline
    - Live Streaming AWS Pipeline

- [4. DevOps](#devops)
  - Infrastructure as Code
    - AWS CloudFormation
  - CI/CD
    - AWS CodePipeline
    - AWS CodeBuild
    - AWS CodeDeploy
  - Monitoring & Observability
    - Amazon CloudWatch

- [5. Deployment](#deployment)
  - Deployment Concepts
  - Deployment Strategies
    - EC2 Deployment
    - Elastic Beanstalk Deployment
    - Lambda Deployment
    - Fargate Deployment
    - Serverless Deployment

- [6. Technical Interview](#interview)

- [References](#references)

<!-- #region Infrastructure -->
<details>
  <summary><h1 id="infrastructure">1. Infrastructure</h1></summary>

## AWS Global Infrastructure

- [Regions & Availability Zones](infrastructure/global_infrastructure/regions_availability_zones.md)

## Security & Identity

- [Authentication vs Authorization](infrastructure/security_identity/a_vs_a.md)
- [Amazon Cognito](infrastructure/security_identity/cognito.md)
- [AWS Identity and Access Management (IAM)](infrastructure/security_identity/iam.md)

## Networking & Content Delivery

- [Amazon Route 53 (DNS)](infrastructure/networking_content_delivery/route53.md)
- [AWS Certificate Manager (SSL/TLS)](infrastructure/networking_content_delivery/certificate_manager.md)
- [Amazon CloudFront (CDN)](infrastructure/networking_content_delivery/cloudfront.md)
- [AWS Web Application Firewall (WAF)](infrastructure/networking_content_delivery/waf.md)

## Storage

- [Amazon S3](infrastructure/storage/storage.md)

## Compute

- Infrastructure as a Service (IaaS)
  - [Amazon EC2](infrastructure/compute/ec2.md)

- Platform as a Service (PaaS)
  - [AWS Elastic Beanstalk](infrastructure/compute/beanstalk.md)
  - [AWS App Runner](infrastructure/compute/app_runner.md)

- Serverless Compute
  - [AWS Lambda](infrastructure/compute/lambda.md)

- Serverless Container Compute
  - [AWS Fargate (ECS/EKS)](infrastructure/compute/fargate.md)

- Additional Topics
  - [About Serverless](infrastructure/compute/serverless.md)
  - [Serverless Framework](infrastructure/compute/serverless_framework.md)

## Databases

- Relational Databases
  - [Amazon RDS (PostgreSQL)](infrastructure/databases/rds.md)
  - [Amazon Aurora](infrastructure/databases/aurora.md)
- NoSQL Databases
  - [Amazon DynamoDB](infrastructure/databases/dynamodb.md)
- Graph Databases
  - [Amazon Neptune](infrastructure/databases/neptune.md)

</details>
<!-- #endregion -->

---

<!-- #region  Frontend -->
<details>
  <summary><h1 id="frontend">2. Frontend</h1></summary>

## Hosting

- [About Hosting](frontend/hosting/about_hosting.md)
- Hosting Options
  - [Amazon S3 (Static Hosting)](frontend/hosting/s3_static.md)
  - [AWS Amplify](frontend/hosting/amplify.md)
  - [Amazon CloudFront + S3](frontend/hosting/cloudfront_s3.md)
- [Hosting Pipeline](frontend/hosting/hosting_pipeline.md)

## Local Storage

- [AWS Amplify DataStore](frontend/local_storage/amplify_datastore.md)

</details>
  <!-- #endregion -->

---

<!-- #region Backend -->
<details>
  <summary><h1 id="backend">3. Backend</h1></summary>

## About Backend

- [When to Use a Backend?](backend/about/when_backend.md)

## Backend APIs

- [Amazon API Gateway](backend/backend_apis/api_gateway.md)
- [AWS AppSync](backend/backend_apis/appsync.md)
  - [GraphQL with AppSync and DynamoDB](backend/backend_apis/graphql.md)

## Caching

- [Amazon ElastiCache](backend/caching/elasticache.md)

## Messaging & Event-Driven Architecture

- [Amazon SQS](backend/messaging_event_driven/sqs.md)
- [Amazon SNS](backend/messaging_event_driven/sns.md)
- [Amazon EventBridge](backend/messaging_event_driven/eventbridge.md)
- [Amazon SES](backend/messaging_event_driven/ses.md)

## Streaming

- [Amazon Kinesis](backend/streaming/kinesis.md)

## Workflow Orchestration

- [AWS Step Functions](backend/workflow_orchestration/step_functions.md)

## Search

- [Amazon OpenSearch](backend/search/opensearch.md)
- [Amazon CloudSearch](backend/search/cloudsearch.md)

## Data Processing & Analytics

- ETL
  - [AWS Glue](backend/data_processing_analytics/etl/glue.md)
  - [ETL Pipeline](backend/data_processing_analytics/etl/etl_pipeline.md)

- Analytics
  - [Amazon Athena](backend/data_processing_analytics/analytics/athena.md)
  - [Amazon Redshift](backend/data_processing_analytics/analytics/redshift.md)

## Business Intelligence

- [Amazon QuickSight](backend/business_intelligence/quicksight.md)

## Machine Learning

- [Amazon SageMaker](backend/machine_learning/sagemaker.md)
- [Amazon Bedrock](backend/machine_learning/bedrock.md)

## Media Services & WebRTC

- [AWS Elemental MediaLive](backend/media_services/medialive.md)
- [AWS Elemental MediaConvert](backend/media_services/mediaconvert.md)
- [AWS Elemental MediaPackage](backend/media_services/mediapackage.md)
- [Amazon IVS](backend/media_services/ivs.md)
- [Amazon Chime SDK](backend/media_services/chime.md)
- [On-demand Streaming AWS Pipeline](backend/media_services/on_demand.md)
- [Live Streaming AWS Pipeline](backend/media_services/live.md)

</details>
<!-- #endregion -->

---

<!-- #region  DevOps -->
<details>
  <summary><h1 id="devops">4. DevOps</h1></summary>

## Infrastructure as Code

- [AWS CloudFormation](devops/infra_as_code/cloudformation.md)

## CI/CD

- [AWS CodePipeline](devops/ci_cd/codepipeline.md)
- [AWS CodeBuild](devops/ci_cd/codebuild.md)
- [AWS CodeDeploy](devops/ci_cd/codedeploy.md)

## Monitoring & Observability

- [Amazon CloudWatch](devops/monitoring/cloudwatch.md)

</details>
<!-- #endregion -->

---

<!-- #region  Deployment -->
<details>
  <summary><h1 id="deployment">5. Deployment</h1></summary>

## Deployment Concepts

- [About Deployment](deployment/concepts/about_deployment.md)

## Deployment Strategies

- [EC2 Deployment](deployment/strategies/ec2_deployment.md)
- [Elastic Beanstalk Deployment](deployment/strategies/beanstalk_deployment.md)
- [Lambda Deployment](deployment/strategies/lambda_deployment.md)
- [Fargate Deployment](deployment/strategies/fargate_deployment.md)

</details>
<!-- #endregion -->

---

<!-- #region Technical Interview -->
<details>
  <summary><h1 id="interview">6. Technical Interview</h1></summary>

- [Interview Questions](interview_preparation/README.md)

</details>
<!-- #endregion -->

---

<!-- #region References -->
<details>
  <summary><h1 id="references">References</h1></summary>

[1] [AWS Documentation](https://docs.aws.amazon.com/)

</details>
<!-- #endregion -->

---

# License

This work is licensed under a [Creative Commons Zero v1.0 Universal](LICENSE) license.
