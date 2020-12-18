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

    git clone git@github.com:openinfer/pb-util.git 

### Step 2: Change Environment variables
     cd $HOME/pb-util/kubernetes/cluster-setup/
     vi variables.sh

Please change variables.sh according to your requirements. 

Examples
     export CLUSTER_NAME=test

### Step 3: Setup Kubernetes cluster

    cd $HOME/pb-util/kubernetes/cluster-setup
    . ./cluster-setup.sh 

**Note** Once the script completes, exit the terminal window and reconnect the session again. This ensures that docker has permissions to build images

### Step 4: Deploy Rabbitmq on Cluster
     
     cd $HOME/pb-util/kubernetes/rabbitmq
     kubectl apply -f namespace.yaml
     kubectl apply -f rbac.yaml
     kubectl config set-context --current --namespace=test-rabbitmq
     kubectl  apply -f headless-service.yaml
     kubectl create secret generic erlang-cookie --from-file=./cookie
     kubectl create secret generic rabbitmq-admin --from-file=./user --from-file=./pass
     kubectl apply -f configmap.yaml
     kubectl apply -f statefulset.yaml
     kubectl apply -f client-service.yaml

### Step 5: setup KubeIAM for permissions

      cd $HOME/pb-util/kubernetes/
      . ./kubeiam.sh

### Step 6: Deploy Publisher on Cluster
  
      cd $HOME/pb-util/kubernetes/publisher
      . ./deploy-pub.sh

### Step 7: Deploy Subscriber on Cluster
  
     cd $HOME/pb-util/kubernetes/subscriber
     . ./deploy-sub.sh

### Step 8: Setup autoscale

      kubectl autoscale deployment pb-subscriber --cpu-percent=40 --min=10 --max=500

### Step 9 : Add certificates 

#### Add SSL certs for domain 

Please follow the below steps to add certs into your cluster for SSL termination.

1. Download certs for the domain that you added in variables.sh

2. Run command with the exact path of downloaded certs.

```kubectl create secret tls <Domain> --key <path of private key> --cert <path of crt file>``` 

    e.g kubectl create secret tls privateidentity --key privateidentity.org.key --cert privateidentity.org.crt

### Step 10: Setup Ingress service

#### Setup Ingress service to access master pod from Postman.

1. cd $HOME/pb-util/kubernetes/cluster-setup 

2. Edit ingress.yml change host to your host which you want to use access.

3. After changes run `kubectl apply -f ingress.yml`

4. Run `kubectl get ing` and copy the address that you will be used while creating route.

To setup Route 53 follow https://github.com/openinfer/PrivateIdentity/wiki/Encryption_Engine_Route


***

#### Preprocess Images

Ensuring the strength of enrolls is the hallmark of Private Identity’s patented application.  A single-subject image is morphed into 60 separate images, reduced down to the compliant 53.  The original image morphs by changing the rotation, flipping, and modifying the colors through an image homogenization algorithm.  The algorithm compares the geometric distances between every permutation of images.   The algorithm discards images causing a geometric distance greater than a threshold.  If the result is less than 53 images morphing tries again.  If after N number of tries, the algorithm cannot find 53 valid images, the person is rejected and the files move to a rejection directory.   

Subject images are parsed out into three directories: the original directory retains the preliminary/primary image, an enroll directory, and a predict directory.  Both the prediction and enroll directories contain an images sub-directory and an embeddings sub-directory.  The images subdirectory contains the morphed images and the embeddings sub-directory contains embedding which by definition are  homomorphically encrypted.  

To preprocess images, locate the directory with the images stored with the person names as their filenames.
Then run the following command to augment the images and removing the bad embeddings which will create a 'enroll' and 'predict' sub-directories. 

### Step 6: Postman to send request

Send a request to process a dataset on S3 to: 

POST: https://test.privateidentity.org/trueid/v1.1/preprocess

```
{
    "bucket": BUCKET_NAME,
    "s3_dataset_dir": IMAGES_DIRECTORY,
    "server_url": SERVER_URL e.g "https://dev.privateidentity.org/trueid/v1.1",
    "enroll_threshold": "10", 
    "num_augmentations": "10",
    "validate_images": "False",
    "api_key": API_KEY
}
```

`bucket`: the S3 bucket containing the dataset.

`s3_dataset_dir`: the path of the dataset in the bucket in S3

`server_url`: Backend URL to be used for enrolling the person

`enroll_threshold`: Number of images to be used for enrolling

`num_augmentations`: Number of augmentations to be applied to the enrolled images

`validate_images`: Option to validate images by cropping and aligning

`api_key`: Provided API KEY for accessing the system.


### To clean up all resources follow below command

      cd $HOME/pb-util/kubernetes/cluster-setup
      . ./delete_cluster.sh
