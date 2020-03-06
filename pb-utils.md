[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)
<br/>

Biometric authentication is only as good as the quality of its enrolls (subject image registration).  Registration and log-in is browser-based, an individual can enroll via the camera on their computer, tablet or phone and requires no external apparatus. 

What differentiates Private Identity’s proprietary application is that it scales to enterprises of any size.  When an individual user enrolls, the entire process is encaged within the browser, processing the captured images and uploading them to the server where all information is classified for future reference in the verification process.  The utility of Python, a high-level, general-purpose programming language, enables the same results whether the registrant database contains ten subjects or 400,000.  Private Identity ensures that the speed and accuracy of the analytics are the same.

## Small Scale

### Clone Projects
    git clone git@github.com:OpenInference/pb-util.git

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

Optional -server_url parameter can be given to enroll the user in different systems.

### Predict Persons

The predict script takes the directory structure from initiate_preprocess.py and uses the images from each person to test the enroll by predicting. Each person must have a least one image to perform a prediction.

 `python3 predict.py -input_path <input_path>`

The script predict.py produces summary output and any error message.


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
    "server_url": "https://dev.privateidentity.org:443/trueid/v1.1",
    "slave_url": "http://slave-svc:5002/trueid/v1.1/slave_preprocess"
}
```

`bucket`: the S3 bucket containing the dataset.

`s3_dataset_dir`: the path of the dataset in the bucket in S3

`num_processes`: the dataset will be processed using `num_processes` parallel requests. For example, if the dataset consists of 1000 people, and num_processes=40, that means we'll have 40 parallel requests and each request processes 1000/40 = 25 people.




