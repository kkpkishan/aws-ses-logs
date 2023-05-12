# AWS Lambda Function Creation using CloudFormation

This repository contains a CloudFormation template to create an AWS Lambda function that logs AWS SES (Simple Email Service) events to CloudWatch Logs.

## Prerequisites

Before you begin, ensure you have the following:

- An AWS account
- AWS CLI installed and configured with your AWS credentials

## Deployment

To deploy the Lambda function using the CloudFormation template, follow these steps:

1. Clone the repository:

   ```bash
   git clone https://github.com/kkpkishan/aws-ses-logs.git
   ```
### Navigate to the project directory:
   ```bash
   cd lambda-function-cloudformation
   ```
### Deploy the CloudFormation stack using the AWS CLI:
  ```bash
  aws cloudformation deploy --template-file template.yaml --stack-name lambda-function-stack --capabilities CAPABILITY_IAM
  ```
## Usage
To use the deployed Lambda function, you need to configure the necessary parameters. Follow these steps:
1. Navigate to the AWS Lambda console in your AWS account.
2. Find the Lambda function created by the CloudFormation stack using the stack outputs or search by name.
3. Configure the function by providing the required environment variables:
   - CloudWatchGroupName: Specify the CloudWatch Log Group Name for bounce notifications.
   - SNSTopicARN: Add the SNS Topic ARN to subscribe the Lambda function to.
   - EventType: Specify the AWS SES event type to log to the CloudWatch Log Group.
4. Save the changes and test the Lambda function by triggering the specified SES event type. 

## Cleanup
To clean up the resources created by the CloudFormation stack, use the following command:
  ```bash
  aws cloudformation delete-stack --stack-name lambda-function-stack
  ```
