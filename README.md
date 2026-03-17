<div align='center'>
  <h1> Amazon Web Services Roadmap </h1>
</div>

# Table of Contents

- [1. Foundations](#foundations)
  - Regions & Availability Zones
- [2. Infrastructure Layer](#core)
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
    - Serverless Compute
      - AWS Lambda
      - AWS Fargate (ECS/EKS)
      - AWS App Runner
    - Additional Topics
      - About Deployment
      - About Serverless
      - Serverless Framework
- [3. Application Architecture Layer](#architecture)
  - Frontend Hosting
    - About Hosting
    - Hosting Options
      - Amazon S3 (Static Hosting)
      - AWS Amplify
      - Amazon CloudFront + S3
    - Hosting Pipeline
  - Backend & APIs
    - When to Use a Backend?
    - Amazon API Gateway
    - AWS AppSync
    - GraphQL with AppSync and DynamoDB
  - Databases
    - Relational Databases
      - Amazon RDS (PostgreSQL)
      - Amazon Aurora
    - NoSQL Databases
      - Amazon DynamoDB
    - Graph Databases
      - Amazon Neptune
  - Caching
    - Amazon ElastiCache
    - AWS Amplify DataStore
- [4. Integration & Advanced Patterns](#integration)
  - Messaging & Event-Driven Architecture
    - Amazon SQS
    - Amazon SNS
    - Amazon EventBridge
  - Additional Messaging Topics
    - Amazon SES
  - Streaming
    - Amazon Kinesis
  - Workflow Orchestration
    - AWS Step Functions
  - Search
    - Amazon OpenSearch
    - Amazon CloudSearch
- [5. Operations Layer](#operations)
  - Monitoring
    - Amazon CloudWatch
  - DevOps & CI/CD
    - AWS CodePipeline
    - AWS CodeBuild
    - AWS CodeDeploy
  - Infrastructure as Code
    - AWS CloudFormation
- [6. Specializations](#specializations)
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
- [7. Interview Preparation](#interview)
- [References](#references)

<!-- #region Foundations -->
<details>
  <summary><h1 id="foundations">1. Foundations</h1></summary>

## [Regions & Availability Zones](foundations/regions_availability_zones/regions_availability_zones.md)

</details>
<!-- #endregion -->

---

<!-- #region Infrastructure Layer -->
<details>
  <summary><h1 id="core">2. Infrastructure Layer</h1></summary>

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
    - About
    - Deployment

- Platform as a Service (PaaS)
  - [AWS Elastic Beanstalk](infrastructure/compute/beanstalk.md)
    - About
    - Deployment Pipeline

- Serverless Compute
  - [AWS Lambda](infrastructure/compute/lambda.md)
  - [AWS Fargate (ECS/EKS)](infrastructure/compute/fargate.md)
  - [AWS App Runner](infrastructure/compute/app_runner.md)

- Additional Topics
  - [About Deployment](infrastructure/compute/about_deployment.md)
  - [About Serverless](infrastructure/compute/serverless.md)
  - [Serverless Framework](infrastructure/compute/serverless_framework.md)

</details>
<!-- #endregion -->

---

<!-- #region Application Architecture Layer -->
<details>
  <summary><h1 id="architecture">3. Application Architecture Layer</h1></summary>

## Frontend & Hosting

- [About Hosting](architecture/frontend_hosting/about_hosting.md)
- Hosting Options
  - [Amazon S3 (Static Hosting)](architecture/frontend_hosting/s3_static.md)
  - [AWS Amplify](architecture/frontend_hosting/amplify.md)
  - [Amazon CloudFront + S3](architecture/frontend_hosting/cloudfront_s3.md)
- [Hosting Pipeline](architecture/frontend_hosting/hosting_pipeline.md)

## Backend & APIs

- [When to Use a Backend?](architecture/backend_apis/when_backend.md)
- [Amazon API Gateway](architecture/backend_apis/api_gateway.md)
- [AWS AppSync](architecture/backend_apis/appsync.md)
- [GraphQL with AppSync and DynamoDB](architecture/backend_apis/graphql.md)

## Databases

- Relational Databases
  - [Amazon RDS (PostgreSQL)](architecture/databases/rds.md)
  - [Amazon Aurora](architecture/databases/aurora.md)

- NoSQL Databases
  - [Amazon DynamoDB](architecture/databases/dynamodb.md)

- Graph Databases
  - [Amazon Neptune](architecture/databases/neptune.md)

## Caching

- [Amazon ElastiCache](architecture/caching/elasticache.md)
- [AWS Amplify DataStore](architecture/caching/amplify_datastore.md)

</details>
<!-- #endregion -->

---

<!-- #region Integration & Advanced Patterns -->
<details>
  <summary><h1 id="integration">4. Integration & Advanced Patterns</h1></summary>

## Messaging & Event-Driven Architecture

- [Amazon SQS](integration/messaging_event_driven/sqs.md)
- [Amazon SNS](integration/messaging_event_driven/sns.md)
- [Amazon EventBridge](integration/messaging_event_driven/eventbridge.md)

## Additional Messaging Topics

- [Amazon SES](integration/messaging_event_driven/ses.md)

## Streaming

- [Amazon Kinesis](integration/streaming/kinesis.md)

## Workflow Orchestration

- [AWS Step Functions](integration/workflow_orchestration/step_functions.md)

## Search

- [Amazon OpenSearch](integration/search/opensearch.md)
- [Amazon CloudSearch](integration/search/cloudsearch.md)

</details>
<!-- #endregion -->

---

<!-- #region Operations Layer -->
<details>
  <summary><h1 id="operations">5. Operations Layer</h1></summary>

## Monitoring

- [Amazon CloudWatch](operations/monitoring_observability/monitoring.md)

## DevOps & CI/CD

- [AWS CodePipeline](operations/devops_cicd/codepipeline.md)
- [AWS CodeBuild](operations/devops_cicd/codebuild.md)
- [AWS CodeDeploy](operations/devops_cicd/codedeploy.md)

## Infrastructure as Code

- [AWS CloudFormation](operations/infrastructure_as_code/cloudformation.md)

</details>
<!-- #endregion -->

---

<!-- #region Specializations -->
<details>
  <summary><h1 id="specializations">6. Specializations</h1></summary>

## Data Processing & Analytics

- ETL
  - [AWS Glue](specializations/data_processing_analytics/etl/glue.md)

- Analytics
  - [Amazon Athena](specializations/data_processing_analytics/analytics/athena.md)
  - [Amazon Redshift](specializations/data_processing_analytics/analytics/redshift.md)

## Business Intelligence

- [Amazon QuickSight](specializations/business_intelligence/quicksight.md)

## Machine Learning & AI

- [Amazon SageMaker](specializations/machine_learning_ai/sagemaker.md)
- [Amazon Bedrock](specializations/machine_learning_ai/bedrock.md)

## Media Services & WebRTC

- [AWS Elemental MediaLive](specializations/media_services_webrtc/medialive.md)
- [AWS Elemental MediaConvert](specializations/media_services_webrtc/mediaconvert.md)
- [AWS Elemental MediaPackage](specializations/media_services_webrtc/mediapackage.md)
- [Amazon IVS](specializations/media_services_webrtc/ivs.md)
- [Amazon Chime SDK](specializations/media_services_webrtc/chime.md)
- [On-demand Streaming AWS Pipeline](specializations/media_services_webrtc/on_demand.md)
- [Live Streaming AWS Pipeline](specializations/media_services_webrtc/pipeline.md)

</details>
<!-- #endregion -->

---

<!-- #region Interview Preparation -->
<details>
  <summary><h1 id="interview">7. Interview Preparation</h1></summary>

- [Interview Questions](interview_preparation/README.md)

</details>
<!-- #endregion -->

---

<!-- #region References -->
<details>
  <summary><h1 id="references">References</h1></summary>

[1] https://aws.amazon.com

[2] [Using Elastic Beanstalk with Amazon CloudWatch](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/AWSHowTo.cloudwatch.html).

[3] [Auto Scaling triggers for your Elastic Beanstalk environment](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environments-cfg-autoscaling-triggers.html).

[4] [Preprocess data and train a machine learning model with Amazon SageMaker AI](https://docs.aws.amazon.com/step-functions/latest/dg/sample-preprocess-feature-transform.html).

[5] [Deploy models for inference](https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html).

</details>
<!-- #endregion -->

---

# License

This work is licensed under a [Creative Commons Zero v1.0 Universal](LICENSE.md) license.
