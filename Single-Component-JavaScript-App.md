# Demo Video

# Summary
> Insert block diagram here showing where it fits in the system

* Preserves privacy by synchronously acquiring and FHE transforming biometric data at the edge
* Easy to deploy with no requirement to install additional software, plugins or extensions
* Built with Javascript, TensorFlow.js and an ensemble of helper DNNs
* Works on commodity devices without sacrificing performance 
* Runs on 90% of all modern devices

This Javascript client provides users with massively horizontally scalable, browser-based biometric enrollment, identity, MFA and account recovery in a convenient Web experience that operates on more than 90% of all browsers, platforms and devices. The Web client uses on-device pre-trained TensorFlow models to acquire, validate, align, crop, transform and 1-way encrypt the biometric.

The client does not require on-device training and has no requirement for expensive hardware, cameras, GPUs, batteries or RAM. Devices with multi-threaded kernels operate in millisecond response time. Devices equipped with GPUs and Edge TPUs operate 70-100x faster. Less capable devices operate by offloading processing to Node.js using the “whereToProcess=nodeServer” URL parameter.

The Web client acquires the biometric using an ensemble of pre-trained TensorFlow™ models. These models offer the opportunity for higher accuracies and lower overhead than traditional procedural programming. These small, convenient Helper DNNs use YOLO architecture, are 10kB to 100kB in size and process in <10ms with accuracies >99%.

