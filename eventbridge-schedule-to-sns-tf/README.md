# Amazon EventBridge Scheduler to Amazon SNS

This pattern will create an EventBridge schedule to send a message to an Amazon SNS topic every 5 minutes.

Learn more about this pattern at Serverless Land Patterns: https://serverlessland.com/patterns/eventbridge-schedule-to-sns-terraform

Important: this application uses various AWS services and there are costs associated with these services after the Free Tier usage - please see the [AWS Pricing page](https://aws.amazon.com/pricing/) for details. You are responsible for any AWS costs incurred. No warranty is implied in this example.

## Requirements

* [Create an AWS account](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html) if you do not already have one and log in. The IAM user that you use must have sufficient permissions to make necessary AWS service calls and manage AWS resources.
* [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) installed and configured
* [Git Installed](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* [Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli?in=terraform/aws-get-started) installed

## Deployment Instructions

## Deployment Instructions

1. Create a new directory, navigate to that directory in a terminal and clone the GitHub repository:
    ``` 
    git clone https://github.com/aws-samples/serverless-patterns
    ```

1. Change the working directory to this pattern's directory

   ```sh
   cd serverless-patterns/eventbridge-schedule-to-sns-tf
   ```

1. From the command line, initialize terraform to  to downloads and installs the providers defined in the configuration:
    ```
    terraform init
    ```
1. From the command line, apply the configuration in the main.tf file:
    ```
    terraform apply
    ```
1. During the prompts:
    * Enter yes

1. Note the outputs from the deployment process. These contain the resource names and/or ARNs which are used for testing.

## How it works

An EventBridge Scheduler schedule is created that sends a message to an Amazon SNS topic every 5 minutes. Along with a schedule and topic, template creates an IAM role and policy for EventBridge Scheduler to assume and send messages. 

## Testing

After the resources has been deployed, you can verify EventBridge is successfully publishing to the topic by viewing the topics "NumberOfMessagesPublished" metric in CloudWatch and verifying positive data points. 

You can also add a subscription to the SNS topic such as an email address or phone number to verify messages are being published successfully.

## Cleanup

1. Change directory to the pattern directory:
    ```
    cd eventbridge-schedule-to-sns-tf
    ```
1. Delete all created resources by terraform
    ```bash
    terraform destroy
    ```
1. During the prompts:
    * Enter yes
1. Confirm all created resources has been deleted
    ```bash
    terraform show
    ```
----
Copyright 2021 Amazon.com, Inc. or its affiliates. All Rights Reserved.

SPDX-License-Identifier: MIT-0
