<div align='center'>
  <h1> 2. Backend & Deployment </h1>
  <h2> 2.5 Serverless </h2>
  <h3> Serverless Framework </h3>
</div>

# Table of Contents

- [About](#about)
- [Install Node.js](#install-nodejs)
- [Install Serverless](#install-serverless)
- [Create IAM Roles](#create-iam-roles)
- [Create a New Serverless Project](#create-a-new-serverless-project)
- [Deploy Local Changes to AWS](#deploy-local-changes-to-aws)
- [Invoking a Function and Fetching Logs](#invoking-a-function-and-fetching-logs)
- [Destroying The Server](#destroying-the-server)
- [The serverless.yml file](#the-serverlessyml-file)

---

# About

The [serverless Framework](https://www.serverless.com/) is used to create, deploy, manage, and debug AWS Lambda functions from the command line. It uses AWS [CloudFormation](https://aws.amazon.com/cloudformation/) under the hood to manage the deployment of resources. It can be integrated into CI/CD pipelines.

# Install Node.js

```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

```bash
nvm install node
```

# Install Serverless

```bash
sudo npm install -g serverless
```

Or

```bash
yarn add serverless
```

# Create IAM Roles

Before creating a serverless project, you will need to create IAM roles to get an `Access key ID` and a `Secret access key`. A .csv file will be available for download after creation.

Follow this steps inside AWS: `AWS IAM Console > Add users >  Tick the Access key box > Attach existing policies directly > Next: Tags > Next: Review > Create: user`

Then run in the terminal:

```bash
serverless config credentials --provider AWS --key <access-key-id> --secret <secret-access-key> --profile <username>
```

# Create a New Serverless Project

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

# Invoking a Function and Fetching Logs

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

# Destroying The Server

```bash
sls remove
```

# The serverless.yml file

The `serverless.yml file` is a configuration file used by the Serverless Framework to define the `Cloud provider`, `environment variables`, `function names`, `Events`, etc.

```yml
service: my-service-name

frameworkVersion: "1"

provider:
  name: aws
  role: arn:aws:iam::123456789012:role/my-predefined-role # Example of attaching an existing IAM role.
  runtime: nodejs18.x # Others are available.
  profile: serverless-user
  stage: dev
  region: us-east-1 # The Provider's region.
  memorySize: 128 # Set the amount of memory (MB) allocated to the AWS Lambda function.
  timeout: 10 # Set the maximum execution time (in seconds) that an AWS Lambda function can run.
  environment: # Environment variables are accessible to the process in which your application is running.
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
    name: my-custom-lambda-function-name # Defines a custom name for your first Lambda function.
    handler: handler.myHandler # Defines the function that will be executed when the Lambda function is triggered.
  myLambdaFunction2:
    name: my-custom-lambda-function-name # Name of your second Lambda function.
    handler: handler.myHandler # Uses the same handler as the first Lambda function.
    memorySize: 256 # Overrides the Memory size defined in the provider.
    timeout: 5 # Overrides the Timeout defined in the provider.
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
    const username = "camponogaraviera";
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
        message: "Hello from Lambda!",
        requestId: context.awsRequestId,
        userData: data,
      }),
    };
  } catch (error) {
    console.error(`Error occurred: ${error.message}`);
    return {
      statusCode: 500,
      body: JSON.stringify({
        message: "Internal Server Error",
        error: error.message,
      }),
    };
  }
};
```
