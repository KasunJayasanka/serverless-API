# Serverless Framework API Project

This project uses the Serverless Framework to deploy a serverless API on AWS with Node.js 18.x runtime. It includes endpoints to get user information, retrieve player scores, and create player scores.

## Prerequisites

- [Node.js](https://nodejs.org/) installed
- [Serverless Framework](https://www.serverless.com/) installed (`npm install -g serverless`)
- [AWS CLI](https://aws.amazon.com/cli/) installed and configured with appropriate credentials

## Project Structure

- `lambdas/endpoints`: Contains the Lambda functions for different endpoints.
- `serverless.yml`: Configuration file for Serverless Framework.
- `webpack.config.js`: Configuration file for Webpack bundling.

## Configuration

### AWS Configuration

Make sure your AWS credentials are configured, and the desired profile is set in the `serverless.yml` file:

```yaml
provider:
  name: aws
  runtime: nodejs18.x
  profile: serverlessUser
  stage: dev
  region: ap-southeast-1

```

### DynamoDB Configuration

A DynamoDB table named `player-points` will be created with the necessary configuration. 
You can change the table name in the `serverless.yml` file under custom:

```yaml
custom:
  tableName: player-points
```

The DynamoDB table configuration is defined in the `serverless.yml` file under resources:

```yaml
resources:
  Resources:
    MyDynamoDbTable:
      Type: AWS::DynamoDB::Table
      Properties:
        TableName: ${self:custom.tableName}
        AttributeDefinitions:
          - AttributeName: ID
            AttributeType: S
        KeySchema:
          - AttributeName: ID
            KeyType: HASH
        BillingMode: PAY_PER_REQUEST

```

### Deployment

To deploy the API, run the following commands:

```bash
npm install
serverless deploy
```
