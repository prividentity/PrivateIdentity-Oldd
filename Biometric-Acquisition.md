# Biometric Acquisition
</br>

* _Private Identity MFA_ ™ provides massively horizontally scalable, synchronous Web browser client for user identification, authentication, MFA and Account Recovery

* _Encryption Engine_ ™ provides asynchronous, elastic high-throughput FHE transform enrollment and identification service that installs anywhere

* _Private Identity Search_ ™ provides asynchronous, elastic high-throughput FHE transform identification service that installs anywhere 

Private Identity provides a Web client and two elastic services to support biometric acquisition and high-throughput FHE transformation at the edge. This enables Private Identity to accept a variety of synchronous and asynchronous biometric inputs (i.e. phones, Webcams, legacy devices and applications, and plaintext images, video, audio and input from third-party biometric acquisition systems) without any requirement to store, transmit or use plaintext biometrics.  ￼

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(10).png)

The _Private Identity MFA_ Web client provides users with a massively scalable, convenient, browser-based enrollment, identity, MFA and account recovery experience that operates on more than 90% of all browsers, platforms and devices. 

The _Encryption Engine_ service provides high-throughput, high-demand identification tasks with unlimited asynchronous throughput for face, face with mask, fingerprint and voice enrollment and identification using elastic, load-balanced, fault-tolerant Kubernetes clusters. 

Similarly, the _Private Identity Search_ service provides high-throughput, high-demand identification tasks with unlimited asynchronous face, face with mask, fingerprint and voice identification using elastic, load-balanced, fault-tolerant Kubernetes clusters. 

The Web client, Encryption Engine and Private Identity Search use an ensemble of pre-trained TensorFlow™ models to detect and recognize faces (50ms), fingerprints (50ms) and voices (100ms) with high accuracy.

### Web Client Biometric Acquisition

* Uses TensorFlow.js and an ensemble of helper DNNs to acquire and FHE transform each biometric 

* Edge computing provides for massively horizontal scalability 

* Works on commodity devices without sacrificing performance 

The Private Identity MFA Web client provides users with massively horizontally scalable, browser-based biometric enrollment, identity, MFA and account recovery in a convenient Web experience that operates on more than 90% of all browsers, platforms and devices. The Web client uses on-device pre-trained TensorFlow models to acquire, validate, align, crop, transform and 1-way encrypt the biometric. ￼

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(9).png)

The Web client does not require on-device training and has no requirement for expensive hardware, cameras, GPUs, batteries or RAM. Devices with multi-threaded kernels operate in millisecond response time. Devices equipped with GPUs and Edge TPUs operate 70-100x faster. Less capable devices operate by offloading processing to Node.js using the “whereToProcess=nodeServer” URL parameter.  

The Web client acquires the biometric using an ensemble of pre-trained TensorFlow™ models.  These models offer the opportunity for higher accuracies and lower overhead than traditional procedural programming.  These small, convenient Helper DNNs use YOLO architecture, are 10kB to 100kB in size and process in <10ms with accuracies >99%.

Each biometric modality requires its own helper DNNs.  For face and fingerprint we use the Face and Fingerprint Geometry model to identify specific face landmarks and boundaries; Face and Fingerprint Validation model to ensure appropriate lighting and clarity and support crop and align; Eyes Open/Closed for passive liveness in face recognition; Eyeglasses On/Off to prevent false negatives in face recognition; and Data Augmentation to increase the entropy of the enrollment set. 

For voice biometric acquisition, helper DNNs isolate singular voices. Additional processing includes Voice Input Segmentation to acquire voice samples using a sliding 10ms window across one second of input; Voice Pulse Code Modulation Transformation to down sample each segment to 2x the frequency range; and Voice Fast Fourier Transform to convert the signal from the time domain to the frequency domain.  

#### Face, Face+Mask and Fingerprint Geometry Detection DNNs

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(8).png)

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(7).png)


 The Face Geometry Detection DNN accurately locates face(s) in an image by transforming each image into geometric primitives and measuring the relative position, width, and other parameters of eyes, mouth(s), nose(s), and chin(s). Likewise, the Fingerprint Geometry Detection DNN accurately locates finger(s) in an image by transforming each image into geometric primitives and measuring each finger’s relative position, width, and other parameters.  Each DNN returns X and Y coordinates of each modality in an image, video frame or video stream. 

#### Face and Fingerprint Validation DNNs

