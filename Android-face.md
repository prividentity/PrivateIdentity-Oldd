## Android facial recognition

<br/><br/>

[Android-face git repository](https://github.com/openinfer/android-face)


The android application is a sample application that exercise the complete BOPS API.

<img src="http://openinfer.com/images/openinfer_android1.png" width="30%">

<br/><br/>

**Sign Up is Just Another Term for Training**

<img src="http://openinfer.com/images/openinfer_android2.png" width="30%">

1. The user must provide name, gender, age and address. 
2. Then click the camera. The android application uses a phone camera to take 10 images for enrollment. Each image is morphed 30 times. This creates at least 300 images for training. The images will be automatically uploaded to the BOPS Server. Click Ok to proceed or cancel to retake images.

Our enrollment interface is configured to link Personally Identifiable Information (PII) to an unencrypted biometric input. All downstream processing is on encrypted biometrics. The enrollment interface is configured to trigger deletion of the unencrypted biometric information.

<br/><br/>

**Login (Search)**
 
<img src="http://openinfer.com/images/openinfer_android3.png" width="30%">

The search function takes in 3 biometric images and check for Liveness, uses a pretrained machine learning model to make predictions for each image, then uses a voting method to determine which prediction is correct. If the number of images is greater than 1, the search function performs a vote, where a pluraltiy algorithm determines the correct subject. Once predicted, the PII information for the Subject is shown.