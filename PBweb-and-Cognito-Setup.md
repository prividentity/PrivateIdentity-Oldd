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
**Note:** Setup awscli on your system with credentials using ACCESS-KEY-ID and SECRET-ACCESS-KEY with Region us-east-2 and please make sure your AWS Credentials have Administrator Rights

### Step 1: Clone the repository

    git clone git@github.com:openinfer/PrivateIdeneity.git

## Cognito Deployment

### Step 2: Change Environment Variables
    cd $Home/PrivateIdentity/cognito/variables.sh

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
     vim variables.sh

Please change the value of variables mentioned inside variables.sh accordingly.
   Example Export CLUSTER_NAME=demo

### Step 2: Setup kubernetes Cluster
     cd $HOME/PrivateIdentity/eks/
     . ./cluster-setup.sh

### Step 3: Setup Variables for PBWeb
    cd $HOME/PrivateIdentity/pbweb
    vim variables.sh
     
### Step 4: Deploy PBWeb on Cluster
    cd $HOME/PrivateIdentity/pbweb
    . ./deploy.sh




     


    

