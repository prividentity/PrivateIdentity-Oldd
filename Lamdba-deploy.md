[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

## Steps to Deploy Lambda function for AWS Connect ##

1. We need to create an IAM user we can use for deploying to AWS Lambda. Go to https://console.aws.amazon.com/iam/home, go to 'Users' and click on 'Add user'.
Give it a user name, let's say 'Lambda-Deploy-User' and check the box for 'Programmatic access' and click on Next.
[[images/lambda1.png]]
Under 'Set permissions' select 'Attach existing policies directly', search and select the following policies:
  * AWSLambda_FullAccess
  * IAMFullAccess
  * AWSCloudFormationFullAccess
  * AmazonS3FullAccess
  * AmazonEC2ContainerRegistryFullAccess

Create user by click on 'Next', 'Review' and 'Create user'.
Copy and save Access key ID and Secret access key somewhere secure. Note: This is the only time you see the secret key.