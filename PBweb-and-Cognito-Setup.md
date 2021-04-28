[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)


## Prerequisite


#### Install pip3 using 
     sudo apt-get install python3-pip
     sudo pip3 install awscli

#### Configure AWS
    aws configure 
    AWS Access Key ID [None]: XXXXXXXXXXXXX
    AWS Secret Access Key [None]: XXXXXXXXXXXXXXXX
    Default region name [None]: us-east-2
    Default output format [None]:
**Note:** Setup awscli on your system with credentials using ACCESS-KEY-ID and SECRET-ACCESS-KEY with Region us-east-1 and please make sure your AWS Credentials have Administrator Rights

### Clone the repository

    git clone git@github.com:openinfer/Verified-Identity.git

## PBWeb Deployment

### If you Already have kubernetes cluster please skip Step 1 and 2

### Step 1: Setup variables for kubernetes Cluster

     cd $Home/Verified-Identity/eks/
     vi variables.sh

We are using variables.sh in order to take input from users and passing that values to cloudformation, 
script to deploy resources in aws.
Please change the value of variables mentioned inside variables.sh accordingly.
   Example Export CLUSTER_NAME=demo

### Step 2: Setup kubernetes Cluster
     cd $HOME/Verified-Identity/eks/
     . ./cluster-setup.sh

### Step 3: Setup Variables for PBWeb
    cd $HOME/Verified-Identity/pbweb
    vi variables.sh
     
### Step 4. Setup Kubernetes Secrets
     1. If you have purchased ssl for your domain you already have secrets.

     kubectl create secret generic domain --from-file=certificate.pem=/path/to/certificate.pem --from-file=privateKey.pem=/path/to/privateKey.pem


### Step 5: Deploy PBWeb on Cluster
    cd $HOME/Verified-Identity/pbweb
    . ./deploy.sh

### Step 6: Setup log on Cloudwatch
    cd $HOME/Verified-Identity/pbweb
    . ./logs-setup.sh

### Step 7: Add SSL Certificates in Ingress

#### Add SSL certs for domain 

Please follow the below steps to add certs into your cluster for SSL termination.

1. Download certs for the domain that you added in variables.sh

2. Run command with the exact path of downloaded certs.

```kubectl create secret tls <Domain> --key <path of private key> --cert <path of crt file>``` 

    e.g kubectl create secret tls private.id --key private.id.key --cert private.id.crt

### Step 8: Setup Ingress service to access you PBWeb over Internet.

1. `cd $Home/Verified-Identity/pbweb`
2. Edit ingress.yml change host to your domain which you want your application.
3. After changes run `kubectl apply -f ingress.yml`
4. Wait for 1 Minute and then Run `kubectl get ing` and copy the address that you will use while creating route.
To setup Route 53 follow https://github.com/openinfer/PrivateIdentity/wiki/PBweb_Route_Setup

## Generate SAML metadata files

### Step 1: open pbweb URL in browser
     https://<yourPBWebdomain>/generateMetadata.html
    
[[images/generate-saml.png]]

### Step 2: put  yourPBWebdomain and click on generate metadata

## Cognito Deployment

### Step 1: Change Environment Variables
    cd $Home/Verified-Identity/cognito/
    vi variables.sh

Please change the value of variables mentioned inside variables.sh accordingly.
   Example Export CognitoDomain=privateid

### Step 2: Setup Cognito
     . ./setup.sh

### To update your already deployed Cognito 
    . ./update.sh

### To Setup Custom domain for your Cognito User Pool Please follow below URL.
 https://github.com/openinfer/PrivateIdentity/wiki/Cognito_Custom_Domain
    




     


    

