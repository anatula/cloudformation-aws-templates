This is a reference for useful templates to quickly launch AWS resources.

###  Requirements:

Install [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html):

```
> aws --version
aws-cli/2.17.56 Python/3.12.6 Darwin/24.1.0 exe/x86_64
```

Use `aws configure` and set the access and secret key, default region, etc.

### Template validation

There is a GitHub Action that will perform validations (using [`cfn-lint`](https://github.com/aws-cloudformation/cfn-lint)) on the templates when doing a push.
To test this locally, use `act`. Install it:

```
brew install act
```

Go to the root directory and run `act push`
