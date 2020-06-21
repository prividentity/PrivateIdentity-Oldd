# Biometric Acquisition
</br>

* _Private Identity MFA_ ™ provides massively horizontally scalable, synchronous Web browser client for user identification, authentication, MFA and Account Recovery

* _Encryption Engine_ ™ provides asynchronous, elastic high-throughput FHE transform enrollment and identification service that installs anywhere

* _Private Identity Search_ ™ provides asynchronous, elastic high-throughput FHE transform identification service that installs anywhere 

Private Identity provides a Web client and two elastic services to support biometric acquisition and high-throughput FHE transformation at the edge. This enables Private Identity to accept a variety of synchronous and asynchronous biometric inputs (i.e. phones, Webcams, legacy devices and applications, and plaintext images, video, audio and input from third-party biometric acquisition systems) without any requirement to store, transmit or use plaintext biometrics.  ￼

The _Private Identity MFA_ Web client provides users with a massively scalable, convenient, browser-based enrollment, identity, MFA and account recovery experience that operates on more than 90% of all browsers, platforms and devices. 

The _Encryption Engine_ service provides high-throughput, high-demand identification tasks with unlimited asynchronous throughput for face, face with mask, fingerprint and voice enrollment and identification using elastic, load-balanced, fault-tolerant Kubernetes clusters. 

Similarly, the _Private Identity Search_ service provides high-throughput, high-demand identification tasks with unlimited asynchronous face, face with mask, fingerprint and voice identification using elastic, load-balanced, fault-tolerant Kubernetes clusters. 

The Web client, Encryption Engine and Private Identity Search use an ensemble of pre-trained TensorFlow™ models to detect and recognize faces (50ms), fingerprints (50ms) and voices (100ms) with high accuracy.

### Web Client Biometric Acquisition

* Uses TensorFlow.js and an ensemble of helper DNNs to acquire and FHE transform each biometric 

* Edge computing provides for massively horizontal scalability 

* Works on commodity devices without sacrificing performance 

The Private Identity MFA Web client provides users with massively horizontally scalable, browser-based biometric enrollment, identity, MFA and account recovery in a convenient Web experience that operates on more than 90% of all browsers, platforms and devices. The Web client uses on-device pre-trained TensorFlow models to acquire, validate, align, crop, transform and 1-way encrypt the biometric. ￼

The Web client does not require on-device training and has no requirement for expensive hardware, cameras, GPUs, batteries or RAM. Devices with multi-threaded kernels operate in millisecond response time. Devices equipped with GPUs and Edge TPUs operate 70-100x faster. Less capable devices operate by offloading processing to Node.js using the “whereToProcess=nodeServer” URL parameter.  

The Web client acquires the biometric using an ensemble of pre-trained TensorFlow™ models.  These models offer the opportunity for higher accuracies and lower overhead than traditional procedural programming.  These small, convenient Helper DNNs use YOLO architecture, are 10kB to 100kB in size and process in <10ms with accuracies >99%.

Each biometric modality requires its own helper DNNs.  For face and fingerprint we use the Face and Fingerprint Geometry model to identify specific face landmarks and boundaries; Face and Fingerprint Validation model to ensure appropriate lighting and clarity and support crop and align; Eyes Open/Closed for passive liveness in face recognition; Eyeglasses On/Off to prevent false negatives in face recognition; and Data Augmentation to increase the entropy of the enrollment set. 

For voice biometric acquisition, helper DNNs isolate singular voices. Additional processing includes Voice Input Segmentation to acquire voice samples using a sliding 10ms window across one second of input; Voice Pulse Code Modulation Transformation to down sample each segment to 2x the frequency range; and Voice Fast Fourier Transform to convert the signal from the time domain to the frequency domain.   

