## Setup cluster on AWS

####  Please change variables.sh as per requirements 
     vi $HOME/pb-util/cluster-setup/variables.sh
Examples
     export CLUSTER_NAME=test

### If you don't have root access please run below script in your newly created machine using AMI. 

    cd $HOME/pb-util/cluster-setup
    . ./preinstalled-cluster-setup.sh 

### If you have root access you can skip above step and run this command.
    
    cd $HOME/pb-util/cluster-setup
    . ./cluster-setup.sh 

**Note** Once the script completes, exit the terminal window and reconnect the session again. This ensures that docker has permissions to build cluster.

## Setup master and slave on Cluster

###     Go to location
           cd $HOME/pb-util/master/jobschedule
           ./cluster-run.sh
           kubectl apply -f deployment.yml 
           kubectl apply -f service.yml 
           cd $HOME/pb-util/slave/pb
           ./cluster-run.sh
           kubectl apply -f apply deployment,yml
           kubectl apply -f apply service.yml

### To scale number of containers
      kubectl scale --replicas=200 deployment pb-slave

**Note:** You can change replicas value as per your requirements 

## Steps to Add SSL certs for domain 

Please follow steps to add certs into cluster for ssl termination.

1. Download certs for domain that you added in variables.sh

2. Run command with exact path of downloaded certs.

```kubectl create secret tls <Domain> --key <path of private key> --cert <path of crt file>``` 

    e.g kubectl create secret tls privateidentity.org --key ~/download/privateidentity.org.key --cert ~/Download/privateidentity.org.crt

## Setup Ingress service to Access master pod from Postman.

1. Go to $HOME/pb-util/cluster-setup 

2. Edit ingress.yml change host to your host which you want to use access.

3. After changes run `kubectl apply -f ingress.yml`

4. Run `kubectl get ing` and copy address you will need it to setup route53.

To setup Route 53 follow https://github.com/openinfer/PrivateIdentity/wiki/Route-Setup

## Deploy the Cluster Autoscaler

### To deploy the Cluster Autoscaler

## HPA
The Horizontal Pod Autoscaler automatically scales the number of pods in a replication controller, deployment, replica set or stateful set based on observed CPU utilization (or, with custom metrics support, on some other application-provided metrics)
### To deploy the Cluster Autoscaler
    
     cd $HOME/pb-util/cluster-setup/
     . ./setup_autoscale.sh