## Architecture Discussion
## Helper DNNs
The Web client operates using helper DNNs.  For face and fingerprint recognition, the client uses the [Face and Fingerprint Geometry DNN](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-and-face-wmask-geometry-detection-dnn) to identify specific face landmarks and boundaries; [Face and Fingerprint Validation DNN](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face--fingerprint-validation-dnns) to ensure appropriate lighting and clarity and support crop and align; [Eyes Open/Closed](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#eyes-openclosed-detection-dnn-spoofing-prevention) for passive liveness in face recognition; [Eyeglasses On/Off](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#eyeglasses-onoff-detection-dnn) to prevent false negatives in face recognition; and [Data Augmentation](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#facial-and-fingerprint-data-augmentation) to increase the entropy of the enrollment set. 

For voice biometric acquisition, helper DNNs isolate singular voices. Additional processing includes [Voice Validation DNN](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-validation-dnn) to validate the isolated voice biometric sample, [Voice Input Segmentation](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-input-segmentation) to acquire voice samples using a sliding 10ms window across one second of input; [Voice Pulse Code Modulation Transformation](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-pulse-code-modulation-pcm-transformation) to down sample each segment to 2x the frequency range; and [Voice Fast Fourier Transform](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-fast-fourier-transformation-fft) to convert the signal from the time domain to the frequency domain.

## FHE Transform at the Edge
The Web client then uses a [face, face with mask, fingerprint](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-facemask-and-fingerprint-embedding-dnns) or [voice](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-embedding-dnn) embedding DNN to FHE transform each plaintext biometric sample. The embedding DNN operates **on the local device**.  Once the biometric sample is FHE transformed, it is then immediately deleted. Embeddings (a/k/a "FHE payloads") are more accurate than plaintext biometric data. Embeddings also reduce network traffic to the cloud by 99.5%. Thus, there is no need to retain plaintext data. Deleting the plaintext (without transmitting, storing or using plaintext data) guarantees user privacy.

## Web Applications
Biometric authentication is only as effective as the original source identifiers that are captured, stored and referenced.  This is the enrollment process, a form of registration that also “trains” the browser and the server to which it’s linked to guarantee accurate recognition of subjects.  Whatever type of biometric authentication is engaged, face, voice or fingerprint, it’s imperative to enroll quality source material to ensure verification.

_Enrollment is just another term for training._

### Face Enroll

Utilizing a browser-based camera (any computer, tablet or smartphone) to capture at least 10 images in the Private Identity app for enrollment.  If any of the images are not suitable for training, a message is returned and the image is removed. The user must add more images until at least 10 images meeting the minimum quality standards have been provided.

The Enroll process captures the face images continuously and compares it with the existing enrolled subjects. If no enrolled subjects are found the system extracts the features from the images and stores the features in the system.

[[https://github.com/openinfer/PrivateIdentity/blob/master/images/begin.png]]

System automatically checks for the glasses if worn by the user. In that case system rejects the images and waits for the user to recapture images again.

[[https://github.com/openinfer/PrivateIdentity/blob/master/images/no_glasses.png]]

Once the user passes the face capture, the user will be asked to accept the User Agreement policy followed by the Information filling. The information provided by the user will be used to idetify the subject enrolled.

Enroll User Agreement | Enroll Information
---|---
[[https://github.com/openinfer/PrivateIdentity/blob/master/images/enroll_ua.png]]|[[https://github.com/openinfer/PrivateIdentity/blob/master/images/enroll_user.png]]

Once the user successfully enrolls, a right check mark will be displayed to the user to notify the completion

[[https://github.com/openinfer/PrivateIdentity/blob/master/images/enroll_complete.png]]

<br/>

If you want face prediction to be more accurate, you can use the URL parameter `profileFaceEnroll`. This parameter will take profile face pictures during enroll. 


### Face Predict

Once the user successfully enrolls in the system, they can verify their identity by predicting with their modality. The same process of scanning the face using the webcam is used for prediction. Once sufficient images are captured, the software extracts the features from the images and sends it to the model for identifying the person. Then, the results will be displayed in the frontend identyfing the user that the software has recognized.

#### Capture Face
[[https://github.com/openinfer/PrivateIdentity/blob/master/images/capture_face.png]]

#### Prediction Result

Private Identity’s facial recognition app detects a subject, determines if its image resides in the database instantaneously and, finally, takes whatever further action is required, allowing access only for an approved user.

[[https://github.com/openinfer/PrivateIdentity/blob/master/images/predict_result.png]]

### Voice Enroll and Predict

Utilizing biometric voice technology, a phrase spoken by a subject is captured and then compared with a previously stored voiceprint. Identifying an individual by voice is a complex task because the human voice is influenced by multiple characteristics, physical, behavioral and emotional.  A voiceprint is algorithmically derived based on an analysis of these factors.

Upon enrollment, Private Identity’s biometric software records and registers the subject’s voice sample. The statistical algorithm analyzes the many distinctive characteristics of the voice and creates a voiceprint or biometric model which is then encrypted and stored in a secure database.

When a subject attempts subsequent logins, the system automatically creates a voice model and compares it with the stored sample. If successful authentication occurs, the subject is allowed access.  The human voice is as unique an identifier as the retina, iris or fingerprints.  No matter how well aspects of pitch, cadence and intonation are attempted via impersonation, it is impossible to fool the referenced voiceprint in Private Identity’s database.

When the biometric voice option is enabled, the user will be requested to speak live sentences that are displayed in the browser.

The browser records the spoken voice and extracts the features. These features are used in the same way as face to aide the enroll / predict process.

#### A sample sentence displayed in the browser

[[https://github.com/openinfer/PrivateIdentity/blob/master/images/voice_2.png]]

### Fingerprint Enroll

_System under progress._

Fingerprint scanning is the most ubiquitous biometric technology, utilized for everything from access to cellphones and personal computers to entry at high-security installations.  It used to be the “bad guys” who were fingerprinted. Today, this unique human characteristic provides corporations, government and individuals with an immediate, fool-proof tool for identity authentication.

During enrollment, or initial capture of a subject’s fingerprint, each print is analyzed for the unique features and lines found on every individual’s fingers. The software app measures the distances and angles between these features and then uses an algorithm to turn this information into a unique numeric code. Comparing fingerprints then becomes a process of comparing codes. If the codes match, the prints match, and the subject is granted access.

When using a fingerprint to verify a subject's identity, the user will be asked to display their thumb for webcam image capture. A guided area will be displayed in the browser to cover the fingerprint region. Once the systems approves the quality of the image, features extracted from the fingerprint image will be sent to the system for enroll and predict.

[[https://github.com/openinfer/PrivateIdentity/blob/master/images/fingerprint.png]]