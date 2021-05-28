[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

## Steps to Deploy Lambda function for AWS Connect ##

1. We need to create an IAM user we can use for deploying to AWS Lambda. Go to https://console.aws.amazon.com/iam/home, go to 'Users' and click on 'Add user'.<br /><br />
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

[[images/lambda2.png]]

2.  Connect to the terminal

3.  Set up IAM user credentials by
  
 ```aws configure```

Enter the access and secret key from step 1 and keep region and output format empty.

4. Create a private repository in ECR by

`aws --region us-east-1 ecr create-repository --repository-name connect-lambda `

5.  Navigate into Connect-lambda directory by

`cd /$home/connect-lambda`

6. Build the Lambda function by

`sam build`

7. Deploy the Connect Lambda Function by

`sam deploy --guided`

Enter a stack name you like, enter the AWS region your function should resist and hit 'y' when asked. SAM config remain at defaults.
