### Cloud Biometric API Uses Models and APIs to Enable Recognition and Search
Cloud Biometric API uses state-of-the-art face, face+face mask, voice and fingerprint algorithms to detect and recognize human biometrics in images and audio. Capabilities include features like face detection and face identification. 

#### There are two types of fees.
**Biometric Transactions**: Cloud Biometric API charges you each time you operate on a biometric with a model or API. Using multiple components (models or APIs) against a single biometric counts as processing multiple operations. 

**Biometric Metadata Storage**: Cloud Biometric API stores a repository of anonymized metadata during enrollment against which Cloud Biometric API can search for matches. Storage charges are applied monthly.

### Pricing Table - General

| Quantity | Price/Transaction | Price/1000 Transactions | Throughput |
| ----------- | ------- | :-----------: | :-----------: | 
| 0-1M transactions/month | $0.00100 | $1.00 | Unlimited |
| 1M-9M transactions/month | $0.00080 | $0.80 | Unlimited |
| Next 90M transactions/month | $0.00060 | $0.60 | Unlimited | 
| Over 100M transactions/month | $0.00040 | $0.40 | Unlimited |
| Data Storage/enroll/month | $0.00001 | $0.01 | Unlimited | 

Each model use or API call counts as one transaction. Some operations are priced differently as described in the table below. 

### Pricing Table - Specific

| Component | 0-1M <br>Transactions | 1M-9M <br>Transactions | 9M-90M <br>Transactions | >100M <br>Transactions |
| ----------- | ----------- | ----------- | ------- | ------- |
| **FACE RECOGNITION** | | | | 
| [Face Landmark](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-face-wmask-and-fingerprint-geometry-detection-dnns)| $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Blur Detection](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#blurry-image-detect-dnn) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Image Spoof Detection](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#video-and-image-spoofing-detection-dnn-spoofing-prevention) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Video Spoof Detection](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#video-and-image-spoofing-detection-dnn-spoofing-prevention) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Eyeglasses Detection](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#active-liveness-dnn-spoofing-prevention) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Eye Blink Detection](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#active-liveness-dnn-spoofing-prevention) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Face Identification](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-facemask-and-fingerprint-embedding-dnns) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Face+Mask Identification](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-facemask-and-fingerprint-embedding-dnns) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| **FINGERPRINT RECOGNITION** | | | | 
| [Fingerprint Geometry](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-face-wmask-and-fingerprint-geometry-detection-dnns) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Fingerprint Validation](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-face-with-mask--fingerprint-validation-dnns) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Fingerprint Identification](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-facemask-and-fingerprint-embedding-dnns) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| **VOICE RECOGNITION** | | | | 
| [Voice Validation](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-validation-dnn)| $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Voice Data Augmentation](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-data-augmentation) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Voice Fast Fourier Transformation (FFT)](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-pulse-code-modulation-pcm-transformation) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Voice Identification](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-embedding-dnn) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| **GEOLOCATION** | | | | 
| On-Device Geolocation | $0.012000 | $0.010000 | $0.08000 | $0.06000 |
| **PHOTO ID VERIFICATION** | | | | 
| [Document Geometry](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#document-geometry-detection-dnns) | $0.00100 | $0.00080 | $0.00600 | $0.00400 |
| [Document OCR API](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#document-ocr-api) | $0.01200 | $0.01000 | $0.00800 | $0.00600 |
| [Mobile Billing Record Lookup](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#mobile-billing-record-lookup-api) | $0.03000 | $0.02800 | $0.02600 | $0.02400 |
| [Mobile Billing Record Lookup](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#mobile-billing-record-lookup-api) (Outside USA) | $2.50000 | $2.48000 | $2.46000 | $2.44000 | 
| [SMS Verification Message API](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#sms-verification-message-api) | $0.02000 | $0.01800 | $0.01600 | $0.01400 | 
| **ENROLLMENT METADATA STORAGE** | | | |
| Face Metadata Storage | $0.00010 | $0.00010 | $0.00010 | $0.00010 | 
| Face+Mask Metadata Storage | $0.00010 | $0.00010 | $0.00010 | $0.00010 | 
| Fingerprint Metadata Storage | $0.00010 | $0.00010 | $0.00010 | $0.00010 | 
| Voice Metadata Storage | $0.00010 | $0.00010 | $0.00010 | $0.00010 | 

### Example 1
If your application made the following requests in a one-month period:
* 700 Face Enrolls using six transactions
  * Face Landmarks
  * Blur Detection
  * Image Spoof Detection
  * Video Spoof Detection 
  * Eyeglass Detection 
  * Face+Mask Identification 

Your cost would be $4.20 (700 persons x (6 transactions x $0.00100)) 

### Example 2
If your application made the following requests in a one-month period:
* 5000 Face Predicts
  * Face Landmarks
  * Blur Detection
  * Image Spoof Detection
  * Video Spoof Detection 
  * Eyeglass Detection 
  * Face+Mask Identification 

Your cost would be $30.00 (5000 predicts x (6 transactions x $0.00100))

Invoices are rounded up to the next penny once at the end of each billing cycle.