## Prerequisite to run Node server ##

You should have running EKS cluster. 

## Setup PaaS plaintext web application ##

### Clone project ###
    
    `git clone git@github.com:openinfer/pb-web.git`

### Setup Environment variables ###

    cd $HOME/pb-web/kubernetes/aws/deployment
    cp variables.sh variables-test.sh  
    vi variables-test.sh

Note: Here **test** is your cluster name. Please replace Frontend, Backend URL as per your requirements in variables-test.sh 
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

To setup SSL on your domain please follow below doc.

https://github.com/openinfer/PrivateIdentity/wiki/cluster-setup#Steps-to-Add-SSL-certs-for-domain