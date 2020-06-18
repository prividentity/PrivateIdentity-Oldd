## Prerequisite to run Node server ##

   1. You should have running EKS cluster.
   2. You should be have ECR to store docker images. 

## Setup PaaS plaintext web application ##

### Clone project ###
    
    `git clone git@github.com:openinfer/pb-web.git`

### Setup Environment variables ###

    cd $HOME/pb-web/kubernetes/aws/deployment
    cp variables.sh variables-test.sh  
    vi variables-test.sh

Note: Here **test** is your cluster name. 

Please replace Frontend, Backend URL as per your requirements in variables-test.sh 

eg. 
     export FRONTEND=test.private.id
     export BACKEND=dev.private.id

     FRONTEND:- Replace value of this variable with your domain name which you want to use to access node app.
     BACKEND:-  Replace value of this variables with your backend python server.
     CLUSTER_NAME:- Replace value of this variable with your kubernetes cluster name.

### Run Cluster command ###

    cd $HOME/pb-web/kubernetes/aws/
    . ./cluster-run.sh

Note: This command will build docker image and put that docker image into kubernetes cluster and you will be able to use Frontend URL to access it.

### Setup SSL certs ###

To setup SSL on your domain please follow below steps.

# Steps to Add SSL certs for domain 

Please follow steps to add certs into cluster for ssl termination.

1. Download certs for domain that you added in variables-test.sh

2. Run command with exact path of downloaded certs.

```kubectl create secret tls <Domain> --key <path of private key> --cert <path of crt file>``` 

    e.g kubectl create secret tls privateid --key ~/download/privateid.key --cert ~/Download/privateid.crt