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
Note: Setup awscli on your system with credentials using ACCESS-KEY-ID and SECRET-ACCESS-KEY with default region us-east-2

### Step 1: Clone the repository

    git clone git@github.com:openinfer/pb.git 

### Step 2: Change Environment variables
 
     vi $HOME/pb-util/cluster-setup/variables.sh

Please change variables.sh according to your requirements. 

Examples
     export CLUSTER_NAME=test

### Step 3: Setup Kubernetes cluster

    cd $HOME/pb-util/cluster-setup
    . ./cluster-setup.sh 

**Note** Once the script completes, exit the terminal window and reconnect the session again. This ensures that docker has permissions to build cluster

### step 4: Deploy publisher and subscriber on Cluster

      cd $HOME/pb-util/publisher/jobschedule
      ./cluster-run.sh
      kubectl apply -f deployment.yml 
      kubectl apply -f service.yml 
      cd $HOME/pb-util/subscriber/pb
      ./cluster-run.sh
      kubectl apply -f deployment.yml
      kubectl apply -f service.yml

### Step 5 : Add certificates 

#### Add SSL certs for domain 

Please follow below steps to add certs into your cluster for ssl termination.

1. Download certs for domain that you added in variables.sh

2. Run command with exact path of downloaded certs.

```kubectl create secret tls <Domain> --key <path of private key> --cert <path of crt file>``` 

    e.g kubectl create secret tls privateidentity.org --key ~/download/privateidentity.org.key --cert ~/Download/privateidentity.org.crt

### Step 6: Setup Ingress service

#### Setup Ingress service to access master pod from Postman.

1. Go to $HOME/pb-util/cluster-setup 

2. Edit ingress.yml change host to your host which you want to use access.

3. After changes run `kubectl apply -f ingress.yml`

4. Run `kubectl get ing` and copy address you will need it to setup route53.

To setup Route 53 follow https://github.com/openinfer/PrivateIdentity/wiki/Route-Setup


***

#### Preprocess Images

Ensuring the strength of enrolls is the hallmark of Private Identity’s patented application.  A single subject image is morphed into 60 separate images, winnowed down to the superior 53.  The original image morphs by changing the rotation, flipping and modifying the colors through an image homogenization algorithm.  The algorithm compares the geometric distances between every permutation of images.   The algorithm discards images causing a geometric distances greater than a threshold.  If the result is less than 53 images morphing tries again.  If after N number of tries, the algorithm cannot find 53 valid images, the person is rejected and the files move to a rejection directory.   

Subject images are parsed out into three directories: the original directory retains the preliminary/primary image, an enroll directory and a predict directory.  Both the prediction and enroll directories contain an images sub-directory and an embeddings sub-directory.  The images sub-directory contains the morphed images and the enbeddings sub-directory contains embedding which by definition are  homomorphically encrypted.  

To preprocess images, locate the directory with the images stored with the person names as their filenames.
Then run the following command to augment the images and removing the bad embeddings which will create a 'enroll' and 'predict' sub-directories. 

### Step 6: Postman to send request

Send a request to process a dataset on S3 to: 

POST: https://master.privateidentity.org/trueid/v1.1/preprocess

```
{
    "bucket": "preprocess-privateidentity" ,
    "s3_dataset_dir": "sample_images",
    "num_processes": 40,
    "server_url": "https://dev.private.id:443/trueid/v1.1",
    "slave_url": "http://publisher-svc:5002/trueid/v1.1/slave_preprocess",
    (Optional)"api_key": <key>
}
```

`bucket`: the S3 bucket containing the dataset.

`s3_dataset_dir`: the path of the dataset in the bucket in S3

`num_processes`: the dataset will be processed using `num_processes` parallel requests. For example, if the dataset consists of 1000 people, and num_processes=40, that means we'll have 40 parallel requests and each request processes 1000/40 = 25 people.

`api_key`: is an optional parameter. If it is not present in JSON then a default value of 1962 will be used.

