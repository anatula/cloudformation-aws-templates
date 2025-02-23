# Basic CloudFormation Custom Resource Example

This project demonstrates a simple AWS CloudFormation template that uses a Custom Resource backed by a Lambda function. The Lambda function is written in Node.js and is embedded directly in the CloudFormation template.

## How It Works

1. **Custom Resource**: The `MyCustomResource` resource is a Custom Resource that triggers the Lambda function.
2. **Lambda Function**: The Lambda function handles the `Create`, `Update`, and `Delete` events from the Custom Resource and sends a response back to CloudFormation.
3. **IAM Role**: The `LambdaExecutionRole` provides the necessary permissions for the Lambda function to execute and log to CloudWatch.

Deploy:

```
aws cloudformation deploy --template-file template.yaml --stack-name my-custom-resource-stack --capabilities CAPABILITY_NAMED_IAM
```

Note: The Lambda function uses the cfn-response module to send responses back to CloudFormation.

### Testing the Example

1. Deploy the stack using the AWS CLI.
2. Check the CloudFormation outputs to see the `CustomResourceMessage` and `CustomResourceId`.
3. Update the stack by changing the `MyProperty` value in the `template.yaml` and redeploying.
4. Delete the stack to trigger the `Delete` event.

Check output:

```
aws cloudformation describe-stacks --stack-name my-custom-resource-stack --query "Stacks[0].Outputs"
```

Delete stack:

```
aws cloudformation delete-stack --stack-name my-custom-resource-stack
```
