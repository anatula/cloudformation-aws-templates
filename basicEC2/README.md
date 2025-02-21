# Basic EC2 instance

Provisions an EC2 instance with configurable parameters such as instance type, key pair, security settings, and SSH/web access control.

In this case the IP of local machine will be the only to access (otherwise the default is 0.0.0.0/0)

```
MY_IP=$(curl -s https://api.ipify.org) \
MY_IP_CIDR="${MY_IP}/32"
```

The key `aws-ec2-ed25519` is an already existing key pair.

```
aws cloudformation create-stack \
 --stack-name MyStackBasicEC2 \
 --template-body file://template.yaml \
 --parameters \
    ParameterKey=AccessIPCIDR,ParameterValue="${MY_IP_CIDR}" \
    ParameterKey=KeyName,ParameterValue=aws-ec2-ed25519
```

The template outputs the EC2 instance's id, the availibility zone it was deployed, and public ip and DNS.

Notes:

- Query for the latest Amazon Linux AMI IDs using AWS Systems Manager Parameter Store
  https://aws.amazon.com/blogs/mt/query-for-the-latest-windows-ami-using-systems-manager-parameter-store/

  ```
  aws ssm get-parameters --name "/aws/service/ami-amazon-linux-latest/al2023-ami-kernel-default-x86_64"
  ```

  Outputs:

  ```
  {
      "Parameters": [
          {
              "Name": "/aws/service/ami-amazon-linux-latest/al2023-ami-kernel-default-x86_64",
              "Type": "String",
              "Value": "ami-0c8db01b2e8e5298d",
              "Version": 111,
              "LastModifiedDate": "2025-02-14T01:35:57.418000+01:00",
              "ARN": "arn:aws:ssm:eu-central-1::parameter/aws/service/ami-amazon-linux-latest/al2023-ami-kernel-default-x86_64",
              "DataType": "text"
          }
      ],
      "InvalidParameters": []
  }
  ```
