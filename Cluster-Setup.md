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

We need to deploy our backend services on Cluster In order to do so we need to run below commands that will auto deploy our code with latest changes from git to Cluster. It's following DevOps approach it's building docker image with latest code from git and pushing it into ECR Repository on AWS and deploying Kubernetes deployment and service for Application with the latest docker image that we pushed on ECR Repo.
 
###     Go to location
 	   cd $HOME/pb/kubernetes/code/pbapp/aws
	   . ./cluster-run.sh master
	   cd $HOME/pb/kubernetes/code/jobscheduler/aws
	   . ./cluster-run.sh master

Note: Here **master** is the name of branch and **v1.2** is version of your application. 

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

Note: Here **master** is the name of branch and **v1.2** is version of your application.

## Steps to Add SSL certs for domain 

Please follow steps to add certs into cluster for ssl termination.

1. Download certs for domain that you added in variables.sh

2. Run command with exact path of downloaded certs.

```kubectl create secret tls <Domain> --key <path of private key> --cert <path of crt file>``` 

    e.g kubectl create secret tls privateidentity.org --key ~/download/privateidentity.org.key --cert ~/Download/privateidentity.org.crt

## Deploy the Cluster Autoscaler

### To deploy the Cluster Autoscaler

1. Deploy the Cluster Autoscaler to your cluster with the following command.

``` 
kubectl apply -f https://raw.githubusercontent.com/kubernetes/autoscaler/master/cluster-autoscaler/cloudprovider/aws/examples/cluster-autoscaler-autodiscover.yaml 
```

2. Add the cluster-autoscaler.kubernetes.io/safe-to-evict annotation to the deployment with the following command.

``` 
kubectl -n kube-system annotate deployment.apps/cluster-autoscaler cluster-autoscaler.kubernetes.io/safe-to evict="false"
```

3. Edit the Cluster Autoscaler deployment with the following command.

``` 
kubectl -n kube-system edit deployment.apps/cluster-autoscaler 
```

4. Edit the cluster-autoscaler container command to replace <YOUR CLUSTER NAME> with your cluster's name, and add the following options.
* --balance-similar-node-groups
* --skip-nodes-with-system-pods=false

```
spec:
      containers:
      - command:
        - ./cluster-autoscaler
        - --v=4
        - --stderrthreshold=info
        - --cloud-provider=aws
        - --skip-nodes-with-local-storage=false
        - --expander=least-waste
        - --node-group-auto-discovery=asg:tag=k8s.io/cluster-autoscaler/enabled,k8s.io/cluster-autoscaler/<YOUR CLUSTER NAME>
        - --balance-similar-node-groups
        - --skip-nodes-with-system-pods=false 
```
Save and close the file to apply the changes.

### Setup Autoscaling for both Applications

## HPA
The Horizontal Pod Autoscaler automatically scales the number of pods in a replication controller, deployment, replica set or stateful set based on observed CPU utilization (or, with custom metrics support, on some other application-provided metrics)

### To setup pod Autoscaling follow below commands and also change min and max number as per your needs. 

    kubectl autoscale deployment pb-app --cpu-percent=60 --min=1 --max=20
    kubectl autoscale deployment pb-jobscheduler --cpu-percent=60 --min=1 --max=20
    kubectl autoscale deployment pb-web-app --cpu-percent=60 --min=1 --max=10
 

To setup connection between resources db and cluster Go to VPC peering https://github.com/openinfer/PrivateIdentity/wiki/VPC-peering 

To setup route on aws for accessing application from browser Go to Route setup https://github.com/openinfer/PrivateIdentity/wiki/Route-Setup


## How to set kube config on your system
    aws eks --region $REGION update-kubeconfig --name $CLUSTER_NAME
    kubectl config use-context <cluster:arn>

Note: Please change <cluster:arn> to your cluster arn 
