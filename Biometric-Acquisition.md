## Biometric Acquisition

Private Identity provides a Web client and two elastic services to support biometric acquisition and high-throughput FHE transformation at the edge. This enables Private Identity to accept a variety of synchronous and asynchronous biometric inputs (i.e. phones, Webcams, legacy devices and applications, and plaintext images, video, audio and input from third-party biometric acquisition systems) without any requirement to store, transmit or use plaintext biometrics.

***

### Facial Recognition Algorithm

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(8).png)

[_Biometric Ingestion and Helper DNN's_](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs)

#### How does it work?



The software captures images from the user, and in these images an API is detecting the facial landmarks, such as the eyes, mouth, nose and converts this image probe into it's geometric primitives. Afterwards if a face is detected, it is cropped, and aligned to be passed through a eye blink detection and a glasses detection. Then if the image passes the conditions of; no glasses, a proper face is detected, and has a high enough quality, then it is augmented. This augmentation will flip, rotate, and modify the lighting of the photo, to create a dataset of images for the user. This dataset is then encrypted and converted into an FHE payload. This one way payload is sent to the cloud as an embedding, and the previously captured images and biometrics are discarded. 

#### What are the requirements for a facial enrollment?

Utilizing a browser-based camera (any computer, tablet or smartphone) to capture at least 10 images in the Private Identity app for enrollment. If any of the images are not suitable for training, a message is returned and the image is removed. The user must add more images until at least 10 images meeting the minimum quality standards have been provided. The user will also need to have been supplied a valid API key in order to have access to the software.

The Enroll process captures the face images continuously and compares it with the existing enrolled subjects. If no enrolled subjects are found the system extracts the features from the images and stores the features in the system.

[Demonstration for Facial Enrollment](https://youtu.be/_MxgytMoMus)

#### What are the requirements for facial prediction?

Once the user successfully enrolls in the system, they can verify their identity by predicting with their modality. The same process of scanning the face using the webcam is used for prediction. Once sufficient images are captured, the software extracts the features from the images and sends it to the model for identifying the person. Then, the results will be displayed in the frontend identifying the user that the software has recognized. The user will also need to have been supplied a valid API key in order to have access to the software.

[Demonstration for Facial Prediction](https://youtu.be/lfaCKwHxgUM)

</br>

***

### Face and Mask Algorithm 

#### How does it work?

The algorithm for the face and mask recognition is virtually the same as the facial algorithm, however for mask there is an additional DNN check for whether a mask is detected. The mask check is enabled in the URL by the user using the parameter, "maskCheck=true" and by default it is false. If the parameter is enabled, the user can use a mask that covers their mouth and nose during the prediction, and during the enrollment. However a clear face enrollment is more accurate for mask predictions. 
</br>

### Fingerprint Recognition
</br>

### Voice Recognition
</br>
