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
