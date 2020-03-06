[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

## VPC Peering
A VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them using private IPv4 addresses or IPv6 addresses. Instances in either VPC can communicate with each other as if they are within the same network. You can create a VPC peering connection between your own VPCs, or with a VPC in another AWS account. The VPCs can be in different regions (also known as an inter-region VPC peering connection).
### Why we need VPC Peering
We are setting VPC peering between EKS Cluster VPC and default VPC. We are doing this because EKS always created its VPC and our Database and other AWS services are in default vpc so in order to make communication between all of them we need to use VPC peering.

### Setup AWS VPC Peering connection between cluster and default VPC on aws
1. Open the Amazon VPC console. https://console.aws.amazon.com/vpc/

    [[images/vpc1.png]]

2. In the navigation pane, choose Peering Connections, Create Peering Connection.

     [[images/vpc2.png]]

3. Create a VPC Peering Connection between EKS Cluster VPC and default VPC
     * VPC (Requester): Select the default VPC in your account
     * Under Select another VPC to peer with: Ensure My account is selected, and select EKS VPC as Accepter
    
    [[images/vpc3.png]]
     
     * In the confirmation dialog box, choose OK.
4. In the navigation pane, choose Peering Connections. Select the VPC peering connection that you've created, and choose Actions, Accept Request.

5. Select the VPC peering connection that you've created, and choose Actions, Accept Request.
    
6. In the confirmation dialog, choose Yes, Accept. A second confirmation dialog displays; choose Modify my route tables now
 
7. Select the route table that's associated with the default subnet in which your db resides

8. Choose Routes, Edit, Add Route

    [[images/vpc4.png]]

9. For Destination, enter the IPv4 address range of EKS CLUSTER Subnet

    [[images/vpc5.png]]

10. Select the VPC peering connection from Target, and then choose Save.

11. You need to edit route for eks as same with destination as IPV4 range of default Subnet

Please follow Docs for more info -: https://docs.aws.amazon.com/vpc/latest/peering/create-vpc-peering-connection.html