The Face Validation DNN tightly aligns, crops and accurately validates each frontalized face input image. Likewise, the Fingerprint Validation DNN tightly aligns, crops and accurately validates each fingerprint input image. Each DNN returns a validation score between 0 to 100, where 100 is a perfect image.  

#### Face+Mask On/Off Detection DNN

The face mask detection algorithm determines if a subject is wearing a mask.  Masks used during enrollment lower subsequent prediction performance. The Face+Mask On/Off Detection DNN accepts one frontalized face input image returns a value 0 to 100, where 0 is mask off and 100 is mask on. The URL parameter for enrollment and prediction “maskCheck=true” provides real-time instructions to the user to remove the mask or can be set to automatically select the Face+Mask Embedding DNN. 

#### Eyeglasses On/Off Detection DNN

The eyeglass detection algorithm determines if a subject is wearing eyeglasses before allowing enrollment. Eyeglasses used during enrollment lower subsequent prediction performance. The Eyeglasses On/Off Detection DNN accepts one frontalized face input image returns a value 0 to 100, where 0 is eyeglasses off and 100 is eyeglasses on. The URL parameter for enrollment and prediction “eyeGlassCheck=true” provides real-time instructions to the user to remove eyeglasses.   

#### Eye Geometry Detect DNN

The Eye Geometry Detection DNN accurately locates eye(s) in an image by transforming each frontal facial image into geometric primitives and measuring relative position. The DNN returns X,Y coordinates of each eye in an image, video frame or video stream.  

#### Eyes Open/Closed Detection DNN (Spoofing Prevention)

The Eyes Open/Closed DN provides real-time passive facial liveness.  This algorithm mitigates risk of a photo spoofing attack during unattended operation. The DNN receives an input image of an eye and outputs a validation score between 0 and 100, where 0 is eyes closed and 100 is eyes open. The user cannot proceed until the detection of a pair of eye-open/eye-closed events. A URL parameter “faceLiveness=true” allows the overriding of default functionality by enabling the eye-blink check. 

#### Facial and Fingerprint Data Augmentation

Data augmentation generalizes the enrollment, improves accuracy and performance during subsequent prediction and allows the DNN to handle real-world conditions. Every enrollment requires >50 biometric input images to maintain accuracy and performance. The algorithm augments all valid input images to reach or exceed 50. The set of images are then broadened to add boundary conditions to generalize the enrollment.  The broadening includes enhanced image rotations and flips, and color and lighting homogenizations.  Augmentations must increase the distance metric (Euclidean distances or cosine similarity) but not surpass class boundaries. The algorithm removes any images that exceed class boundaries. The remaining images challenge the distance metric boundaries without surpassing them.  

If only one image is available for enrollment, the Encryption Engine will augment the frontal facial input image 60 times, remove the outliers and then enroll the user. The Web client captures 8 images, morphs each image 9 times, removes any outliers and then enrolls the user.  

Enrollment requires >50 augmented biometric input images to maintain the health, accuracy and performance of the recognition algorithm. The Encryption Engine accepts biometric input image(s), morphs and homogenizes the lighting and contrast once, and discards the original images. 

There is no intrinsic requirement to morph images for prediction.  However, we find that homogenized images perform better than non-homogenized images. Image homogenization occurs through convenience libraries in Python and JavaScript. For prediction, the Web client captures 3 images, morphs and homogenizes the lighting and contrast once, and discards the original images. 

#### FACE, FACE+MASK, AND FINGERPRINT EMBEDDING DNNs

The Face, Face+Mask, and Fingerprint Embedding DNNs FHE transform the biometric input image to a distance measurable 1-way encryption (embedding, or vector encryption) consisting of a two-dimensional positional array of 128 floating-point numbers. 

The Face, Face+Mask, and Fingerprint Embedding DNNs maintain full accuracy through real-world boundary conditions including poor lighting; inconsistent camera positioning; expression; image rotation of up to 22.5°; variable distance; focus impacted by blur and movement; occlusions of 20-30% including facial hair, glasses, scars, makeup, colored lenses and filters, and abrasions; and B/W and grayscale images.  The embedding DNNs use the MobileNetV2 architecture and output a 1-way encrypted payload in <100ms. 

#### Voice Input Segmentation 

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(6).png)

Voice Input Segmentation generalizes the enrollment, improves accuracy and performance during prediction, and allows the DNN to handle real-world conditions. Every enrollment requires >50 10ms voice samples to maintain accuracy and performance. The algorithm uses a sliding 10ms window across one second of input to reach or exceed 50 samples. 

