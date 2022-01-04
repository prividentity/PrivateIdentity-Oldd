Installation of infrastructure happens with cloudformation template provided directly 
When you have cloudformation template you need to open To use cloudformation template you need to prepare the folloing credentials in aws 

1. AWS EC2 Key Pair (This Keys required that you could later be able to access to EKS nodes and EC2 Services ) 
2. AWS API Administration Access Key  and Passport  (API Key is required for application to create infrastructure and access resources from EKS  )
3. Domain Name - You need to have front end domain name and api domain name 

When you have  template and all necessary variables ready 
Open AWS CloudFormation Page  - https://REGION.console.aws.amazon.com/cloudformation/ 
Upload template file into cloudformation 

1. Press on Create Stack 
[[https://github.com/openinfer/PrivateIdentity/blob/master/images/cloudformation/1_create_stack.PNG|alt=octocat]]
2. Upload Template to CloudFormation
[[https://github.com/openinfer/PrivateIdentity/blob/master/images/cloudformation/2_upload_file.PNG|alt=octocat]]
3. Specify stack details 
[[https://github.com/openinfer/PrivateIdentity/blob/master/images/cloudformation/3_fill_cf_values.png|alt=octocat]]
4. Configure stack options
This step we can ignore and press next 
5. Review deployment
[[https://github.com/openinfer/PrivateIdentity/blob/master/images/cloudformation/4_create_stack.PNG|alt=octocat]]

6. Domain Configuration  
Go To EC2 Panelk Loadbalnceres and see loadbalancer record 
it should be something like this  
ab78e3a37444c4f2180fd72fac63a029-9bf95e78da146b39.elb.eu-north-1.amazonaws.com
Please use this record and point it in DNS as A record 

[[https://github.com/openinfer/PrivateIdentity/blob/master/images/cloudformation/7_LoadBalancer.PNG|alt=octocat]]

SSH into EC2 Instance which is created with ClooudFormation and run the following command 
sudo kubectl get services -A 


