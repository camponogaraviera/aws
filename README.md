<div align='center'>
  <h1> Amazon Web Services Roadmap </h1>
</div>

# Table of Contents

- [1. Frontend Hosting](#hosting)
  - About Hosting
  - Hosting Options
    - Amazon S3
    - AWS Amplify
    - Amazon CloudFront + Amazon S3
  - Content Delivery Network (CDN)
    - Amazon CloudFront
- [2. Backend Deployment](#deployment)
  - When to Use a Backend?
  - About Deployment
  - Infrastructure as a Service (IaaS)
    - Amazon Elastic Compute Cloud (EC2)
  - Platform-as-a-Service (PaaS)
    - AWS Elastic Beanstalk
  - Serverless
    - AWS Lambda
    - AWS Fargate with ECS or EKS
    - AWS App Runner
    - Serverless Framework
- [3. Networking](#networking)
  - Amazon Route 53 (DNS)
  - AWS Certificate Manager (SSL/TLS)
  - Amazon API Gateway
  - AWS Web Application Firewall (WAF)
- [4. Security](#security)
  - Authentication vs Authorization
  - Amazon Cognito
  - Amazon Identity and Access Management (IAM)
- [5. GraphQL & WebSocket APIs](#api)
  - AWS AppSync
  - GraphQL with AppSync and DynamoDB
- [6. Messaging & Streaming](#message)
  - Amazon SES
  - Amazon SNS
  - Amazon SQS
  - Amazon Kinesis
- [7. Database](#database)
  - Amazon RDS for PostgreSQL
  - Amazon DynamoDB
  - Amazon Neptune
  - Amazon Aurora
- [8. Storage (data lakes)](#storage)
  - Amazon S3
- [9. Caching](#caching)
  - Amazon Elasticache
  - AWS Amplify DataStore
- [10. Search](#search)
  - Amazon OpenSearch
  - Amazon CloudSearch
- [11. Data Processing & Analytics](#etl)
  - ETL Pipeline
    - Data Processing
      - AWS Glue
    - Analytics
      - Amazon Athena
      - Amazon Redshift
- [12. Visualization](#vis)
  - Amazon QuickSight
- [13. Monitoring](#monitoring)
  - Amazon CloudWatch
- [14. DevOps](#devops)
  - AWS CodePipeline
  - AWS CodeBuild
  - AWS CodeDeploy
- [15. Integration & Saga Pattern](#saga)
  - AWS Step Functions
  - Amazon EventBridge
  - AWS CloudFormation
- [16. Machine Learning](#ml)
  - Amazon SageMaker
  - Amazon Bedrock
- [17. Media Services & WebRTC](#ms)
  - AWS Elemental MediaLive
  - AWS Elemental MediaConvert
  - AWS Elemental MediaPackage
  - Amazon IVS
  - Amazon Chime SDK
  - On-demand Streaming AWS Pipeline
  - Live Streaming AWS Pipeline
- [18. Interview Preparation](#interview)
- [References](#references)

<!-- #region Hosting -->
<details>
  <summary><h1 id="hosting">1. Frontend Hosting</h1></summary>

## [About Hosting](services/hosting/about_hosting.md)

## [Hosting Options](services/hosting/hosting.md)

- Amazon S3
- Amazon CloudFront + Amazon S3
- AWS Amplify
- Hosting Pipeline

## Content Delivery Network (CDN)

- [Amazon CloudFront](services/hosting/cloudfront.md)

</details>
<!-- #endregion -->
  
---

<!-- #region Deployment -->
<details>
  <summary><h1 id="deployment"> 2. Backend Deployment </h1></summary>

## [When to Use a Backend?](services/deployment/when_backend.md)

## [About Deployment](services/deployment/about_deployment.md)

## Infrastructure as a Service (IaaS)

- [Amazon Elastic Compute Cloud (EC2)](services/deployment/ec2.md)
  - About
  - Deployment

## Platform-as-a-Service (PaaS)

- [AWS Elastic Beanstalk](services/deployment/beanstalk.md)
  - About
  - Deployment Pipeline

## Serverless

- [About Serverless](services/deployment/serverless.md)
- [AWS Lambda](services/deployment/lambda.md)
- [AWS Fargate with ECS or EKS](services/deployment/fargate.md)
- [AWS App Runner](services/deployment/app_runner.md)
- [Serverless Framework](services/deployment/serverless_framework.md)

</details>
<!-- #endregion -->

---

<!-- #region Networking -->
<details>
  <summary><h1 id="networking">3. Networking </h1></summary>

- [Amazon Route 53 (DNS)](services/networking/route53.md)
- [AWS Certificate Manager (SSL/TLS)](services/networking/certificate_manager.md)
- [Amazon API Gateway](services/networking/api_gateway.md)
- [AWS Web Application Firewall (WAF)](services/networking/waf.md)

</details>
<!-- #endregion -->

---

<!-- #region Security -->
<details>
  <summary><h1 id="security">4. Security</h1></summary>

- [Authentication vs Authorization](services/security/a_vs_a.md)
- [Amazon Cognito](services/security/cognito.md)
- [Amazon Identity and Access Management (IAM)](services/security/iam.md)

</details>
<!-- #endregion -->

---

<!-- #region APIs -->
<details>
  <summary><h1 id="api">5. GraphQL & WebSocket APIs</h1></summary>

- [AWS AppSync](services/apis_/appsync.md)
- [GraphQL with AppSync and DynamoDB](services/apis_/graphql.md)

</details>
<!-- #endregion -->

---

<!-- #region Messaging & Streaming -->
<details>
  <summary><h1 id="message">6. Messaging & Streaming</h1></summary>

- [Amazon SES](services/messaging/ses.md)
- [Amazon SNS](services/messaging/sns.md)
- [Amazon SQS](services/messaging/sqs.md)
- [Amazon Kinesis](services/streaming/kinesis.md)

</details>
<!-- #endregion -->

---

<!-- #region Database -->
<details>
  <summary><h1 id="database">7. Database </h1></summary>

- [Amazon RDS for PostgreSQL](services/database/rds.md)
- [Amazon DynamoDB](services/database/dynamodb.md)
- [Amazon Neptune](services/database/neptune.md)
- [Amazon Aurora](services/database/aurora.md)

</details>
<!-- #endregion -->

---

<!-- #region Storage -->
<details>
  <summary><h1 id="storage">8. Storage (data lakes)</h1></summary>

- [Amazon S3](services/storage/storage.md)

</details>
<!-- #endregion -->

---

<!-- #region Caching -->
<details>
  <summary><h1 id="caching">9. Caching</h1></summary>

- [Amazon Elasticache](services/caching/elasticache.md)
- [AWS Amplify DataStore](services/caching/amplify_datastore.md)

</details>
<!-- #endregion -->

---

<!-- #region Search -->
<details>
  <summary><h1 id="search">10. Search</h1></summary>

- [Amazon OpenSearch](services/search/opensearch.md)
- [Amazon CloudSearch](services/search/cloudsearch.md)

</details>
<!-- #endregion -->

---

<!-- #region Data Processing & Analytics -->
<details>
  <summary><h1 id="etl">11. Data Processing & Analytics</h1></summary>
  
- [ETL Pipeline](services/etl/etl.md)
  - Data Processing
    - [AWS Glue](services/etl/glue.md)
  - Analytics
    - [Amazon Athena](services/etl/athena.md)
    - [Amazon Redshift](services/etl/redshift.md)

</details>
<!-- #endregion -->

---

<!-- #region Visualization -->
<details>
  <summary><h1 id="vis">12. Visualization</h1></summary>

- [Amazon QuickSight](services/visualization/quicksight.md)

</details>
<!-- #endregion -->

---

<!-- #region Monitoring -->
<details>
  <summary><h1 id="monitoring">13. Monitoring</h1></summary>

- [Amazon CloudWatch](services/monitoring/monitoring.md)

</details>
<!-- #endregion -->

---

<!-- #region DevOps -->
<details>
  <summary><h1 id="devops">14. DevOps</h1></summary>
  
- [AWS CodePipeline](services/devops/codepipeline.md)
- [AWS CodeBuild](services/devops/codebuild.md)
- [AWS CodeDeploy](services/devops/codedeploy.md)

</details>
<!-- #endregion -->

---

<!-- #region Integration & Saga Pattern -->
<details>
  <summary><h1 id="saga">15. Integration & Saga Pattern</h1></summary>
  
- [AWS Step Functions](services/saga/step_functions.md)
- [Amazon EventBridge](services/saga/eventbridge.md)
- [AWS CloudFormation](services/saga/cloudformation.md)

</details>
<!-- #endregion -->

---

<!-- #region Machine Learning -->
<details>
  <summary><h1 id="ml">16. Machine Learning</h1></summary>

- [Amazon SageMaker](services/ml/sagemaker.md)
- [Amazon Bedrock](services/ml/bedrock.md)

</details>
<!-- #endregion -->

---

<!-- #region Media Services & WebRTC -->
<details>
  <summary><h1 id="ms">17. Media Services & WebRTC</h1></summary>
  
- [AWS Elemental MediaLive](services/media/medialive.md)
- [AWS Elemental MediaConvert](services/media/mediaconvert.md)
- [AWS Elemental MediaPackage](services/media/mediapackage.md)
- [Amazon IVS](services/media/ivs.md)
- [Amazon Chime SDK](services/media/chime.md)
- [On-demand Streaming AWS Pipeline](services/media/on_demand.md)
- [Live Streaming AWS Pipeline](services/media/pipeline.md)

</details>
<!-- #endregion -->

---

<!-- #region Interview Preparation -->
<details>
  <summary><h1 id="interview">18. Interview Preparation</h1></summary>

- [Interview Questions](interview_prep/README.md)

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
