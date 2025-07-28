<div align='center'>
  <h1> Deployment Options </h1>
</div>

# Table of Contents

- **About Deployment**
- **Infrastructure and Platform as a Service (PaaS)**
  - [Elastic Compute Cloud (EC2)](#elastic-compute-cloud-ec2)
    - About 
    - Deployment 
  - [Elastic Beanstalk](#elastic-beanstalk)
    - About 
    - Deployment 
- **Serverless**
  - [Lambda](#lambda)
    - About 
    - Use Cases and Best Practices
    - Scaling
    - Deployment 
  - [Fargate](#fargate)
    - About 
    - Deployment 
  - [App Runner](#app-runner)
    - About
  - [Serverless Framework](#serverless-framework)
    - About
    - Install Node.js
    - Install Serverless
    - Create IAM Roles
    - Create a New Serverless Project
    - Deploy Local Changes to AWS
    - Invoking a Function and Fetching Logs
    - Destroying The Server
    - The serverless.yml file

# About Deployment

Deployment is delivering/pushing the application's code to a runtime environment (server, edge network, cloud provider) where it can be executed. It includes build pipelines and infrastructure.

- **Services**: AWS SAM or Serverless Framework.
    
# Infrastructure and PaaS (Platform as a Service)

## [Elastic Compute Cloud (EC2)](https://aws.amazon.com/pt/ec2/)

### About

EC2 is the Enterprise level for systems that will likely scale with multiple web servers. Each EC2 instance is a virtual machine in the cloud that shares the RAM memory of a single physical machine that can run multiple sandboxed virtual machines. A virtual machine provides full control over the operating system.

EC2 allows one to manage everything on the instance, including OS updates, scaling, load balancing, monitoring, and security. EC2 instances can also be used to manage docker containers. There is **no cold-start** (good for WebSockets).

Note: a containerized application is an application that is packaged along with its dependencies, libraries, and configurations into a container, which can then run consistently across different environments. 

### Deployment 

Deploy long-running applications on an EC2 instance if you prefer to manage the infrastructure yourself. Containerization is optional.

---

## [Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk)

### About

"Elastic Beanstalk is a service for deploying and scaling web applications and services." —AWS.

Beanstalk is a Platform as a Service (PaaS) that automates much of the infrastructure management, including provisioning, load balancing, scaling, and monitoring. It abstracts away the underlying EC2 instances and lets you focus on your application. AWS manages the underlying EC2 instances, but it is not fully serverless.

### Deployment 

Elastic Beanstalk (EB) is a good choice for applications with **long-running processes** (e.g., custom video processing outside MediaConvert, WebSockets, etc.) since it supports **always-on** compute (unlike Lambda, which has a 15-minute timeout).  

**Beanstalk + Express.js** for building RESTful APIs works well for **monolithic architectures** but is **less optimal for microservices** compared to ECS/EKS or serverless solutions (due to scaling granularity and operational overhead).

---

# Serverless

Serverless does not mean a lack of server; it only means there is no need to manage server infrastructure.

## [Lambda](https://aws.amazon.com/pm/lambda)

### About

"Compute service that runs your code in response to events and automatically manages the compute resources." —[AWS](https://aws.amazon.com/pm/lambda). 

Unlike AWS EC2, which is maintained by AWS and the user, AWS Lambda is completely serverless (maintained by AWS). This service allows users to run their functions/code snippets (in JavaScript, Java, or Python) on the cloud.

Lambda triggers are then set up to watch for events and invoke/execute a Lambda function when an event occurs. This function can return a value, write/read and modify data of services such as S3 and DynamoDB, or connect to other services such as API Gateway, AppSync, SNS, and others.

- Events: an event is what triggers the execution of a Lambda function. The event object [is a JSON-formatted document that contains data for a Lambda function to process. The Lambda runtime converts the event to an object and passes it to your function code](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-concepts.html#gettingstarted-concepts-event). Examples of events are: API Gateway requests, S3 object uploads, and DynamoDB table updates. 

- [Triggers](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-concepts.html#gettingstarted-concepts-trigger): a trigger is a specific configuration or rule that defines when a Lambda function should be invoked/executed. Triggers are defined and configured within the event source service, i.e., **in the AWS service that generates the event** (e.g., S3 bucket settings, DynamoDB stream configuration, etc.). **Lambda does not poll for events; the event source service pushes events to Lambda.**

### Use Cases and Best Practices 

Lambda executes API logic. It is suitable for short-lived event-driven applications within Lambda's constraints (15-minute timeout, max [10GB RAM, and 6 vCPU cores](https://aws.amazon.com/about-aws/whats-new/2021/07/aws-lambda-supports-10-gb-memory-6-vcpu-cores-bahrain-osaka-hong-kong-regions/)). For that reason, **it is an anti-pattern to set up an Express.js/Fastify API with Lambda**, since Express.js/Fastify is a framework for long-running applications that continuously listens for requests. Each invocation spins up a new instance (cold start), making Express's persistent listeners redundant. **CRUD operations should be implemented directly on Lambda**.

As a best practice, a Lambda function should be designed to do a [single task per microservice](https://docs.aws.amazon.com/whitepapers/latest/serverless-multi-tier-architectures-api-gateway-lambda/microservices-with-lambda.html). For example:

- Lambda + API Gateway HTTP/WebSockets API to handle stateless API calls (e.g., RESTful and WebSocket). 
- Lambda + AppSync to define GraphQL resolvers.
- Lambda + SNS for real-time notifications.
- Lambda + S3 to store the thumbnail of an image.
- Lambda + DynamoDB to store/retrieve data.

Note: HTTP APIs from API Gateway used to build RESTful APIs are up to [71% cheaper compared to REST APIs](https://aws.amazon.com/about-aws/whats-new/2019/12/amazon-api-gateway-offers-faster-cheaper-simpler-apis-using-http-apis-preview/), also available from API Gateway, but offer only API proxy functionality.

### Scaling

["By default, Lambda provides your account with a total concurrency limit of 1,000 concurrent executions across all functions in an AWS Region."](https://docs.aws.amazon.com/lambda/latest/dg/lambda-concurrency.html)

Lambda's scalability comes from **stateless, parallelizable workloads**, not raw compute power. For example, in large-scale apps (YouTube, Facebook), Lambda would handle the **API logic**, while heavy lifting (video encoding, etc.) goes to **specialized services** (e.g., EC2, MediaConvert).  

### Deployment 

Connect the API Gateway HTTP API to your Lambda function to handle incoming HTTP requests (RESTful-like).

## [Fargate](https://aws.amazon.com/fargate/)

### About

"AWS Fargate is a serverless, pay-as-you-go compute engine that lets you focus on building applications without managing servers." —AWS.

Fargate is a serverless compute engine specifically designed to work with containers. There is no need to manage EC2 instances, AWS takes care of the underlying infrastructure (VMs, scaling, etc).

Fargate can be used with either ECS (Elastic Container Service) or EKS (Elastic Kubernetes Service), but not independently. It needs an orchestrator to manage the containers. ECS offers single-model deployment. EKS offers multi-model deployment.

### Deployment 

Use AWS Fargate to deploy applications with **long-running containerized processes** that require more control over the infrastructure. Prefer **Fastify + Fargate** over **Express.js + Fargate** for microservice architectures.

Pipeline:

```bash
Docker Image → Container Registry → Fargate + (ECS or EKS).
```

- Use Docker to containerize/package your application workloads (e.g., WebSocket APIs, Fastify/Express.js for RESTful API or Apollo for GraphQL API) + dependencies into a container image. The Dockerfile contain instructions for building the Docker image. The image is a standalone executable package.
- Store the Docker image in a container registry (e.g., Amazon ECR).
- Deploy the containerized application on Fargate with ECS or EKS.

---

## [App Runner](https://aws.amazon.com/apprunner/)

### About

AWS App Runner **automatically builds/deploys** your container from a GitHub repo. There is no need to manage ECS/Fargate, just push code.  

Pros: simpler than Fargate (no cluster management). Auto-scaling included. Still uses containers under the hood (just abstracts it).  

Cons: it supports HTTP/HTTPS but not WebSockets, i.e., there is **no support for long-running processes**. 

If WebSockets is a must, use **API Gateway WebSockets + Lambda** or **ECS Fargate**.

---

# [Serverless Framework](https://www.serverless.com/) 

## About

The serverless framework is used to create, deploy, manage, and debug AWS Lambda functions from the command line. It uses AWS [CloudFormation](https://aws.amazon.com/cloudformation/) under the hood to manage the deployment of resources. It can be integrated into CI/CD pipelines.

## Install Node.js 

```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```
```bash
nvm install node
```

## Install Serverless 

```bash
sudo npm install -g serverless 
```
Or
```bash
yarn add serverless 
```

## Create IAM Roles

Before creating a serverless project, you will need to create IAM roles to get an `Access key ID` and a `Secret access key`. A .csv file will be available for download after creation.

Follow this steps inside AWS: ```AWS IAM Console > Add users >  Tick the Access key box > Attach existing policies directly > Next: Tags > Next: Review > Create: user```

Then run in the terminal:

```bash
serverless config credentials --provider AWS --key <access-key-id> --secret <secret-access-key> --profile <username>
```

## Create a New Serverless Project 

- Following the setup wizard (choose a template):

```bash
sls 
```

- Check for available templates:

```bash
serverless create --help 
```

- From scratch:

```bash
sls create --template <template-name> --path <project-folder-name>
```
```bash
cd <project-folder-name>
```

## Deploy Local Changes to AWS

- This will deploy the whole stack:

```bash
sls deploy
```
You can now open the modified function in the AWS Lambda console.

- To deploy only the lambda function that was changed:

```bash
sls deploy function -f <function-name>
```

## Invoking a Function and Fetching Logs 

```bash
sls invoke -f <function-name>
```

Display logs (also available via AWS [CloudWatch](https://aws.amazon.com/pt/cloudwatch/)):

```bash
sls invoke -f <function-name> --log
```

Display all logs:

```bash
sls logs -f <function-name>
```

## Destroying The Server

```bash
sls remove 
```

## The serverless.yml file

The `serverless.yml file` is a configuration file used by the Serverless Framework to define the `Cloud provider`, `environment variables`, `function names`, `Events`, etc.  

```yml
service: my-service-name

frameworkVersion: '1'

provider:
  name: aws
  role: arn:aws:iam::123456789012:role/my-predefined-role # Example of attaching an existing IAM role.
  runtime: nodejs18.x # Others are available.
  profile: serverless-user
  stage: dev
  region: us-east-1   # The Provider's region.
  memorySize: 128     # Set the amount of memory (MB) allocated to the AWS Lambda function.
  timeout: 10         # Set the maximum execution time (in seconds) that an AWS Lambda function can run.
  environment:        # Environment variables are accessible to the process in which your application is running.
    FIRST_VAR: "value1"
    SECOND_VAR: "value2"
  # IAM Roles:
  iam:
    role:
      statements:
        - Effect: "Allow"
          Action:
            - "lambda:*"
          Resource:
            - "*"

functions:
  myLambdaFunction1:
    name: my-custom-lambda-function-name  # Defines a custom name for your first Lambda function.
    handler: handler.myHandler            # Defines the function that will be executed when the Lambda function is triggered.
  myLambdaFunction2:
    name: my-custom-lambda-function-name  # Name of your second Lambda function.
    handler: handler.myHandler            # Uses the same handler as the first Lambda function.
    memorySize: 256                       # Overrides the Memory size defined in the provider. 
    timeout: 5                            # Overrides the Timeout defined in the provider.
    events:
      - httpApi:
          path: users/create
          method: post
      - s3:
          bucket: my-bucket
          event: s3:ObjectCreated:*
      - schedule:
          rate: rate(5 minutes)
```

Example of `myHandler` function inside a `handler.js` file:
```javascript
// handler.js file.

export const myHandler = async (event, context) => {
  console.log(`Function Name: ${context.functionName}`);
  console.log(`Remaining Time: ${context.getRemainingTimeInMillis()}ms`);
  
  try {
    // Your function logic begins here:
    const username = 'camponogaraviera';
    const API_URL = `https://api.github.com/users/${username}`;
    const response = await fetch(API_URL); // This asynchronous function cannot exceed a timeout of 10s as defined in the serverless.yml file.

    if (!response.ok) { 
      throw new Error(`Error: ${response.status} ${response.statusText}`); // Check for HTTP errors.
    }

    const data = await response.json(); // Parse the JSON response.
    
    // Return a response or an error:
    return {
      statusCode: 200,
      body: JSON.stringify({ 
        message: 'Hello from Lambda!', 
        requestId: context.awsRequestId,
        userData: data, 
      }),
    };
  } catch (error) {
    console.error(`Error occurred: ${error.message}`);
    return {
      statusCode: 500,
      body: JSON.stringify({ 
        message: 'Internal Server Error',
        error: error.message,
      }),
    };
  }
};
```

