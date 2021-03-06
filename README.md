
# Custom Authorizer

Lambda Function for custom authorizer in API Gateway

![aws-services][aws-services-image]

## How To Setup a CodePipeline

<a href="https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=ServerlessCodePipeline&amp;templateURL=https://s3.amazonaws.com/cloudformation-serverless-codepipeline.us-east-1/codepipeline.yaml"><img src="https://camo.githubusercontent.com/210bb3bfeebe0dd2b4db57ef83837273e1a51891/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f636c6f7564666f726d6174696f6e2d6578616d706c65732f636c6f7564666f726d6174696f6e2d6c61756e63682d737461636b2e706e67" alt="Launch Stack" data-canonical-src="https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png" /></a>

Input Parameter Values

- CloudformationLambdaExecutionRoleArn:

  Enter `ARN of IAM Role for Cloudformation to create changesets and target stack`. If you already created one or more CodePipeline that uses Cloudformation, this role should have been created already, so you can use the same role, 'cloudformation-lambda-execution-role'. If not, please create a role with the same name with Trust Relationships and Policy Document defined <a href="https://s3.amazonaws.com/cloudformation-serverless-codepipeline.us-east-1/roles/role_cloudformation-lambda-execution-role.json">here</a>.

- CodePipelineServiceRoleArn:

  Enter `ARN of IAM Role for CodePipeline to be executed`. If you already created one or more CodePipeline, this role should have been created already, so you can use the same role, 'AWS-CodePipeline-Service'. If not, please create a role with the same name with Trust Relationships and Policy Document defined <a href="https://s3.amazonaws.com/cloudformation-serverless-codepipeline.us-east-1/roles/role_AWS-CodePipeline-Service.json">here</a>.

- CustomAuthorizerIAMRoleName:

- CustomAuthorizerLambdaName:

- EncryptionLambdaName:

  Enter the `NAME (not ARN) of the encryption Lambda Function`. If you didn't already deployed the Encryption Lambda Function, see <a href="https://github.com/SungardAS/aws-services-encryption">here</a> to deploy the Lambda Function to Encrypt Environment Variables.

- GitHubPersonalAccessToken:

  `Access Token` for CodeBuild to access to the this Github repository. (See <a href="https://help.github.com/articles/creating-an-access-token-for-command-line-use/">here</a> to find how to generate the access token).

- GitHubSourceRepositoryBranch: `master`

- GitHubSourceRepositoryName: `aws-services-authorizer`

- GitHubSourceRepositoryOwner: `SungardAS`

- ParameterOverrides: `{ "SSOHost": "sso_host", "SSOBasicAuthUsername": "sso_user", "SSOBasicAuthPassword": "sso_password", "SSOMasterToken": "sso_master_token" }`

- ProjectImage: `aws/codebuild/python:2.7.12`

## How To Test Lambda Functions

- $ cd tests
- Export environment variables, SSO_HOST, SSO_BASIC_AUTH_USERNAME, SSO_BASIC_AUTH_PASSWORD, SSO_MASTER_TOKEN
- Replace \<username\> and \<password\> with proper values in 'test.py'
- $ python test.py

## [![Sungard Availability Services | Labs][labs-logo]][labs-github-url]

This project is maintained by the Labs group at [Sungard Availability
Services](http://sungardas.com)

GitHub: [https://sungardas.github.io](https://sungardas.github.io)

Blog:
[http://blog.sungardas.com/CTOLabs/](http://blog.sungardas.com/CTOLabs/)

[labs-github-url]: https://sungardas.github.io
[labs-logo]: https://raw.githubusercontent.com/SungardAS/repo-assets/master/images/logos/sungardas-labs-logo-small.png
[aws-services-image]: ./docs/images/logo.png?raw=true
