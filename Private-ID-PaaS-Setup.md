Installation of infrastructure happens with cloudformation template provided directly 
When you have cloudformation template you need to open To use cloudformation template you need to prepare the folloing credentials in aws 

1. AWS EC2 Key Pair (This Keys required that you could later be able to access to EKS nodes and EC2 Services ) 
2. AWS API Administration Access Key  and Passport  (API Key is required for application to create infrastructure and access resources from EKS  )
3. Domain Name - You need to have front end domain name and api domain name 

When you have  template and all necessary variables ready 
Open AWS CloudFormation Page  - https://REGION.console.aws.amazon.com/cloudformation/ 
Upload template file into cloudformation 

1. Press on Create Stack 

2. Specify stack details 
3. Configure stack options
4. Review deployment