#### Voice Pulse Code Modulation (PCM) Transformation

Pulse Code Modulation lessens the input to two times the frequency range allowing for the smallest possible Fourier transform without computational loss. 

#### Voice Fast Fourier Transformation (FFT)

The Voice Fast Fourier Transform (FFT) moves the pulse code modulated audio signal from the time domain to a representation in the frequency domain.  The transform output is a 2-dimensional array of frequencies that is input to the Voice Embedding DNN.

#### Voice Embedding DNN

The Voice Embedding DNN accepts input of one 2-dimensional array of frequencies, FHE transforms the input to a 4kB, 2-dimensional positional array of 128 floating-point numbers (Cosine-measurable embedding, or 1-way vector encryption), and then deletes the original biometric. 

#### Offline Web Client Biometric Acquisition (Local Mode)

* Private Identity MFA Web client acquires biometrics at the edge with or without a network 

* Web client automatically switches to Local Mode after it detects loss of network 

The Web client supports offline operation (“Local Mode”) using Edge computing. The device in Local Mode authenticates a user using face and fingerprint recognition in 10ms with intermittent or no Internet connection as long as the user authenticates at least once to the device while online. The device stores the user’s FHE (embeddings) locally using the Web Storage API during the first prediction. The client automatically detects the loss of network connectivity. The URL parameter “localMode=true” directs the Web client to use the offline embedding store to authenticate. 

### Encryption Engine

* Asynchronous pre-processing engine for massive plaintext biometric ingestion 

* Elastic, fault-tolerant and load balanced Kubernetes clusters

* Decoupled from back-end cluster for privacy 

* Provides exception processing 

The Encryption Engine provides unlimited asynchronous throughput for high-demand enrollment and identification tasks using elastic, load-balanced, fault-tolerant Kubernetes clusters.￼

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(5).png)


The Encryption Engine maintains full accuracy and performance through real-world boundary conditions and accepts Base-64 plaintext images, video or audio using directory scanning or RESTful API. The Engine identifies multiple faces and fingerprints per frame, identifies voice in audio, provides data augmentation, creates a 1-way hash (FHE transformation) for subsequent processing, and then immediately discards the original biometrics. FHE transformation requires 10ms constant time using Cloud AI services and load-balanced, elastic, fault-tolerant Kubernetes clusters.

### Private Identity Search

* Asynchronous pre-processing engine for massive plaintext biometric ingestion 

* Elastic, fault-tolerant and load balanced Kubernetes clusters

* Decoupled from back-end cluster for privacy 

* Provides exception processing 

Private Identity Search™ provides high-demand identification tasks asynchronous face, face+mask, fingerprint and voice identification with unlimited throughput using elastic, load-balanced, fault-tolerant Kubernetes clusters. 

Similar to the Encryption Engine (described above), Private Identity Search maintains full accuracy and performance through real-world boundary conditions and accepts Base-64 plaintext images, video or audio by directory scanning or RESTful API. Private Identity Search identifies multiple faces and fingerprints per frame, identifies voice in audio, provides data augmentation, creates a 1-way hash (FHE transformation) for subsequent processing, and then immediately discards the original biometrics. Search returns identity in 200ms constant time using Cloud AI services and load-balanced, elastic, fault-tolerant Kubernetes clusters.

## Biometric Matching Algorithms

The Private Identity architecture is biometric modality agnostic. Private Identity uses two DNNs per modality and a set of helper DNNs for each biometric acquisition. Each modality has one pre-trained TensorFlow embedding model and one TensorFlow classifying model that work hand-in-hand to match subjects.  The first DNN and its associated helper DNNs acquire the biometric using the Biometric Acquisition Workflow and then discard (delete) the plaintext biometric after embedding creation.  ￼

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(4).png)

The second DNN, a custom Fully Connected Neural Network (FCNN), classifies each FHE and subsequently returns identity in polynomial time. It is capable of classifying an unlimited number of FHEs and returning identity in constant time when configured using load-balanced, elastic, fault-tolerant Kubernetes clusters.  Testing on GCP using 100,000 FHEs/second (approx. 8B authentications/day, or similar to the daily volume of Azure Active Directory) through cloud AI responded in constant time.  The second DNN runs in any AI cloud container or on-premise. 

### Facial Recognition Algorithm

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(3).png)

* Provides absolute accuracy (99.99%) with nearly zero false positives (0.0001%)

