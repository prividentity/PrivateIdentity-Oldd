[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

# Table of Contents

* ### [IEEE 2410 2020 Standard for Biometric Privacy (SBP) Server-](https://github.com/openinfer/PrivateIdentity/wiki/Internal-Documentation#IEEE-2410-2020-Standard-for-Biometric-Privacy-(SBP)-Server)

* ### [Cluster Setup-](https://github.com/openinfer/PrivateIdentity/wiki/Internal-Documentation#Cluster-Setup)

* ### [Demo Parameter Usage-](https://github.com/openinfer/PrivateIdentity/wiki/Internal-Documentation#Demo-Parameter-Usage)

* ### [SaaS Architecture-](https://github.com/openinfer/PrivateIdentity/wiki/Internal-Documentation#SaaS-Architecture)

* ### [PB Utility-](https://github.com/openinfer/PrivateIdentity/wiki/Internal-Documentation#pb-Utils)

* ### [NodeJS Endpoints-](https://github.com/openinfer/PrivateIdentity/wiki/Internal-Documentation#NodeJS-Endpoints)

* ### [Customer Integration-](https://github.com/openinfer/PrivateIdentity/wiki/Internal-Documentation#Customer-Integration)

* ### [Maryland Test Facility-](https://github.com/openinfer/PrivateIdentity/wiki/Internal-Documentation#Maryland-Test-Facility)

* ### [FAQ-](https://github.com/openinfer/PrivateIdentity/wiki/Internal-Documentation#FAQ)


# IEEE 2410 2020 Standard for Biometric Privacy (SBP) Server

### SBP API Overview

**Format**

All API communicate RESTful using JSON.  

**Developer API_Key**

Individual developers need to apply for an API_Key for their applications that shall use SBP. Once individual developers have their own API_Key, all of the API calls their applications make use this API_Key as one of the parameters.

### API Enroll Overview

To enroll a user, we take the Enrollment Data which is a set of tag/value pairs (any tag, such as an ID number or GUID is acceptable). Using a Global UUID a new identity is created in the persistent engine corresponding to the Enrollment Data provided.

**Request**

The format of this API call is:  

POST “/trueid/v1.1/enroll”

|Parameter     |         Value| 
|-----|----|
|api_key       |         api_key string to use this service|
|subject_id or uuid           |         Tag/Value pairs|
|features      |         Type, Name, Feature Array. Type is voice, face or fingerprint.|

An Enroll API request example is as follows:
```
{
    "api_key": "XXXXXXXXXXXXXXXXXX",
    "Enrollment Data": {
	"id": "1008023",
    },
    "features": [
	{“type”: “voice”, name: “voice1.wav”,  “embedding_vector”: [...] },
	{“type”: “face”, name: “face1.png”, “embedding_vector”: [...]},
        {“type”: “fingerprint”, name: “fingerprint1.png”, “embedding_vector”: [...]},

	…
	{}
    ]

}
```

**Response**

The response of an Enroll request returns O as Success given data validation and database storage success.
The response returns -1 if the user already exists in the model.
The response returns -2 if the embedding distance is too far caused by at least one bad enroll embedding (usually caused by a bad enroll image).


### Predict Overview

Once enrolled, a caller shall call the Predict API to perform an attempt to use the trained system to identify the individual subject based upon images provided in the call.

**Request**

The format of this API call is: 

POST “/trueid/v1.1/predict”

|Parameter      |            Value|
|----------|--------------| 
|api_key       |         api_key string to use this service|
|features       |            Type, Name, Feature Array. Type is voice, face or fingerprint.|


A Predict API request example is as follows:
```
{
    "api_key": "XXXXXXXXXXXXXXXXXX",
    "features": [
	{“type”: “voice”, name: “voice1.wav”,  “embedding_vector”: [...] },
	{“type”: “face”, name: “face1.png”, “embedding_vector”: [...]},
        {“type”: “fingerprint”, name: “fingerprint1.png”, “embedding_vector”: [...]},
	…
	{}
    ]
}
```
**Response**

The response of a Predict request, if meeting confidence thresholds, returns enrollment data in the following format:
```
{
    "Enrollment Data": {
	"id": "1008023",
    },
    "message": "OK",
    "status": 0,
    "subject_id": 4,
    ]
}
```

### Liveness Overview

To recognize liveness, a mechanism to affirm interaction with a live individual, we take in audio files along with their respective expected text. The API call returns a value related to the certainty that the audio samples match what is expected.  Video  shall be used through the same API call.   All input is in .wav format.  Liveness is a local client call, typically, but is supported on the server in the format listed below.  The best practice is for a local liveness call so that plaintext is not transmitted.  

**Request**

The format of this API call is: 

POST “/trueid/v1.1/liveness”
```
{
    "voice": [
        ["voice_1", "base64_audio_1", "text_expected_1"],
        ["voice_2", "base64_audio_2", "text_expected_2"],
        ...
        ["voice_n",  "base64_audio_n", text_expected_n"]
    ],
    "api_key": "xxxxxx"
}
```
**Response**

The response of a liveness request Returns accuracy data as a ratio from 0 to 1, with a value of .9 denoting 90% accuracy.
```
{
    "accuracy": [
        ["accuracy_1": ".9"],
        ["accuracy_2": ".8"],
        ...
        ["accuracy_n": ".85"]
    ],
}
```
### Add Role Overview

This API helps add role parametres to the database. The role helps us assign different levels to the subjects enrolled in the database. Role consists of two parameters named as <tag> and <value>. For ex., <tag> can define the name of the role such as admin, developer etc., whereas the <value> defines the level of access that can be granted to the user level1, tier1 etc.,. The <tag> and <value> can be anything depending upon the convenience of the user. The request must be a post with the values passed in the request body as JSON.


**Request**

The format of this API call is: 

POST  “/trueid/v1.1/add_role”

|Parameter | Value             |
|----------|-------------------|
|tag       | String, Role Name |
|value     | String, Role value|
|api_key     | api_key in string value|
```
{
    "tag": "admin",
    "value": "L1"
}
```
**Response**

The response of add role request returns <role_id> of the <tag> and <value> added to the database with a status of 0, where the <role_id> will be an auto-generated number from the system. This <role_id> is then used for adding the role to the particular subject. If the add role fails, API will return a status of -2 with the reason in the message.
```
{
   “status”: 0
   “role_id” : 1
   “message” : “Role Successfully added.”
}
{
   “status”: -2
   “message” : “Role exists in database”
}
```
### Delete Subject Overview
This API deletes a subject from the database. To delete the subject from the database, the user must know the <subject_id>. The request must be a post with the values passed in the request body as JSON.


**Request**

The format of this API call is: 

POST  “/trueid/v1.1/delete_subject”

|Parameter | Value           |
|----------|-----------------|
|subject_id   | Number, Subject ID |
|api_key     | api_key in string value|

```
{
    "subject_id": 1,
    "api_key": "xxxxx"
}
```
**Response**

The response of delete subject request returns a status of 0 upon successful deletion. <subject_id> must be passed in the request body. If the delete subject fails, API will return a status of -2 with the reason in the message.
```
{
   “status”: 0
   “message” : “Subject Successfully deleted.”
}

{
   “status”: -2
   “message” : “SubjectID does not exists in database”
}
```


### Delete Role Overview

This API helps delete a role parametres from the database. To delete the role from the database, the user must know the <role_id> acquired during the addition of role to the database. The request must be a post with the values passed in the request body as JSON.


**Request**

The format of this API call is: 

POST  “/trueid/v1.1/delete_role”

|Parameter | Value           |
|----------|-----------------|
|role_id   | Number, Role ID |
|api_key     | api_key in string value|

```
{
    "role_id": 1,
    "api_key": "xxxxx"
}
```
**Response**

The response of delete role request returns a status of 0 upon successful deletion. <role_id> must be passed in the request body. If the delete role fails, API will return a status of -2 with the reason in the message.
```
{
   “status”: 0
   “message” : “Role Successfully deleted.”
}

{
   “status”: -2
   “message” : “RoleID does not exists in database”
}
```
### Add Role to Subject

This API helps to add an existing role to a particular subject. Request must provide both the <role_id> and the <subject_id> they want to add. The request must be a post with the values passed in the request body as JSON.


**Request**

The format of this API call is: 

POST  “/trueid/v1.1/add_role_to_subject”

|Parameter | Value              |
|----------|--------------------|
|role_id   | Number, Role ID    |
|subject_id| Number, Subject ID |
|api_key     | api_key in string value|
```
{
    "role_id": 1,
    "subject_id":4,
    "api_key": "xxxxxx"
}
```
**Response**

The response of add role to subject request returns a status of 0 upon successful addition. <role_id> and <subject_id> must be passed in the request body. If the API fails, it will return a status of -2 with the reason in the message. The API will also fail if there is no specified <role_id> or <subject_id> present in the database.
```
{
   “status”: 0
   “message”: “Role Successfully added to the Subject.”
}

{
   “status”: -2
   “message” : “Not a valid subject/Role. (or) Role exists in database”
}
```
### Delete Role from Subject

This API helps to delete a role from a particular subject. Request must provide both the <role_id> and the <subject_id> they want to remove. The request must be a post with the values passed in the request body as JSON.

**Request**

The format of this API call is: 

POST  “/trueid/v1.1/delete_role_from_subject”

|Parameter | Value              |
|----------|--------------------|
|role_id   | Number, Role ID    |
|subject_id| Number, Subject ID |
|api_key     | api_key in string value|
```
{
    "role_id": 1,
    "subject_id":4,
    "api_key": "xxxxx"
}
```
**Response**

The response of delete role from subject request returns a status of 0 upon successful deletion. <role_id> and <subject_id> must be passed in the request body. If the API fails, it will return a status of -2 with the reason in the message. The API will also fail if there is no specified <role_id> or <subject_id> present in the database.
```
{
   “status”: 0
   “message”: “Role Successfully deleted from Subject.”
}

{
   “status”: -2
   “message” : “Not a valid subject/Role. (or) Role does not exist in database”
}
```


### API Verify Overview

To check the distance between the given embeddings_1 array with the given embeddings_2 array or the embeddings of enrolled person with given subject_id

**Request**

The format of this API call is:  

POST “/trueid/v1.1/verify”

|Parameter     |         Value| 
|-----|----|
|api_key       |         api_key string to use this service|
|type          |         a string (face, voice, fingerprint)|
|embeddings_1  |         a list of embeddings of the first person |
|embeddings_2  |         a list of embeddings of the second person if subject_id is not provided|
|subject_id    |         Number, Subject ID of the enrolled person to retrieve embeddings if embeddings_2 is not provided|

An API request example is as follows:
```
{
   "api_key": "xxxxx",
   "type": "face",
   "embeddings_1": [
  		[...],
                [...],
                 …
  	],
   "embeddings_2": [
	  	[...],
                [...],
                 …
	]
}
```

Another API request example is as follows:
```
{
   "api_key": "xxxxx",
   "type": "face",
   "embeddings_1": [
  		[...],
                [...],
                 …
  	],
   "subject_id": 1
}
```

**Response**

The response returns -1 if there is error. If return 0, it's success and provide information as:
```
{
    "status": 0,
    "distance": {
        "max": 1.3864889343185174,
        "mean": 1.3714485861588377,
        "min": 1.3531817732607498
    },
    "threshold": {
        "max": 0.55,
        "mean": 0.5,
        "min": 0.3
    }
}
```

[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

# Cluster Setup

* Asynchronous pre-processing engine for massive plaintext biometric ingestion 
* Elastic, fault-tolerant and load balanced Kubernetes clusters
* Decoupled from back-end cluster for privacy 
* Provides exception processing 

The Encryption Engine provides unlimited asynchronous throughput for high-demand enrollment and identification tasks using elastic, load-balanced, fault-tolerant Kubernetes clusters.
The Encryption Engine maintains full accuracy and performance through real-world boundary conditions and accepts Base-64 plaintext images, video or audio using directory scanning or RESTful API. The Engine identifies multiple faces and fingerprints per frame, identifies voice in audio, provides data augmentation, creates a 1-way hash (FHE transformation) for subsequent processing, and then immediately discards the original biometrics. FHE transformation requires 10ms constant time using Cloud AI services and load-balanced, elastic, fault-tolerant Kubernetes clusters. 

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

## Build the containers for sagemakers
Change the variables in variables.sh before this, and add the proper endpoints:

    cd $HOME/pb/kubernetes/deployment
    . ./sagemaker.sh
    cp variables.sh variables-[Clustername].sh
    

### Please Create a copy of variables.sh as variables-[ClusterName].sh ###

     cd $HOME/pb/kubernetes/deployment
     cp variables.sh variables-[ClusterName].sh

**NOTE** Please Replace [ClusterName] with you clustername. e.g variables-pbtest.sh
     
## Setup PBAPP on Cluster

We need to deploy our backend services on Cluster. In order to do so we need to run the commands below that will auto deploy our code with the latest changes from git to Cluster. It's following DevOps approach it's building docker image with latest code from git and pushing it into ECR Repository on AWS and deploying Kubernetes deployment and service for Application with the latest docker image that we pushed on ECR Repo.
 
###     Go to location
 	   cd $HOME/pb/kubernetes/code/pbapp/aws
	   . ./cluster-run.sh 
	   cd $HOME/pb/kubernetes/code/jobscheduler/aws
	   . ./cluster-run.sh 

## Steps to Add SSL certs for domain 

Please follow steps to add certs into cluster for ssl termination.

1. Download certs for domain that you added in variables.sh

2. Run command with exact path of downloaded certs.

```kubectl create secret tls <Domain> --key <path of private key> --cert <path of crt file>``` 

    e.g kubectl create secret tls privateidentity --key ~/download/privateidentity.org.key --cert ~/Download/privateidentity.org.crt

3. Rename your keys to .pem format in order to create secrets for SAML.
    
    e.g mv privateidentity.org.key privateKey.pem
        mv privateidentity.org.crt certificate.pem

4. RUN command to create secrets for SAML.
    
    kubectl create secret tls privateid-domain --key privateKey.pem --cert certificate.pem
 

### Please Create a copy of variables.sh as variables-[ClusterName].sh ###

     cd $HOME/pb-web/kubernetes/aws/deployment
     cp variables.sh variables-[ClusterName].sh

**NOTE** Please Replace [ClusterName] with you clustername. e.g variables-pbtest.sh


## Setup PBWEB on Cluster

In order to Deploy frontend service to Cluster with latest code from git run below commands. It is also following same DevOps approach to put app on cluster.  

### Please Create a copy of variables.sh as variables-[ClusterName].sh ###

     cd $HOME/pb-web/kubernetes/aws/deployment
     cp variables.sh vaiables-[ClusterName].sh


### Change environment variables for pb-web app
      vi $HOME/pb-web/kubernetes/aws/deployment/variables-[ClusterName].sh

** NOTE ** Please Replace [ClusterName] with you clustername. e.g variables-pbtest.sh


Examples
    `export BRANCH="master"
     export VERSION="v1.2"
     export BACKED="dev.privateidentity.org"

###    Go to location
  	  cd $HOME/pb-web/kubernetes/aws
	  . ./cluster-run.sh 

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

[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

# Demo Parameter Usage

## Merging Face and Voice Enrollments on /a/
<br/>

This page documents how to update enrolled user modalities. This document assumes a user is already enrolled by only one modality (like face or voice) and they want to add another one on top of it. 

Note that only one modality can be enrolled for this to work, if a face modality is to be added to a voice modality, the face modality can't already exist. In this case use the parameter action=subjectDelete&subject_id=# this will delete your modality specified with the subject id.

The following workflow must start with the user predicting with one modality to get his subject_id. Afterwards, the user should manually go to the application interface, with the newly requested modality equaling to true.

**Request**


The format of this API call is:  


|Parameter     |         Value| 
|-----|----|
|api_key       |         api_key string to use this service|
|action           |         Must be set to enroll|
|uuid      |         uuid retrieved from initial predict.|

In addition to the previous parameters, a certain modality must be set to true, while the original one should be set to false.


**Example**

A certain user is enrolled with face, and can successfully predict with that. This user wants to enroll with voice, too. The subject_id parameter must be retrieved from the face predict. Next, the URL the user should have the following parameters to enroll with voice:

GET “/apiKey=xxxx&voice=true&face=false&action=enroll&uuid=x”

NOTE: the other modality should be set to false for this feature to work.


**Response**

After the merge is complete, the response from the console will be seen as the following, note that the ID will be the same as the original ID:

```
{
    "uuid":1,
    "message":"OK",
    "status":0
}
```

## User Interface Demonstration
<br/>

There are two versions of the demonstration app, the first one is version 0.9, and the parameters are selected manually. The second version, version 1.0, has an interface from which you can select parameters.

Version 1.0 and Version 0.9 are functionally the same, so an enrollment made on one version, can be accessed on another.

A picture with the panel layout explained is shown below, or you can view a demonstration video from this link
[Demonstration](https://www.youtube.com/watch?v=6x0b5FckhIA)

![Version 1.0 User Interface](https://github.com/openinfer/PrivateIdentity/blob/master/images/Version%201.0%20UI.png)

## Anti Spoofing Technique
<br/>

Spoofing is a well-known scenario when a user with malicious intent tries to bypass the biometric security by playing a recorded video/printed image.

To enable the anti-spoofing in the application, add the URL parameter `antiVideoSpoof=true` while launching the application. This enables the application to check whether the stream of images captured from the webcam is a recorded one or a live one. This is achieved by a machine learning model running in the browser that checks the image passed to it and gives back a probability of whether the image is a spoofed one or not. If the spoofing is detected, the application won't allow the user to perform the requested operation until it is a live one. There are two models to detect when someone is spoofing, the first one detects if the spoof origin is a video on a device or an image on a device. The second one detects if the spoof origin is a print image. So for example if someone tried using a spoof printed image of a face, it will pass through the device image or device video model, but will be caught on the print image model and be detected as spoof.

[Sample Demonstration of Video Spoofing](https://youtu.be/NajcsUsrnbI):

![Video Spoof Demo](https://github.com/openinfer/PrivateIdentity/blob/master/images/Spoof_Icon_Example.png)

Another way to check the spoofing is to check whether the liveness of the user can be verified. This can be detected by checking the user's eye blink from the sequence of captured images. To enable the liveness of the user, either add the URL parameter `faceLiveness=true` or double click on the face icon before performing a enroll/prediction.

Sample Demonstration of Eyeblink success:

![Eye Blink Demo](https://github.com/openinfer/PrivateIdentity/blob/master/images/eye_blink_demo.png)

[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

<br/>

# SaaS Architecture

In this document, the SaaS architecture is explained in terms of how the workflow should be executed. The elements of this workflow are as follows: 

1. Consuming client.
1. NodeJS middle-tier.
1. Authorizing Python server.

1- The consuming client is any application trying to use any of our services previously explained. The client must have a valid api_key for a request to execute. 

2- NodeJS middle-tier is passing the api_key to the Python server, and making sure it exists in valid format. If the api_key is invalid or absent in the call payload, error message will be sent back without consuming the Python server.

3- The Python server checks to see if the request has a valid api_key. If the api_key format is valid, processing continues. 


The first step in the workflow is to register a new api_key for any given client, so that it can be used. This api_key cannot be used inside a browser JavaScript code. It can be used, for example, on NodeJS, and that would be to prevent exploiting the api_key to the outer world.

Here is an example of using api_key in the previously described workflow:


|Parameter     |         Value| 
|-----|----|
|...           |         This can be any kind of request, like predict or enroll.|
|api_key      |          value of api_key in text format.|

```
{
 ...,
 api_key: "xxxxxxxxxxx"
}
```

This structure denotes that any kind of request, must have a key called api_key at the top level of the request.  The three dots in the previous payload can be replaced with any other type of request, i.e., predict or enroll.

If the api_key is absent or coming in invalid format, in any request payload, the NodeJS will respond back with the following error message:

```
{
 error: 'invalid api_key key'
} 
```

[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)
<br/>

# pb-Utils

Biometric authentication is only as good as the quality of its enrolls (subject image registration).  Registration and log-in is browser-based, an individual can enroll via the camera on their computer, tablet or phone and requires no external apparatus. 

What differentiates Private Identity’s proprietary application is that it scales to enterprises of any size.  When an individual user enrolls, the entire process is encaged within the browser, processing the captured images and uploading them to the server where all information is classified for future reference in the verification process.  The utility of Python, a high-level, general-purpose programming language, enables the same results whether the registrant database contains ten subjects or 400,000.  Private Identity ensures that the speed and accuracy of the analytics are the same.

## Small Scale

### Clone Projects
    git clone git@github.com:openinfer/pb-util.git

## Python Utility

1. Make sure you have python3 installed in the system
2. Install pip3 using `sudo apt-get install python3-pip`
3. Install pip3 using `sudo apt-get install python3-opencv`
4. Move to the working directory `cd pb-util/integration_scripts`
5. Install the necessary packages using `sudo pip3 install -r requirements.txt`
6. Locate the image path which has the person images with their names as the filenames with a jpg, png, or gif extension

### Preprocess Images

Ensuring the strength of enrolls is the hallmark of Private Identity’s patented application.  A single subject image is morphed into 60 separate images, winnowed down to the superior 53.  The original image morphs by changing the rotation, flipping and modifying the colors through an image homogenization algorithm.  The algorithm compares the geometric distances between every permutation of images.   The algorithm discards images causing a geometric distances greater than a threshold.  If the result is less than 53 images morphing tries again.  If after N number of tries, the algorithm cannot find 53 valid images, the person is rejected and the files move to a rejection directory.   

Subject images are parsed out into three directories: the original directory retains the preliminary/primary image, an enroll directory and a predict directory.  Both the prediction and enroll directories contain an images sub-directory and an embeddings sub-directory.  The images sub-directory contains the morphed images and the enbeddings sub-directory contains embedding which by definition are  homomorphically encrypted.  

To preprocess images, locate the directory with the images stored with the person names as their filenames.
Then run the following command to augment the images and removing the bad embeddings which will create a 'enroll' and 'predict' sub-directories. 

 `python3 initiate_preprocess.py -input_path <input_path> -model_path ./best_face_model/`

Once the script completes all files exist in the appropriate subdirectories.

### Enroll Persons

The enroll script takes the directory structure from initiate_preprocess.py and uses the images from each person to enroll them into the system. Each person must have a minimum number of 40 images for enrolling otherwise the enroll will fail.

 `python3 enroll.py -input_path <input_path>`

Upon script completion, the system contains all enrolled users.

**Optional `-server_url` parameter can be given to enroll the user in different systems.**

**Optional `-api_key` parameter can be given to verify the api key endpoints in the system. Default value if 1962 is used if not provided**

### Predict Persons

The predict script takes the directory structure from initiate_preprocess.py and uses the images from each person to test the enroll by predicting. Each person must have a least one image to perform a prediction.

 `python3 predict.py -input_path <input_path>`

The script predict.py produces summary output and any error message.

**Optional `-server_url` parameter can be given to enroll the user in different systems.**

**Optional `-api_key` parameter can be given to verify the api key endpoints in the system. Default value if 1962 is used if not provided**


## Large Scale


## Configure cluster on your local machine
    aws eks --region $REGION update-kubeconfig --name $CLUSTER_NAME
    kubectl config use-context <cluster:arn>




Send a request to process a dataset on S3 to: 

POST: https://master.privateidentity.org/trueid/v1.1/preprocess

```
{
    "bucket": "preprocess-privateidentity" ,
    "s3_dataset_dir": "sample_images",
    "num_processes": 40,
    "server_url": "https://dev.private.id:443/trueid/v1.1",
    "slave_url": "http://slave-svc:5002/trueid/v1.1/slave_preprocess",
    (Optional)"api_key": <key>
}
```

`bucket`: the S3 bucket containing the dataset.

`s3_dataset_dir`: the path of the dataset in the bucket in S3

`num_processes`: the dataset will be processed using `num_processes` parallel requests. For example, if the dataset consists of 1000 people, and num_processes=40, that means we'll have 40 parallel requests and each request processes 1000/40 = 25 people.

`api_key`: is an optional parameter. If it is not present in JSON then a default value of 1962 will be used.

[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

# NodeJS Endpoints

## Overview 

This document explains how to utilize the NodeJS endpoints, which can handle API requests and send them back to the Python endpoints.

## Predict Overview
<br/>

The NodeJS endpoint provides an interface for prediction, and enrollment, or any other provided service. The following example illustrates the prediction process through the NodeJS server.


**Face And/Or Prediction Request -**

The format of this API call is: 

POST “/node/ptPredict”

|Parameter      |            Value|
|----------|--------------| 
|modality | The modality parameter determines the biometric: "face, voice, fingerprint" |
|api_key       |         The api string is necessary to process the api requests. Contact Private Identity to obtain the designated key |
|images[]       | The images parameter is an array of facial image files |
|audio | The audio parameter is a voice file |
|fingerprint[]  | The fingerprint is an array of fingerprint image files |

Accepted images are 224 pixels in height and width. Format the request payload as FormData. For more information visit: https://developer.mozilla.org/en-US/docs/Web/API/FormData

A Predict API request example is as follows:
```
{
    "api_key": "XXXXXXXX",
    "modality": "voice, face, fingerprint"
    "images[]": "base64 image",
    "images[]": "base64 image",
    "images[]": "base64 image", 
    "images[]": "base64 image",
    ...
    "audio": "audio file",
    "fingerprint[]": "base64 image",
    "fingerprint[]": "base64 image",
    "fingerprint[]": "base64 image", 
    "fingerprint[]": "base64 image",

}
```

**Response**

The response of a Predict request, if successful, returns enrollment data in the following format:
```
{
    "enrollment data": {
	"id": "1008023",
    },
    "message": "OK",
    "status": 0,
    "subject_id": 4,
}
```

## Enroll Overview
<br/>

The NodeJS endpoint provides an interface for prediction, and enrollment, or any other provided service. The following example illustrates the enrollment process through the NodeJS server.


**Enrollment Request -**

The format of this API call is: 

POST “/node/ptEnroll”

|Parameter      |            Value|
|----------|--------------| 
|modality | The modality parameter determines the biometric: "face, voice, fingerprint" |
|api_key       |         The api string is necessary to process the api requests. Contact Private Identity to obtain the designated key |
|images[]       | The images parameter is an array of facial image files |
|audio | The audio parameter is a voice file |
|fingerprint[]  | The fingerprint parameter is an array of fingerprint image files |

Images that are accepted are 224 pixels in height and width. Format the request payload as FormData. For more information visit: https://developer.mozilla.org/en-US/docs/Web/API/FormData

An enroll API request example is as follows:
```
{
    "api_key": "XXXXXXXX",
    "modality": "voice, face, fingerprint"
    "images[]": "base64 image",
    "images[]": "base64 image",
    "images[]": "base64 image", 
    "images[]": "base64 image",
    ...
    "audio": "audio file",
    "fingerprint[]": "base64 image",
    "fingerprint[]": "base64 image",
    "fingerprint[]": "base64 image", 
    "fingerprint[]": "base64 image",

}
```

**Response**

The response of an Enroll request, if successful, returns a new enrollment, or an error if the user is already enrolled:
```
{
     {
     "status: 0"
     "UUID:" "XXXXXX"
     "subject id:" "XXXXX"
     }
  or {
     "status: -1"
     "subject id:"User found in registry"
     "subject id:" "XXXXX"
        
}
```

## Postman Example Project
<br/>

The Postman application illustrates a use case for the API calls, such as predict. The example includes a file download at the bottom of the passage. The file download includes voice and face instances and a .json file that makes the API calls.  Use these files to demonstrate the API calls.

This is a step by step instructional on how to use postman to view the API calls and their responses:

1. Download Postman, and ensure it is functional by logging into the application and viewing the user interface

[Download Postman Here](https://www.postman.com/downloads/)
![Postman User Interface](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_1.png)
2. Download the package located here [Postman Package](https://github.com/openinfer/PrivateIdentity/blob/master/JSEndpoint/EnrollMaterialandCalls.zip). Uncompress the file for Postman to import it. 

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman2.png)

3. Import the package into Postman using the import feature and select the .json that has the API calls.
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_2.png)
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_4.png)
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_5.png)
4. The left hand side of the screen contains the API calls necessary to predict and enroll a variety of modalities.
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_6.png)
5. Select the relevant API call and then go over to the "body" tab in the center of the screen.
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_7.png)
6. Select the files you want to address. Use the files with a .jpg suffix for face or a .wav suffix for voice.  
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_8.png)
7. After file selection, process the request by clicking the "send" button.
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_9.png)
8. The request response displays on the bottom of the screen.

[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

# Customer Integrations

### DIV/HTML ###

* Built in React (pluggable)
* Embed as a DIV
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/DIV-HTML)

### PaaS (Web Tier) ###

* Docker Image
* Runs elastic, load balanced, fault tolerant K8s
* Connects to a Server Side Component managed by Private Identity
* Runs on any cloud (AWS, GCP, Azure)
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/PaaS-Web-Application)

### PaaS (Entire Tier) ###

* Docker Images
* Runs elastic, load balanced, fault tolerant K8s
* Includes Server Side Component
* Runs on any cloud (AWS, GCP, Azure)
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/cluster-setup) 

### SaaS (Open) ###

* Entirely managed and run on AWS by Private Identity
* API Key access
* Fully elastic, load balanced, fault tolerant

### SaaS (Dedicated for Customer) ###

* Entire K8s cluster dedicated to Customer
* Entirely managed and run on AWS by Private Identity
* API Key access
* Fully elastic, load balanced, fault tolerant

### RESTful API ###

* Receives fully homomorphic encryption (FHE) payload from client device
* Returns UUIDs
* Runs all ciphertext and plaintext business methods
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/Predict-Enroll-library)

### Encryption Engine ###

* Cluster for biometric ingestion
* Elastic, load balanced, fault tolerant K8s, autoscale to 1000s of nodes
* Javascript API and RESTful API
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/Client-Cluster-setup)

### W3C/FIDO2 WebAuthn (polymorphic interface) ###

* Authenticator enrollment -> how enrolling on /demo/ shows your enroll data in /webauthn 
* Authenticator authentication -> how prediction on /demo/ shows your enroll data in /webauthn

### Photo ID Verification ###

* DIV/HTML -> https://private.id/demo/?apiKey=####&passport=true&version=0.9. (Request APIKey from Administrator)
* The link requests a level 2 enrollment, then takes a face prediction, then appends a document verification onto that predicted enrollment. 
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/Verified-Enroll)

[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

# The Maryland Test Facility Public Code Repository

Public code that supports this software integration at the [MdTF Website](https://github.com/TheMdTF/mdtf-public)

## Rally2-matching-system

MdTF has a rally2-matching-system that performs the comparison of biometric types and evaluates the performance of the matching system.

## API

The API definition for matching systems can be found in the [Rally2-Matching-System](https://github.com/TheMdTF/mdtf-public/tree/master/rally2-matching-system/api)

Three API Calls have been exposed:

### 1. `GET /v1/info`

This API call produces a JSON output that explains the information of the algorithm like version, system requirements, and contact details.

_Sample Output:_

`{
    "AlgorithmName": "Private ID Matching Algorithm",
    "AlgorithmType": "Face & Face Mask",
    "AlgorithmVersion": "1.0.0",
    "CompanyName": "Private ID",
    "RecommendedCpus": 4,
    "RecommendedMem": 4096,
    "TechnicalContactEmail": "scott@private.id"
}`


### 2. `POST /v1/create-template`

This API call is responsible for consuming the image data and outputs one or more fully homomorphic encrypted (FHE) payloads. Each FHE payload is a positional arrays of 128 floating-point numbers generated by a custom mobile embedding DNN.  

The recognition system uses FHE payloads to calculate a similarity (geometric distance) between sets of vector data in their encrypted form. The FHE payloads are returned in the form of a base64 encoded string.

FHE payloads are generated for all the images that will be used for comparison

> The API consumes an ImageData in the form of base64 png image string and produces a base64 template string

_Sample Output:_

`{
    "Template": "WzAuMDUwMDcyMjk3NDUzODgwMzEsMC4wNjUwNTE0MjE1MjMwOTQxOCwwLjAxMTI1MjIyOTEwMTk1NTg5LDAuMDU5ODE1MzkxODk4MTU1MjEsLTAuMTUxMjE1NDA0MjcyMDc5NDcsLTAuMTQ5NTE4MTAyNDA3NDU1NDQsMC4wNTA2NzE3NDUwOTE2NzY3MSwtMC4wNDU3NDU4ODY4NjIyNzc5ODUsMC4xMTM2MDg2MzU5NjIwMDk0MywwLjAyOTE5MjgwNzE1Mjg2NzMxNywwLjAzOTM5MDUzNzg4NzgxMTY2LC0wLjEwMTk0ODQxNzcyMzE3ODg2LDAuMDU3MTY1MzE3MjM3Mzc3MTcsMC4wODczNTUzMjMxMzU4NTI4MSwtMC4wMDAyMTMwNzk3OTQ3NzU2OTQ2LDAuMDgyODEyODgyOTU5ODQyNjgsMC4wNDI0OTUwNDU4MTA5Mzc4OCwtMC4xMjIyNjg5NzQ3ODEwMzYzOCwtMC4xMzc3NDUwOTcyNzk1NDg2NSwwLjE2MTk5OTMyOTkyNDU4MzQ0LDAuMDcxMzQ3MzkzMDk1NDkzMzIsLTAuMD=="
}`


### 3. `POST /v1/compare-list`

This API call performs the comparison of the main FHE payloads with all the requested FHE payloads and produces a `Score` and `Normalized Score` for every 1:1 comparison.

`SingleTemplate` holds the template data for comparing with all the other data in the `TemplateList` array. 

The system produces a `ComparisonArray` where for each data in the `TemplateList`, a score and a normalized score will be produced.

_Sample Output:_

`[
    {
        "NormalizedScore": 0.5830713966448668,
        "Score": 0.4269286033551331
    },
    {
        "NormalizedScore": 0,
        "Score": 1.2406864489270033
    }
]`

### Sample Output from MdTF

```
test-routine.sh face 172.17.0.2

Rally Matching System Test Routine Started...
Mode:  face
Host:  172.17.0.2
Port:  8080 

Creating Template for S223-01-t10_01.png
Creating Template for S223-03-t10_01.png
Creating Template for S309-04-t10_01.png
Creating Template for S309-05-t10_01.png
Creating Template for S324-01-t10_01.png
Creating Template for S324-02-t10_01.png
Created 6 templates from 6 images
Average extraction time 425.1666666666 ms per extraction

Compare list generated 6 scores
Compare list generated 6 scores
Compare list generated 6 scores
Compare list generated 6 scores
Compare list generated 6 scores
Compare list generated 6 scores
Performed 36 comparisons
Average comparison time 3.6388888888 ms per comparison

Score Matrix:
0.000 0.480 0.997 0.900 0.958 0.876 
0.480 0.000 0.931 0.839 0.931 0.859 
0.997 0.931 0.000 0.475 1.086 1.088 
0.900 0.839 0.475 0.000 1.040 1.010 
0.958 0.931 1.086 1.040 0.000 0.352 
0.876 0.859 1.088 1.010 0.352 0.000 

Normalized Score Matrix:
1.000 0.530 0.013 0.110 0.052 0.134 
0.530 1.000 0.079 0.171 0.079 0.151 
0.013 0.079 1.000 0.535 0.000 0.000 
0.110 0.171 0.535 1.000 0.000 0.000 
0.052 0.079 0.000 0.000 1.000 0.658 
0.134 0.151 0.000 0.000 0.658 1.000 

Rally Matching System Test Routine Complete
```


[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

# FAQ

**Q : What is a biometric?**

Biometrics is the technical term for body measurements and calculations. It refers to metrics related to human characteristics.

Biometrics authentication (or realistic authentication) is used in computer science as a form of identification and access control. It is important to note that privacy with biometrics is essential since biometric, in contrast to password, cannot be reset.

**Q : What is facial recognition?**

A facial recognition is face recognition technology measures and matches the unique characteristics for the purposes of identification or authentication.

Facial recognition is a category of biometric software that maps an individual's facial features mathematically and stores the data as a faceprint. The software uses deep learning algorithms to compare a live capture or digital image to the stored faceprint in order to verify an individual's identity.

**Q : What is a CNN?**

Yann LeCun and Yoshua Bengio introduced the concept of CNNs in 1995. A con-volutional neural network is a feed-forward network with the ability of extracting topological properties from the input image. It extracts features from the raw image and then a classifier classifies extracted features. CNNs are invariance to distortions and simple geometric transformations like translation, scaling, rotation and squeezing.

Convolutional Neural Networks combine three archit ectural ideas to ensure some degree of shift, scale, and distortion invariance: local receptive fields, shared weights, and spatial or temporal sub-sampling. The network is usually trained like a stan-dard neural network by back propagation.

**Q : What is a fully connected neural network?**

In information technology, a neural network is a system of hardware and/or software patterned after the operation of neurons in the human brain. Neural networks -- also called artificial neural networks -- are a variety of deep learning technologies. Commercial applications of these technologies generally focus on solving complex signal processing or pattern recognition problems. Examples of significant commercial applications since 2000 include handwriting recognition for check processing, speech-to-text transcription, oil-exploration data analysis, weather prediction and facial recognition.

**Q : What is unique about Private Indentity Identification and Authentication?**

Biometrics have a long-held hope of replacing passwords by establishing a non-repudiated identity and providing authentication with convenience. Convenience drives consumers toward biometrics-based access management solutions. Unlike passwords, biometrics cannot be script-injected; however, biometric data is considered highly sensitive due to its personal nature and unique association with users. Biometrics differ from passwords in that compromised passwords may be reset. Compromised biometrics offer no such relief. A compromised biometric offers unlimited risk in privacy (anyone can view the biometric) and authentication (anyone may use the biometric). Standards such as the Biometric Open Protocol Standard (BOPS) (IEEE 2410-2016) provide a detailed mechanism to authenticate biometrics based on pre-enrolled devices and a previous identity by storing the biometric in encrypted form. This solution allows authentication and identification to occur in up to polynomial time, allowing for search in encrypted biometric stores with speed, accuracy and privacy.

**Q : What is enrollment?**

The act of signing/registration people up for participation is enrollment.

Since we have little control over devices such as cameras or sensors, the biometric template arrives as plaintext. If we encrypt it immediately and only process it as ciphertext, we have the maximum practical level of privacy. An important part of offering this highest level of privacy is a one-way encryption algorithm, meaning that given ciphertext, there is no mechanism to get to the original plaintext. Many one-way encryption algorithms exist, such as MD5 and SHA-512. However, these algorithms are not homomorphic. This means we cannot do a closeness match between two ciphertext vectors using Euclidean measurements. Private Identity offers a general purpose solution that produces biometric ciphertext that is Euclidean-measurable. We do this using a Neural Network. We then apply a classification algorithm to allow for one-to-many identification. This solution maximizes privacy and runs between O(1) and O(log⁡(n)) time.

Enrollment is the act of introducing a Subject to the indentification or authenication system. Enrollment, for Open Inference, is the process of extracting features and training a neural network for a particular subject. For Enrollment to work reliably, we give as mnay biometric instances as possible. We use in excess of 10 images, which the software morphs into 250 distinct images. The system then trains on 250 images. All of the training and images are encrypted BEFORE any form of training guaranteeing full privacy.

**Q : What is search?**

Search is a prediction across a trained neural network. Artificial neural networks respond to a prediction request by querying a neural network. The network responds with an accurate response as to who is the subject based on an encrypted search.

**Q : What is voting?**

For voting, we take several searches and the correct answer is the response with plurality. For example, we take 3 facial images. The neural network is 99 percent accurate. So we use the three images and simultaneously search. There is a 1 percent chance we are wrong, voting makes our result 100 percent accurate.

**Q : What is tensorflow?**

TensorFlow is an open source software library for numerical computation using data flow graphs. Nodes in the graph represent mathematical operations, while the graph edges represent the multidimensional data arrays (tensors) communicated between them. The flexible architecture allows you to deploy computation to one or more CPUs or GPUs in a desktop, server, or mobile device with a single API. TensorFlow was originally developed by researchers and engineers working on the Google Brain Team within Google's Machine Intelligence research organization for the purposes of conducting machine learning and deep neural networks research, but the system is general enough to be applicable in a wide variety of other domains as well.

**Q : What is a feature vector?**

A feature vector is an n-dimensional vector of numerical features that represent some object. Many algorithms in machine learning require a numerical representation of objects, since such representations facilitate processing and statistical analysis.

**Q : What is alignment?**

For biometrics to train properly the biometric itself must make it easy to train. If all biometrics are similarly reprsented, then the training is more accurate. We do thisby preprocessing the biometric which involes aligning.

In computer vision, alignment: is the process of finding the spatial mapping, i.e. elements in one image into meaningful correspondence with elements in a second image.

**Q : What is cropping?**

Cropping is the removal of the outer parts of an image to improve framing, accentuate subject matter or change aspect ratio.







