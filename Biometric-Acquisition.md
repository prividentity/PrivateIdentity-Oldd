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

![insert diagram](Face_Mask_Diagram)

#### How does it work?

The algorithm for the face and mask recognition is virtually the same as the facial algorithm, however for mask there is an additional DNN check for whether a mask is detected. The mask check is enabled in the URL by the user using the parameter, "maskCheck=true" and by default it is false. If the parameter is enabled, the user can use a mask that covers their mouth and nose during the prediction, and during the enrollment. However a clear face enrollment is more accurate for mask predictions. 

#### What are the requirements for face and mask enrollment?

The user has to define the parameter to enable the mask Check, because by default it is disabled. Utilizing a browser-based camera (any computer, tablet or smartphone) to capture at least 10 images in the Private Identity app for enrollment. If any of the images are not suitable for training, a message is returned and the image is removed. The user must add more images until at least 10 images meeting the minimum quality standards have been provided. The user will also need to have been supplied a valid API key in order to have access to the software.

The Enroll process captures the face images continuously and compares it with the existing enrolled subjects. If no enrolled subjects are found the system extracts the features from the images and stores the features in the system.

[Demonstration for Face and Mask Enrollment](youtube.com)

#### What are the requirements for face and mask prediction?

The user has to define the parameter to enable the mask Check, because by default it is disabled. Once the user successfully enrolls in the system, they can verify their identity by predicting with their modality. The same process of scanning the face using the webcam is used for prediction. Once sufficient images are captured, the software extracts the features from the images and sends it to the model for identifying the person. Then, the results will be displayed in the frontend identifying the user that the software has recognized. The user will also need to have been supplied a valid API key in order to have access to the software.

[Demonstration for Face and Mask Prediction](youtube.com)

</br>

***

### Fingerprint Recognition

_System under progress._

![Fingerprint recognition workflow](https://github.com/openinfer/PrivateIdentity/blob/master/images/Workflow%20-%20Fingerprint.png)

[_Biometric Ingestion and Helper DNN's_](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#FACE-\&-FINGERPRINT-VALIDATION-DNNs)

#### How does it work?

During enrollment, or initial capture of a subject’s fingerprint, each print is analyzed for the unique features and lines found on every individual’s fingers. The software app measures the distances and angles between these features and then uses an algorithm to turn this information into a unique numeric code. Comparing fingerprints then becomes a process of comparing codes. If the codes match, the prints match, and the subject is granted access. The algorithm is the same process for facial recognition, the image is processed, augmented, encrypted, transmitted to the server, and then the biometrics are discarded.

When using a fingerprint to verify a subject's identity, the user will be asked to display their thumb for webcam image capture. A guided area will be displayed in the browser to cover the fingerprint region. Once the systems approves the quality of the image, features extracted from the fingerprint image will be sent to the system for enroll and predict.

#### What are the requirements for a fingerprint enrollment?

Utilizing a browser-based camera (any computer, tablet or smartphone) to capture at least 10 images in the Private Identity app for enrollment. If any of the images are not suitable for training, a message is returned and the image is removed. The user must add more images until at least 10 images meeting the minimum quality standards have been provided. The user will also need to have been supplied a valid API key in order to have access to the software.

[Demonstration for a Fingerprint Enrollment](youtube.com)

#### What are the requirements for a fingerprint prediction?

Once the user successfully enrolls in the system, they can verify their identity by predicting with their modality. The same process of scanning the finger using the webcam is used for prediction. Once sufficient images are captured, the software extracts the features from the images and sends it to the model for identifying the person. Then, the results will be displayed in the frontend identifying the user that the software has recognized. The user will also need to have been supplied a valid API key in order to have access to the software.

[Demonstration for a Fingerprint Prediction](youtube.com)
</br>

***

### Voice Recognition

![Voice recognition workflow](https://github.com/openinfer/PrivateIdentity/blob/master/images/Workflow%20-%20Voice.png)

[_Biometric Ingestion and Helper DNN's_](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#VOICE-INPUT-SEGMENTATION)

#### How does it work?

Upon enrollment, Private Identity’s biometric software records and registers the subject’s voice sample. The statistical algorithm analyzes the many distinctive characteristics of the voice and creates a voiceprint or biometric model which is then encrypted and stored in a secure database.

When a subject attempts subsequent logins, the system automatically creates a voice model and compares it with the stored sample. If successful authentication occurs, the subject is allowed access. The human voice is as unique an identifier as the retina, iris or fingerprints. No matter how well aspects of pitch, cadence and intonation are attempted via impersonation, it is impossible to fool the referenced voiceprint in Private Identity’s database.

#### What are the requirements for a voice enrollment?

The user will utilize a browser-based microphone (any computer, tablet or smartphone) to capture at least 1 voice segment in the Private Identity app for enrollment. If any of the voice segments are not suitable for training, a message is returned and the audio is removed. The user must add more voice segments until at least 1 voice segment meets the minimum quality standards that have been provided. The user will also need to have been supplied a valid API key in order to have access to the software.


[Demonstration for a Voice Enrollment](youtube.com)

#### What are the requirements for a voice prediction?

Once the user successfully enrolls in the system, they can verify their identity by predicting with their modality. The same process of recording the voice using the microphone is used for prediction. Once sufficient voice segments are captured, the software extracts the features from the voice segments and sends it to the model for identifying the person. Then, the results will be displayed in the frontend identifying the user that the software has recognized. The user will also need to have been supplied a valid API key in order to have access to the software.

[Demonstration for a Voice Prediction](youtube.com)
</br>
