## Prerequisite


#### Install pip3 using 
     sudo apt-get install python3-pip
     sudo pip3 install awscli

#### Configure AWS
    aws configure 
    AWS Access Key ID [None]: XXXXXXXXXXXXX
    AWS Secret Access Key [None]: XXXXXXXXXXXXXXXX
    Default region name [None]: us-east-1
    Default output format [None]:
**Note:** Setup awscli on your system with credentials using ACCESS-KEY-ID and SECRET-ACCESS-KEY with Region us-east-2 and please make sure your AWS Credentials have Administrator Rights

### Step 1: Clone the repository

    git clone git@github.com:openinfer/PrivateIdenity.git

## Cognito Deployment

### Step 2: Change Environment Variables
    cd $Home/PrivateIdentity/cognito/
    vi variables.sh

Please change the value of variables mentioned inside variables.sh accordingly.
   Example Export CognitoDomain=privateid

### Step 3: Setup Cognito
     . ./setup.sh

### To update your already deployed Cognito 
    . ./update.sh

## PBWeb Deployment

### If you Already have kubernetes cluster please skip Step 1 to 2

### Step 1: Setup variables for kubernetes Cluster

     cd $Home/PrivateIdentity/eks/
     vi variables.sh

Please change the value of variables mentioned inside variables.sh accordingly.
   Example Export CLUSTER_NAME=demo

### Step 2: Setup kubernetes Cluster
     cd $HOME/PrivateIdentity/eks/
     . ./cluster-setup.sh

### Step 3: Setup Variables for PBWeb
    cd $HOME/PrivateIdentity/pbweb
    vi variables.sh
     
### Step 4. Setup Kubernetes Secrets
     1. If you have purchased ssl for your domain you already have secrets.

     kubectl create secret generic privateid-domain --from-file=certificate.pem=/path/to/certificate.pem --from-file=privateKey.pem=/path/to/privateKey.pem


### Step 5: Deploy PBWeb on Cluster
    cd $HOME/PrivateIdentity/pbweb
    . ./deploy.sh

### Step 6: Add SSL Certificates

#### Add SSL certs for domain 

Please follow the below steps to add certs into your cluster for SSL termination.

1. Download certs for the domain that you added in variables.sh

2. Run command with the exact path of downloaded certs.

```kubectl create secret tls <Domain> --key <path of private key> --cert <path of crt file>``` 

    e.g kubectl create secret tls privateidentity.org --key privateidentity.org.key --cert privateidentity.org.crt

### Step 7: Setup Ingress service to access you PBWeb over Internet.

1. cd $Home/PrivateIdentity/pbweb
2. Edit ingress.yml change host to your domain which you want your application.
3. After changes run `kubectl apply -f ingress.yml`
4. Run `kubectl get ing` and copy the address that you will be used while creating route.
To setup Route 53 follow https://github.com/openinfer/PrivateIdentity/wiki/PBweb_Route_Setup


    




     


    

