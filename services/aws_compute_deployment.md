<div align='center'>
  <h1>Compute & Deployment</h1>
</div>

# Table of Contents
 
- **Static Websites**
  - AWS S3
- **Infrastructure and PaaS (Platform as a Service)**
  - [Amazon Elastic Compute Cloud (EC2)](#amazon-elastic-compute-cloud)
    - About 
    - Deployment 
  - [AWS Elastic Beanstalk](#aws-elastic-beanstalk)
    - About 
    - Deployment 
- **Serverless**
  - [AWS Fargate](#aws-fargate)
    - About 
    - Deployment 
  - [AWS Lambda](#aws-lambda)
    - About 
    - Use Cases and Best Practices
    - Scaling
    - Deployment 
  - [Serverless Framework](#serverless-framework)
    - About
    - Install NodeJs
    - Install Serverless
    - Create IAM Roles
    - Create a New Serverless Project
    - Deploy Local Changes to AWS
    - Invoking a Function and Fetching Logs
    - Destroying The Server
    - The serverless.yml file
 
# Static Websites 

## AWS S3

Suitable for static websites with no server-side scripting, only client-side. However, it requires the S3 bucket to be publicly readable (not recommended). It does not provide SSL/TLS certificate for endpoints (HTTPS).

# Infrastructure and PaaS (Platform as a Service)

## [Amazon Elastic Compute Cloud (EC2)](https://aws.amazon.com/pt/ec2/)

### About

EC2 is the Enterprise level for systems that will likely scale with multiple web servers. EC2 offers virtual machines in the cloud. Each EC2 instance is a virtual machine that shares the RAM memory of a single physical machine that can run multiple sandboxed virtual machines. EC2 instances can be used to manage docker containers.

### Deployment 

Deploy your server on an EC2 instance if you prefer to manage the infrastructure yourself. Containerization is optional.

---

## [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk)

### About

"Elastic Beanstalk is a service for deploying and scaling web applications and services." —AWS.

### Deployment 

Use Elastic Beanstalk to simplify infrastructure management and deploy long-running containerized or non-containerized applications. AWS manages the underlying EC2 instances, but it is not fully serverless.

---

# Serverless

## [AWS Fargate](https://aws.amazon.com/fargate/)

### About

"AWS Fargate is a serverless, pay-as-you-go compute engine that lets you focus on building applications without managing servers." —AWS.

### Deployment 

Use Docker to containerize Express or Apollo servers for ECS (Elastic Container Service) or EKS (Elastic Kubernetes Service), and deploy them using AWS Fargate. There is no need to manage EC2 instances, AWS takes care of the underlying infrastructure (VMs, scaling, etc).

---

## [AWS Lambda](https://aws.amazon.com/pm/lambda)

### About

"Compute service that runs your code in response to events and automatically manages the compute resources." —[AWS](https://aws.amazon.com/pm/lambda). 

Unlike AWS EC2, which is maintained by AWS and the user, AWS Lambda is completely serverless (maintained by AWS). This service allows users to run their functions/code snippets (in JavaScript, Java, or Python) on the cloud. Lambda triggers are then set up to watch for events and invoke/execute a Lambda function when an event occurs. This function can return a value, write/read and modify data of services such as S3 and DynamoDB, or connect to other services such as API Gateway, Cognito Sync (mobile), Kinesis, SNS, CodeCommit, CloudWatch Events/Logs, Alexa Skills/Smart Home, AWS IoT, CloudFront, and others.

- Events: an event is what triggers the execution of a Lambda function. The event object [is a JSON-formatted document that contains data for a Lambda function to process. The Lambda runtime converts the event to an object and passes it to your function code](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-concepts.html#gettingstarted-concepts-event). Examples of events are: API Gateway requests, S3 object uploads, and DynamoDB table updates. 

- [Triggers](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-concepts.html#gettingstarted-concepts-trigger): a trigger is a specific configuration or rule that define when a Lambda function should be invoked/executed. Triggers are defined and configured within the event source service, such as API Gateway, S3, DynamoDB, etc.

### Use Cases and Best Practices 

As a best practice, a Lambda function should be designed to do a single task only:

- Handle HTTP requests.
- Uploading an object to S3 bucket.
- Storing/retrieving data into/from DynamoDB.
- Creating a thumbnail of an image.
- Communication between the API and other Amazon services (S3, Kinesis, SNS, Step Functions, Bedrock...).
 
### Scaling

["By default, Lambda provides your account with a total concurrency limit of 1,000 concurrent executions across all functions in an AWS Region."](https://docs.aws.amazon.com/lambda/latest/dg/lambda-concurrency.html)

### Deployment 

Use AWS Lambda with apollo-server-lambda and API Gateway for a fully serverless architecture. Integrate your Express or Apollo server with AWS Lambda using said package. Connect API Gateway to your Lambda function to handle incoming GraphQL requests and route them to your server. Suitable for lightweight applications within Lambda's constraints (15-minute timeout, memory limits) that do not require a long-running service.

---

# [Serverless Framework](https://www.serverless.com/) 

## About

The serverless framework is used to create, deploy, manage, and debug AWS Lambda functions from the command line. It uses AWS [CloudFormation](https://aws.amazon.com/cloudformation/) under the hood to manage the deployment of resources. It can be integrated into CI/CD pipelines.

## Install NodeJs 

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