* Recognizes faces using any general-purpose camera (webcams, phones) ≥256kB

* Enrolls an unlimited number of users (“unlimited gallery size”) using an ethnically balanced dataset 

* Operates in polynomial time irrespective of gallery size and without discrimination (race, age, gender)

* Trained using the VGG Face2 dataset ethnically balanced with the Asian-Celeb dataset 

Minimum Imaging Requirements: Face ≥224×224 pixels. Camera ≥256kB. 
Face images smaller than 224×224 pixels may reduce performance. 

Discrimination:  An ethnically balanced dataset and a variety of homogenized lighting algorithms prevent discrimination based on age, gender or ethnicity. 

Predict RESTful API. Accepts FHE input from the web client or the Encryption Engine. The API returns identity in 200ms constant time with unlimited throughput. 

Enroll RESTful API: Accepts FHE input from the web client or the Encryption Engine. The API enrolls the subject in 800ms constant time with unlimited throughput. 

Delete_Subject RESTful API. Accepts FHE input from the web client or the Encryption Engine and deletes identity.

### Face+Mask Recognition Algorithm

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(2).png)

* Provides high accuracy (98%) with nearly zero false positives (0.0001%)

* Recognizes faces with masks using any general-purpose camera (webcams, phones) ≥256kB

* Enrolls an unlimited number of users (“unlimited gallery size”) using an ethnically balanced dataset 

* Operates in polynomial time irrespective of gallery size and without discrimination (race, age, gender)

* Trained using the VGG Face2 dataset ethnically balanced with the Asian-Celeb dataset 

Minimum Imaging Requirements: Face ≥224×224 pixels. Camera ≥256kB. 
Face images smaller than 224×224 pixels may reduce performance. 

Discrimination:  An ethnically balanced dataset and a variety of homogenized lighting algorithms prevent discrimination based on age, gender or ethnicity. 

Predict RESTful API. Accepts FHE input from the web client or the Encryption Engine. The API returns identity in 200ms constant time with unlimited throughput. 

Enroll RESTful API: Accepts FHE input from the web client or the Encryption Engine. The API enrolls the subject in 800ms constant time with unlimited throughput. 

Delete_Subject RESTful API. Accepts FHE input from the web client or the Encryption Engine and deletes identity.

### Fingerprint Recognition Algorithm

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(1).png)

* Provides absolute accuracy (99.99%) with nearly zero false positives (0.0001%) 

* Recognizes fingerprints using any general-purpose camera (webcams, phones) ≥4MP

* Matches in polynomial time irrespective of gallery size and without discrimination (race, age, gender)

* Trained using the NIST Special Database 4 and CASIA-FingerprintV5 

The DNN maintains full accuracy through real-world boundary conditions including poor lighting; camera positioning; expression; image rotation to 22.5°; distance; focus; blur and movement; 30% occlusions including scars, abrasions, and B/W and grayscale images. 

Minimum Imaging Requirements: Fingerprint ≥224x224. Camera ≥4MP
Images smaller than 224x224 pixels may reduce performance.

Discrimination: Private Identity HSL filters remove light absorption, skin contour and skin color as distractors and, when combined with a balanced training data set, ensure fairness across ethnic, gender and age groups.  

Predict RESTful API. Accepts FHE input from the Web client or the Encryption Engine. The API returns identity in 200ms constant time with unlimited throughput. 

Enroll RESTful API: Accepts FHE input from the Web client or the Encryption Engine. The API enrolls the subject in 800ms constant time with unlimited throughput. 

Delete_Subject RESTful API. Accepts FHE input from the Web client or the Encryption Engine and deletes identity.

### Voice / Speaker Identification Algorithm

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper.png)

* Text-, language- and accent-independent voice identification with 1 second of audio

* Provides high accuracy (93%) with nearly zero false positives (0.0001%) 

* Matches in polynomial time irrespective of gallery size and without discrimination

Minimum Audio Requirements: Voice ≥1 second. Audio ≥8.1kHz (telephone quality)
The minimum voice input size is 100ms. 

Predict RESTful API. Accepts FHE input from the Web client or the Encryption Engine. The API returns identity in 300ms constant time with unlimited throughput. 

Enroll RESTful API: Accepts FHE input from the Web client or the Encryption Engine. The API enrolls the subject in 800ms constant time with unlimited throughput. 

Delete_Subject RESTful API. Accepts FHE input from the Web client or the Encryption 