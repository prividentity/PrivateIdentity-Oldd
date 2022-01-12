# Prerequisites 

 1. Obtain your custom Cloudformation template from Private ID. This will contain  a unique private key created for your org.  
 2. Obtain your AWS EC2 Key Pair from your AWS administrator. This key pair is required for access to EKS nodes and EC2 Services.
 3. Obtain your AWS API Administration Access Key and Passport from your AWS Administrator. The API Key is required for application to create the infrastructure and access resources from EKS. 
 4. Create a unique domain name and api domain name for this installation. 
 5. You need to have AWS DNS Zone ready for deployment  

NOTE : When CloudFormation will complete deployment application deployment will run around 30 minutes after that , Because the deployment consist of 2 parts 1. CpoudFormation Deployment which creates infrastructure and custom script  which deploys and configures application in AWS infrastructure  
 


# Step 1 - Upload your Cloudformation Template
1. Open the AWS CloudFormation Page https://REGION.console.aws.amazon.com/cloudformation/ 
2. Upload the Cloudformation template file provided to you by Private Identity into cloudformation 
3. Press Create Stack 
[[https://github.com/openinfer/PrivateIdentity/blob/master/images/cloudformation/1_create_stack.PNG|alt=octocat]]
4. Upload Template to CloudFormation
[[https://github.com/openinfer/PrivateIdentity/blob/master/images/cloudformation/2_upload_file.PNG|alt=octocat]]
5. Fill in the stack details as appropriate 
[[https://github.com/openinfer/PrivateIdentity/blob/master/images/cloudformation/8_CloudFormationFront.png|alt=octocat]]
6. Leave Configure Stack Options blank. Press "next" to proceed to the next step. 
7. Review deployment and check the "acknowledgement" box.
[[https://github.com/openinfer/PrivateIdentity/blob/master/images/cloudformation/4_create_stack.PNG|alt=octocat]]

# Configure your domain  

 1. Navigate to your EC2 Panel Load Balancer. The Load Balancer record 
will look something like this  
EXAMPLE: `ab78e3a37444c4f2180fd72fac63a029-9bf95e78da146b39.elb.eu-north-1.amazonaws.com`
Please use this record and point to it in DNS with an A record 

[[https://github.com/openinfer/PrivateIdentity/blob/master/images/cloudformation/7_LoadBalancer.PNG|alt=octocat]]
 
//End