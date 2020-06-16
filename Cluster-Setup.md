[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

#### If you do not have root privilege run the following: 

## Setup Machine 
https://github.com/openinfer/PrivateIdentity/wiki/Setup-Machine

Now, clone the following projects.


### Clone Projects

    git clone git@github.com:openinfer/pb.git
    git clone git@github.com:openinfer/pb-web.git
     

## Install AWSCLI


### Install pip3 using 
     sudo apt-get install python3-pip
     sudo pip3 install awscli

## Configure AWS
    aws configure 
    AWS Access Key ID [None]: XXXXXXXXXXXXX
    AWS Secret Access Key [None]: XXXXXXXXXXXXXXXX
    Default region name [None]: us-east-2
    Default output format [None]:
Note: Setup awscli on your system with credentials using ACCESS-KEY-ID and SECRET-ACCESS-KEY with default region us-east-2

## What is kubernetes
Kubernetes is an open-source container-orchestration system for automating application deployment, scaling, and management. It was originally designed by Google, and is now maintained by the Cloud Native Computing Foundation.

## Features of kubernetes
* Automated Scheduling
* Self-Healing Capabilities
* Automated rollouts & rollback
* Horizontal Scaling & Load Balancing
* Offers environment consistency for development, testing, and production
* Infrastructure is loosely coupled to each component can act as a separate unit
* Provides a higher density of resource utilization
* Offers enterprise-ready features
* Application-centric management
* Auto-scalable infrastructure
* You can create predictable infrastructure

## AWS EKS CLUSTER
Amazon Elastic Kubernetes Service (Amazon EKS) is a managed service that makes it easy for you to run Kubernetes on AWS without needing to stand up or maintain your own Kubernetes control plane. Kubernetes is an open-source system for automating the deployment, scaling, and management of containerized applications.

###  Steps to install AWS EKS Cluster
####  Please change variables.sh as per requirements 
     vi $HOME/pb/kubernetes/deployment/variables.sh 
Examples
    `export BRANCH="devel"
     export VERSION="v1.2"
     export CLUSTER_NAME=scott`

We have cluster-run.sh script that will Deploy EKS Cluster on AWS and you need to change parameters in variables.sh as described above then you can run cluster-run.sh in order to setup EKS cluster on AWS.

### If you do not have root access please run below script in your newly created machine using AMI. 

    cd $HOME/pb/kubernetes/deployment
    . ./preinstalled-cluster-setup.sh 

### If you have root access you can skip above step and run this command.
    
    cd $HOME/pb/kubernetes/deployment
    . ./cluster-setup.sh 

**Note** Once the script completes, exit the terminal window and reconnect the session again. This ensures that docker has permissions to build cluster.

## Setup mysql and redis 
Follow this
https://github.com/openinfer/PrivateIdentity/wiki/Configure-redis-and-mysql

## Build the containers for sagemakers
Change the variables in variables.sh before this:

    cd $HOMEpb/kubernetes/deployment
    . ./sagemaker.sh

## Setup PBAPP on Cluster

We need to deploy our backend services on Cluster. In order to do so we need to run the commands below that will auto deploy our code with the latest changes from git to Cluster. It's following DevOps approach it's building docker image with latest code from git and pushing it into ECR Repository on AWS and deploying Kubernetes deployment and service for Application with the latest docker image that we pushed on ECR Repo.
 
###     Go to location
 	   cd $HOME/pb/kubernetes/code/pbapp/aws
	   . ./cluster-run.sh 
	   cd $HOME/pb/kubernetes/code/jobscheduler/aws
	   . ./cluster-run.sh 

## Setup PBWEB on Cluster

In order to Deploy frontend service to Cluster with latest code from git run below commands. It is also following same DevOps approach to put app on cluster.  

### Change environment variables for pb-web app
      vi $HOME/pb-web/kubernetes/aws/variables.sh

Examples
    `export BRANCH="master"
     export VERSION="v1.2"
     export BACKED="dev.privateidentity.org"

###    Go to location
  	  cd $HOME/pb-web/kubernetes/aws
	  . ./cluster-run.sh 

## Steps to Add SSL certs for domain 

Please follow steps to add certs into cluster for ssl termination.

1. Download certs for domain that you added in variables.sh

2. Run command with exact path of downloaded certs.

```kubectl create secret tls <Domain> --key <path of private key> --cert <path of crt file>``` 

    e.g kubectl create secret tls privateidentity --key ~/download/privateidentity.org.key --cert ~/Download/privateidentity.org.crt

## Deploy the Cluster Autoscaler
## HPA
The Horizontal Pod Autoscaler automatically scales the number of pods in a replication controller, deployment, replica set or stateful set based on observed CPU utilization (or, with custom metrics support, on some other application-provided metrics)
### To deploy the Cluster Autoscaler
    
     cd $HOME/pb/kubernetes/deployment
     . ./setup_autoscale.sh
 

To setup route on aws for accessing application from browser Go to Route setup https://github.com/openinfer/PrivateIdentity/wiki/Route-Setup


## How to set kube config on your system
    aws eks --region $REGION update-kubeconfig --name $CLUSTER_NAME
    kubectl config use-context <cluster:arn>

Note: Please change <cluster:arn> to your cluster arn 
