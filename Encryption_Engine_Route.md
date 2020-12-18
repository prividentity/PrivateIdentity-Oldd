[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

## Setup Route on AWS

## Ingress Controller
Kubernetes Ingress is an API resource that allows you manage external or internal HTTP(S) access to 
Kubernetes services running in a cluster. Amazon Elastic Load Balancing Application Load Balancer (ALB) is a popular AWS service that load balances incoming traffic at the application layer (layer 7) across multiple targets, such as Amazon EC2 instances, in a region. ALB supports multiple features including host or path based routing, TLS (Transport Layer Security) termination, WebSockets, HTTP/2, AWS WAF (Web Application Firewall) integration, integrated access logs, and health checks.


## AWS Route53 
Amazon Route 53 is a highly available and scalable cloud Domain Name System (DNS) web service. It is designed to give developers and businesses an extremely reliable and cost effective way to route end users to Internet applications by translating names like www.example.com into the numeric IP addresses like 192.0.2.1 that computers use to connect to each other.


## Steps to setup Route53 Domain to Cluster NLB

1. Open the Route 53 console at https://console.aws.amazon.com/route53/

2. Choose Create Hosted Zone   

     [[images/aws1.png]]

3. In the Create Hosted Zone pane, enter a domain name and, optionally, a comment.

     [[images/aws2.png]]

4. For Type, accept the default value of Public Hosted Zone and choose create.

5. You need to change NS in your domain hosting service **[NOTE: This doc is according to godaddy as domain Service]**

6. Make note of the four names listed for Name Servers
    
     [[images/aws3.png]]

7. Log into your GoDaddy Account Manager.

8. Click on manage button and Locate the domain you wish to register private name servers for and click the Gear icon, then select Manage DNS

9. In the Name Server Settings pop-up, select the radio button for I'll choose my own nameservers, then paste your 4 copied NS from AWS.
 
     [[images/go1.png]]

Note: It would take some time to change nameservers. 
   
10.   You need to create Record Sets for Web Tier and Server Tier Please set target as your newly created NLB for both. Use names of backend and frontend variables you had setup in variables.sh 

11. Choose Create Record Set, Choose a name 

    [[images/aws4.png]]

12. Select ALIAS and In the list of targets, select the load balancer for which you want to create an alias record [ingress load balancer]
 
13. Choose Create Record Set

14. Create Record set for frontend as well.
    
     [[images/aws5.png]]

We have setup AWS Route53 for our cluster now can access our application from url devel.privateidentity.org

    
