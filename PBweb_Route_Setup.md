[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

## Setup Route on AWS

## Ingress Controller
Kubernetes Ingress is an API resource that allows you manage external or internal HTTP(S) access to 
Kubernetes services running in a cluster. Amazon Elastic Load Balancing Application Load Balancer (ALB) is a popular AWS service that load balances incoming traffic at the application layer (layer 7) across multiple targets, such as Amazon EC2 instances, in a region. ALB supports multiple features including host or path based routing, TLS (Transport Layer Security) termination, WebSockets, HTTP/2, AWS WAF (Web Application Firewall) integration, integrated access logs, and health checks.


## AWS Route53 
Amazon Route 53 is a highly available and scalable cloud Domain Name System (DNS) web service. It is designed to give developers and businesses an extremely reliable and cost effective way to route end users to Internet applications by translating names like www.example.com into the numeric IP addresses like 192.0.2.1 that computers use to connect to each other.


## Steps to setup Route53 Domain to Cluster NLB

1. Open the Route 53 console at https://console.aws.amazon.com/route53/

2. Click on Hosted Zones   

     [[images/route_first.png]]


3. Click on your hosted zone 

    [[images/route_second.png]]

4. Choose Create Record Set

    [[images/route_third.png]]

12. Enter name and select ALIAS  In the list of targets, select the load balancer for which you want to create an alias record [ingress load balancer]
     [[images/route_fouth.png]]
  Click on Create


    
