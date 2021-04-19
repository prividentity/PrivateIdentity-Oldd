## AWS Cognito User Pool

1. Open the AWS Cognito user pool https://us-east-2.console.aws.amazon.com/cognito/users

2. Click on Domain name
   [[images/UserPool1.png]]

3. click on Use your domain and enter Details
   
    [[images/UserPool2.png]]

Note: Please note TargetID it will be use in remaining step.

## AWS Route53 
Amazon Route 53 is a highly available and scalable cloud Domain Name System (DNS) web service. It is designed to give developers and businesses an extremely reliable and cost effective way to route end users to Internet applications by translating names like www.example.com into the numeric IP addresses like 192.0.2.1 that computers use to connect to each other.

## Steps to Create Route53 Domain for Cognito

1. Open the Route 53 console at https://console.aws.amazon.com/route53/

2. Click on Hosted Zones   

     [[images/route_first.png]]

3.  Click on your hosted zone 

    [[images/Route53-1.png]]

4. Choose Create Record Set

    [[images/Route53-4.png]]

5. Enter the Alias you got from Cognito and Click on create
   
    [[images/Route53-5.png]] 



