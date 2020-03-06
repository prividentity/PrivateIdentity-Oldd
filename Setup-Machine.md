### This doc is to setup Machine with all the dependencies installed. 
## AMAZON MACHINE IMAGE
An Amazon Machine Image is a special type of virtual appliance that is used to create a virtual machine within the Amazon Elastic Compute Cloud. It serves as the basic unit of deployment for services delivered using EC2

Please follow below steps to launch AMI into your environment.

1. Open EC2 Console https://console.aws.amazon.com/ec2/
    [[images/ami1.png]]

2. From the navigation bar, choose AMIs.
    [[images/ami2.png]]

3. Find the AMI you want to use to launch a new instance. To begin, open the menu next to the search bar, and then type **ami-0057bed62ebd38911** 

4. Select the AMI, and then choose Launch.

5. Choose an instance type, and then choose Next: Configure Instance Details.
    [[images/ami3.png]]

6. Review your configuration details and then choose choose add storage if you want to add more storage to your machine.
    [[images/ami4.png]]

7. Click on security Group and select your security group accordingly.
    [[images/ami5.png]]

8. Click on Review and launch. 
    [[images/ami6.png]]

9. Click on launch.
    [[images/ami7.png]]

10. Choose key pair or you can create new one to login into machine.
    [[images/ami8.png]]

11. From Navigation Bar, Choose instances you will see your newly created instance. 