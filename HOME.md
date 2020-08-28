[![logo-name](https://github.com/openinfer/PrivateIdentity/blob/master/images/CBMFA%20White%20Space%20on%20Right.png)](https://www.private.id/)

## VIDEO INTRODUCTION

[![IMAGE ALT TEXT](https://github.com/openinfer/PrivateIdentity/blob/master/images/CBMFA%20Overview%20Video%20Img3.png)](https://youtu.be/G33UR87I81E "Quick Introduction to Cloud Biometric MFA")

## OVERVIEW
* <b>Integrates easily</b> into your IAM solution or applications using the included Javascript component (embedded DIV), JavaScript APIs, REST APIs, SAML 2.0 or OAuth/OIDC.

* <b>Deploys instantly </b>across all modern browsers, devices, platforms and clouds. There is no client software to install and no hardware to buy.

* <b>Preserves privacy</b> using [fully homomorphic encryption](https://en.wikipedia.org/wiki/Private_biometrics) (FHE). Processes only anonymized data</b> and not biometric data. 

* <b>Exempt from GDPR, CCPA and BIPA obligations</b>, as documented in [IEEE 2410 Standard for Biometric Privacy](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D).

* <b>Non-biased algorithms </b>recognize everybody equally across all ethnicities, skin tones, genders and ages. The mobile DNNs also accommodate boundary conditions with up to 30% occlusions including facial hair, abrasions, masks, and blurry or rotated images.

## RESOURCES

* <b>[Short Introduction](https://www.youtube.com/watch?v=G33UR87I81E&feature=youtu.be "Short Video Introduction")</b> [YouTube] 
* <b>Getting Started with Private Identity</b> [YouTube]

* <b>[Architecture](https://github.com/openinfer/PrivateIdentity/wiki#basic-architecture) </b>[Developer Wiki]

* <b>[Demo Video](https://youtu.be/6x0b5FckhIA) </b>[YouTube Channel]

* <b>[Discussion with Demos](https://youtu.be/Zn-pNJ0svJg) </b>[YouTube Channel]

* <b>White Paper </b> [Google Doc]  (Needs editing!)

* <b>[Private Biometrics](https://en.wikipedia.org/wiki/Private_biometrics) </b>[Wikipedia]

* <b>[https://private.id/demo](https://private.id/demo/?apiKey=00000000000000001962) </b> [Try it now!]

## KEY FEATURES
### Single Component Javascript App
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Single%20Compoent%20App%201.png)
* Preserves privacy by synchronously acquiring and FHE transforming biometric data at the edge 
* Easy to deploy with no requirement to install additional software, plugins or extensions 
* Built with Javascript, TensorFlow.js and an ensemble of helper DNNs 
* Runs on 90% of all modern devices 

The Javascript client provides users with massively horizontally scalable, browser-based biometric enrollment, identity, MFA and account recovery in a convenient Web experience that operates on more than 90% of all browsers, platforms and devices. The Web client uses on-device pre-trained TensorFlow models to acquire, validate, align, crop, transform and 1-way encrypt the biometric. 

The Web client does not require on-device training and has no requirement for expensive hardware, cameras, GPUs, batteries or RAM. Devices with multi-threaded kernels operate in millisecond response time. Devices equipped with GPUs and Edge TPUs operate 70-100x faster. Less capable devices operate by offloading processing to Node.js using the “whereToProcess=nodeServer” URL parameter.  

The Web client acquires the biometric using an ensemble of pre-trained TensorFlow™ models.  These models offer the opportunity for higher accuracies and lower overhead than traditional procedural programming.  These small, convenient Helper DNNs use YOLO architecture, are 10kB to 100kB in size and process in <10ms with accuracies >99%.

[Link](https://github.com/openinfer/PrivateIdentity/wiki/Client-Applications) for additional information.

### Built-in Privacy
* Fully homomorphic encryption (FHE) complies with privacy laws worldwide including GDPR, CCPA and BIPA 
* Certified compliant with [IEEE 2410](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D) Standard for Biometric Privacy 

Fully homomorphic encryption (FHE) mitigates the regulatory and legal privacy risk of biometric data by enabling mathematical operations on an encrypted dataset. This eliminates all requirements to process plaintext biometrics or templates.

Specifically, biometric data is irreversibly anonymized using a 1-way cryptographic hash algorithm and then discarded (deleted) without the data ever leaving the local device. To accomplish this, the system transforms biometric data inputs into FHE payloads that are globally unique (i.e. no two payloads are ever the same), positional arrays of 128 floating-point numbers that do not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait. 

This anonymized FHE payload ceases to be biometric data or personal data because the system eliminates any known or foreseeable possibility of linking any of the data to the individual to whom the data originally related. As a result, the FHE is not “Personal Data” under General Data Protection Regulation (EU) 2016/679 (“GDPR”) or the California Consumer Privacy Act (“CCPA”) and is not “Biometric Information” under the Biometric Information Privacy Act (“BIPA”).  

The data subject’s rights provided under each of these statutes thus fall away, and businesses may utilizes this biometric solution without subjecting their organizations to GDPR, CCPA or BIPA data subject rights or special handling requirements for personal data, biometric data, biometric identifiers, or associated data breach notification requirements. Finally, a breach of the Cloud Biometric MFA system would not result in the loss of any biometric data or personal data.  _(The analysis of data privacy laws in this Website does not constitute legal advice and all businesses should seek counsel concerning their data privacy legal and compliance obligations.)_

### Flexible Deployment
![Flexible Deployment Graphic](https://github.com/openinfer/PrivateIdentity/blob/master/images/Flex%20Deploy%201.png)<br>
The Cloud Biometric MFA solution is available as SaaS or PaaS on GCP, AWS and on-premises. Private Identity provides pre-configured SaaS enterprise integrations using SAML 2.0 or OAuth/OIDC for Google Identity®, PING Identity®, Okta® Factor Authentication, SAML 2.0, OAuth/OIDC, WebAuthn, Azure® Active Directory and AWS® IAM. 

For PaaS integrations on GCP, the solution leverages TensorFlow.js, Cloud AI Platform, Cloud Compute, K8s Engine, Memory Store (Redis), MySQL clustered & fault tolerant, Cloud Storage buckets & data lakes, Cloud Speech to Text, Cloud Vision API, Cloud DNS and Cloud Identity.  Similarly, for PaaS integrations on AWS, the solution leverages TensorFlow.js, Sagemaker, Compute, EKS, In Memory Store (Redis), MySQL clustered & fault tolerant, S3, AIM, and Cloud Speech to Text, Cloud Vision API and Route 53. 

### No Discrimination
![Image of No Discrimination](https://github.com/openinfer/PrivateIdentity/blob/master/images/No%20Discrim%201.png)<br>
To overcome bias (discrimination), we use an ethnically balanced dataset combined with a variety of homogenized lighting (HSL) algorithms to ensure fairness across ethnic, gender and age groups. The HSL filters are particularly important in that they remove light absorption, skin contour and skin color as distractors.  
 
The face recognition DNN is pre-trained using an ethnically balanced dataset of 50M images (8000 classes) from both Oxford VGGFace2 and Asian-Celeb. The classes in the dataset are ethnically distributed as follows: 60% Caucasian, 30% Asian, 5% Black and 5% Indian. 

The resulting DNN recognizes everybody equally with an  [accuracy of 99.92%.](https://github.com/openinfer/PrivateIdentity/wiki/EVALUATION-METRICS-FOR-FACE-RECOGNITION-DNN)

### Facial Recognition 
![woman's face](https://github.com/openinfer/PrivateIdentity/blob/master/images/Face%20Recogni%201.png)<br>
| Accuracy | Type I Error | Type II Error | Speed |
|---|---|---|---|
| **1:1 Verification** | | |
| TMR=99.99% | FMR=0.0001% | FNMR=0.0001% | Speed=300ms |
| **1:Many Identification** | | |
| IR=99.99% | FPIR=0.0001% | FNIR=0.0001% | Speed=300ms |

* Recognizes faces using any general-purpose camera (webcams, phones) ≥256kB
* Enrolls an unlimited number of users (“unlimited gallery size”) 
* Operates in polynomial time irrespective of gallery size 
* Trained using the Oxford VGGFace2 dataset ethnically balanced with the Asian-Celeb dataset 
* Minimum Imaging Requirements: Face ≥ 224×224 pixels. Camera ≥256kB. Face images smaller than 224×224 pixels may reduce performance. 
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters

### Face + Mask Recognition  
![woman wearing face mask](https://github.com/openinfer/PrivateIdentity/blob/master/images/Face%20w%20Mask%201.png)
| Accuracy | Type I Error | Type II Error | Speed |
|---|---|---|---|
| **1:1 Verification** | | |
| TMR=99.99% | FMR=0.0001% | FNMR=0.0001% | Speed=300ms |
| **1:Many Identification** | | |
| IR=98.20% | FPIR=0.0001% | FNIR=1.80% | Speed=300ms |

* Recognizes faces **and faces with masks** using any general-purpose camera (webcams, phones) ≥256kB
* Enrolls an unlimited number of users (“unlimited gallery size”) 
* Operates in polynomial time irrespective of gallery size 
* Trained using the Oxford VGGFace2 dataset ethnically balanced with the Asian-Celeb dataset 
* Minimum Imaging Requirements: Face ≥ 224×224 pixels. Camera ≥256kB. Face images smaller than 224×224 pixels may reduce performance. 
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters

### Fingerprint Identification
![man's finger](https://github.com/openinfer/PrivateIdentity/blob/master/images/fingerprint%20recogni%201.png)
| Accuracy | Type I Error | Type II Error | Speed |
|---|---|---|---|
| **1:1 Verification** | | |
| TMR=99.99% | FMR=0.0001% | FNMR=0.0001% | Speed=300ms |
| **1:Many Identification** | | |
| IR=96.30% | FPIR=0.0001% | FNIR=3.70% | Speed=300ms |
* Recognizes fingerprints using optical scan (camera) or capacitive sensor 
* Uses any general-purpose camera (Webcams, phones) ≥720P (1MP)
* Enrolls an unlimited number of users (“unlimited gallery size”) 
* Operates in polynomial time irrespective of gallery size 
* Trained using the NIST Special Database 4 and CASIA-FingerprintV5 
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters
* Minimum Imaging Requirements: Fingerprint ≥ 224×224 pixels. Camera ≥256kB. Fingerprint images smaller than 224×224 pixels may reduce performance. 

### Voice (Speaker) Identification 
![man speaking into phone](https://github.com/openinfer/PrivateIdentity/blob/master/images/voice%20recogni%201.png)
| Accuracy | Type I Error | Type II Error | Speed |
|---|---|---|---|
| **1:1 Verification** | | |
| TMR=99.99% | FMR=0.0001% | FNMR=0.0001% | Speed=300ms |
| **1:Many Identification** | | |
| IR=95.20% | FPIR=0.0001% | FNIR=4.80% | Speed=300ms |
* Text-, language- and accent-independent voice identification with 1 second of audio
* Enrolls an unlimited number of users (“unlimited gallery size”) 
* Operates in polynomial time irrespective of gallery size 
* Minimum Audio Requirements: Voice ≥1 second. Audio ≥8.1kHz (telephone quality). The minimum voice input size is 100ms. Voice input < 1 second may reduce performance.
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters

### Geometry, Validation and Embedding DNNs

#### Geometry Detection DNNs for Face, Face w/Mask, Fingerprint, Eye and Voice 
* <b>Transforms images into geometric primitives</b> to measure the relative position, width, and other parameters of eyes, mouth(s), nose(s), chin(s), and finger(s)
* <b>Returns X and Y coordinates</b> of each modality in an image, video frame or video stream.
* YOLO architecture, 100kB
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-and-face-wmask-geometry-detection-dnn) for additional information

#### Validation DNNs for Face, Face w/Mask and Fingerprint 
* <b>Accurately aligns & crops</b> each frontalized face input image
* <b>Detects photo or video attack (anti-spoofing)</b> during unattended operation
* <b>Detects blinking</b> (eyes open/closed) for real-time passive facial liveness (anti-spoofing)
* <b>Detects face mask</b> if the user is wearing a face mask. 
* <b>Detects eyeglasses</b> before allowing enrollment
* <b>Returns a validation score</b> between 0 to 100, where 100 is a perfect image.  
* MobileNetV2 architecture, 1.5MB
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face--fingerprint-validation-dnns) for additional information

#### Validation DNN for Voice
* <b>Validates audio input</b> for a quality human voice to discriminate between a voice and external noise
* YOLO architecture, 100kB
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-speaker-identification) for additional information

#### Embedding DNNs for Face, Face w/Mask and Fingerprint 
* <b>FHE transforms the biometric input image </b>to a distance measurable 1-way encryption (embedding, or vector encryption) consisting of a two-dimensional positional array of 128 floating-point numbers 
* <b>Maintains full accuracy</b> through real-world boundary conditions including poor lighting; inconsistent camera positioning; expression; image rotation of up to 22.5°; variable distance; focus impacted by blur and movement; occlusions of 20-30% including facial hair, glasses, scars, makeup, colored lenses and filters, and abrasions; and B/W and grayscale images.  
* Produces (output) FHE payload in < 100ms
* MobileNetV2 architecture, 1.3MB for Face and 900kB for Fingerprint 
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-facemask-and-fingerprint-embedding-dnns) for additional information

#### Embedding DNN for Voice
* FHE transforms one 2-dimensional array of frequencies (input) to a 4kB, 2-dimensional positional array of 128 floating-point numbers (Cosine-measurable embedding) 
* Produces FHE payload in < 100ms
* MobileNetV2 architecture, 3.5MB
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-embedding-dnn) for additional information

### Offline Authentication
* <b>Acquires biometrics at the edge</b> with or without a network (TensorFlow at the Edge)
* <b>Automatically switches to Local Mode</b> after it detects loss of network 
* <b>Authenticate user in 10ms</b> with intermittent or no Internet connection as long as the user authenticates at least once to the device while online 
* <b>Automatically detects</b> the loss of network connectivity. 

## SOLUTIONS

### IAM Integrations
![IAM Logos](https://github.com/openinfer/PrivateIdentity/blob/master/images/IAM%20Integr%201.png)
* Integrates with your existing Enterprise directory using SAML 2.0 or OAuth/OIDC
* [Google G Suite Integration](https://github.com/openinfer/PrivateIdentity/wiki/SAML-2.0#integration-with-gsuite)
* [Ping Identity PingFederate® Integration](https://github.com/openinfer/PrivateIdentity/wiki/Enterprise-Integrations#ping-identity)
* [Okta® Factor Authentication Integration](https://github.com/openinfer/PrivateIdentity/wiki/Enterprise-Integrations#okta)
* [Azure Active Directory (AAD) Integration](https://github.com/openinfer/PrivateIdentity/wiki/SAML-2.0#integration-with-microsoft-azure)


### Digital Identity Verification
![hand holding drivers license](https://github.com/openinfer/PrivateIdentity/blob/master/images/Identity%20Verification%201.png)
* <b>Meets AML/KYC identity-proofing requirements </b>for remote presentation of identifying materials or information by an end user for KYC
* Allows organizations to verify user to [Enrollment Level 2](https://arch.idmanagement.gov/usecases/12_proofidentityloa2/)</b> using an official Photo ID card or passport. 
* <b>Compares ID cards or passport photo</b> to enrolled user's face 
* <b>Compares name and contact information on ID card </b>or passport to mobile phone billing records
* <b>Verifies phone owner with SMS </b>message to phone 
* <b>Preserves privacy</b> by having no personal data leave the local device 
* [Link to documentation on Github](https://github.com/openinfer/PrivateIdentity/wiki/Verified-Enroll)

### Account Recovery
![woman gesturing that she forgot her password](https://github.com/openinfer/PrivateIdentity/blob/master/images/Account%20Recovery%201.png)
* <b>Users enroll once</b> using multiple biometric modalities (face, fingerprint, voice) to ensure future access.
* <b>Quickly and accurately identifies locked-out account holders</b> and restores access

## OPEN STANDARDS, ENCRYPTION & PRIVACY 
![Image of lego blocks ](https://github.com/openinfer/PrivateIdentity/blob/master/images/Open%20Stanards%201.png)
* Private Identity actively supports the development of open standards for biometric privacy, cryptography and security
* <b>Third-party accredited certification</b> (3PAO) is provided by [GMS Registrar](https://gmsaudit.com/). 

Private Identity is certified compliant with IEEE 2410 Standard for Biometric Privacy, ISO 27001:2013 International Standard for Information Security Management, ISO 9001:2015 International Standard for Quality Management Systems, US DoD Standard Trusted Computer System Evaluation Criteria (TCSEC), US ODNI ICD 503 Intelligence Community Technology Systems Security Risk Management, Certification and Accreditation and US DoD Multiple Independent Levels of Security/Safety (MILS) Architecture, and compliant with W3C Web Authentication API (WebAuthn), FIPS 197, TLS, IPSEC and SSL.  

### IEEE 2410 Standard for Biometric Privacy 
* <b>Requires FHE for private identity assertion </b>and authentication 
* <b>Guarantees compliant systems do not incur GDPR, CCPA, BIPA or HIPAA privacy obligations</b>
* Link to approved [draft standard](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D)]  

### W3C WebAuthn
* <b>Enables creation and use of strong</b>, attested, scoped, public key-based credentials by Web applications 
* [Link to Standard](https://www.w3.org/TR/webauthn/)

### US ODNI ICD 503
* <b>Applies to all US government organizations</b>, their commercial contractors, and Allied governments information systems that process, store, or communicate intelligence information.
* [Link to Directive](https://www.dni.gov/files/documents/ICD/ICD_503.pdf)

### US DOD Standard Trusted Computer System Evaluation Criteria (TCSEC)
* <b>Original standard for processing and storage of classified </b>and other sensitive DoD information 
* [Link to DoD 5200.28-STD](https://csrc.nist.gov/csrc/media/publications/conference-paper/1998/10/08/proceedings-of-the-21st-nissc-1998/documents/early-cs-papers/dod85.pdf)

### FIPS 197 Advanced Encryption Standard (AES)
* <b>Guideline for Implementing Cryptography </b>in the US Federal Government. 
* [Link to NIST Special Publication 800-21](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)

### TLS / IPSEC / SS
* <b>Standard protocols providing privacy and data integrity </b>between two or more communicating computer applications
* [Link to IETF](https://tools.ietf.org/html/rfc8446)

## OPEN STANDARDS, SECURITY ARCHITECTURE 

### ISO 27001:2013 Information Security Management Standard
* <b>International Standard for information risk management process </b>includes all legal, physical and technical controls 
* [Link to ISO/IEC 27001](https://www.iso.org/isoiec-27001-information-security.html)

### ISO 9001:2015 Quality Management Standard
* <b>International Standard ensures software satisfies statutory and regulatory requirements </b>and meets the needs of customers and other stakeholders
* [Link to ISO 9000](https://www.iso.org/iso-9001-quality-management.html)

### OAuth 2.0 / OpenID Connect / SAML 2.0
* <b>Standards that cover authorization, federation, identity management and single sign-on (SSO)</b>
* [Link to IETF](https://tools.ietf.org/html/rfc8252)

### DoD Multiple Independent Levels of Security/Safety (MILS) Architecture
* <b>Compartmentalized approach to the design of security-critical</b>, safety-critical, high-assurance computing systems
* [Link to MILS Community](https://mils.community/)

## FLEXIBLE DEPLOYMENT

### SAML 2.0
* Supports SAML 2.0 and OAuth/OIDC protocols
* [Google G Suite Integration](https://github.com/openinfer/PrivateIdentity/wiki/SAML-2.0#integration-with-gsuite)
* [Ping Identity PingFederate® Integration](https://github.com/openinfer/PrivateIdentity/wiki/Enterprise-Integrations#ping-identity)
* [Okta® Factor Authentication Integration](https://github.com/openinfer/PrivateIdentity/wiki/Enterprise-Integrations#okta)
* [Azure Active Directory (AAD) Integration](https://github.com/openinfer/PrivateIdentity/wiki/SAML-2.0#integration-with-microsoft-azure)

***

### Single Component JavaScript Application (Embedded DIV)
![Javascript](https://github.com/openinfer/PrivateIdentity/blob/master/images/JS%20Deploy%202.png)
* Deploys effortlessly with no software to install and no hardware to buy
* Users enroll in four seconds, authenticate in 300ms
* Built in React.js (pluggable)
* Embed as a DIV
* Preserves privacy by acquiring and FHE transforming biometric data at the edge 
* Runs on 90% of all modern devices 
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/Client-Applications) for additional information.
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/DIV-HTML)

### JavaScript APIs (Predict Enroll API)
![Image of Javascript API ](https://github.com/openinfer/PrivateIdentity/blob/master/images/JS%20API%202.png)
* Lightweight Javascript library with 2 API calls (enroll and predict) 
* Accepts image and audio inputs and returns UUID
* Includes a Web sandbox to exercise the API 
* Deploys effortlessly with no software to install and no hardware to buy
* Users enroll in four seconds, authenticate in 300ms
* Preserves privacy by acquiring and FHE transforming biometric data at the edge 
* Runs on 90% of all modern devices 
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/JavaScript-API) for setup.

> **Method: window.enroll**(uuid, apiKey, 'face', images1, 'voice', voiceFile, 'fingerprint', images2);
Accepts FHE input and enrolls subject in 800ms constant time.

> **Method: window.predict**(apiKey, 'face', images1, 'voice', voiceFile, 'fingerprint', images2);
Accepts FHE input and returns identity in 300ms constant time.

***

### REST APIs 
![RESTful API image](https://github.com/openinfer/PrivateIdentity/blob/master/images/REST%20API2.png)
* Four APIs that communicate RESTful using JSON
* Receives FHE payloads (input) from JavaScript app, JavaScript APIs or Encryption Engine 
* Enrolls in four seconds, authenticates in 300ms

> POST “/trueid/v1.1/enroll”
> POST “/trueid/v1.1/predict”
> POST “/trueid/v1.1/liveness”
> POST “/trueid/v1.1/verify”

***

### ENCRYPTION ENGINE (Setup)
![Picture of shield with lock on front](https://github.com/openinfer/PrivateIdentity/blob/master/images/Encryption%20Engine%202.png)
Provide asynchronous processing for high-demand, high-throughput enrollment and identification tasks using elastic, fault tolerant, load balanced Kubernetes clusters. It is decoupled from the back end clusters to preserve privacy and supports the JavaScript API and REST API.

*** 

### SaaS Deployments
![Picture of cloud](https://github.com/openinfer/PrivateIdentity/blob/master/images/SaaS%20Deploy%202.png)

#### SaaS (Open)
API Key access to the elastic, load balanced and fault tolerant Private Identity Web services managed and run on AWS by Private Identity.

#### SaaS (Dedicated for a single Customer)
API Key access to an elastic, load balanced and fault tolerant Kubernetes cluster running Private Identity Web services dedicated entirely to a single customer. Managed and run on AWS by Private Identity.

***

### PaaS Deployments 

#### PaaS Web Tier (Setup)
Docker image of the Web tier that runs in elastic, load balanced, fault tolerant Kubernetes clusters on-premise or any public or private cloud. Connects to Private Identity Web services managed and run on AWS by Private Identity.

#### PaaS Entire Tier (Setup)
Docker images of all software that runs in elastic, load balanced, fault tolerant Kubernetes clusters on-prem or any public or private cloud. Includes all backend services and has no requirement to connect to Private Identity.

***

## PRIVACY

### FHE allows organizations to utilize Cloud Biometric MFA without incurring GDPR, CCPA or BIPA obligations. 
Fully homomorphic encryption (FHE) mitigates the regulatory and legal privacy risk of biometric data by enabling mathematical operations on an encrypted dataset. This eliminates all requirements to process plaintext biometrics or templates.

Specifically, biometric data is irreversibly anonymized using a 1-way cryptographic hash algorithm and then discarded (deleted) without the data ever leaving the local device. To accomplish this, the system transforms biometric data inputs into FHE payloads that are globally unique (i.e. no two payloads are ever the same), positional arrays of 128 floating-point numbers that do not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait. 

This anonymized FHE payload ceases to be biometric data or personal data because the system eliminates any known or foreseeable possibility of linking any of the data to the individual to whom the data originally related. As a result, the FHE is not “Personal Data” under General Data Protection Regulation (EU) 2016/679 (“GDPR”) or the California Consumer Privacy Act (“CCPA”) and is not “Biometric Information” under the Biometric Information Privacy Act (“BIPA”).  

The data subject’s rights provided under each of these statutes thus fall away, and businesses may utilizes this biometric solution without subjecting their organizations to GDPR, CCPA or BIPA data subject rights or special handling requirements for personal data, biometric data, biometric identifiers, or associated data breach notification requirements. Finally, a breach of the Cloud Biometric MFA system would not result in the loss of any biometric data or personal data.

_(Note: The analysis of data privacy laws in this Website does not constitute legal advice and all businesses should seek counsel concerning their data privacy legal and compliance obligations.)_

### GDPR Compliant and GDPR Exempt
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/GDPR%201.png)
Fully Homomorphic Encryption complies with GDPR. System exempt from GDPR obligations and data breach notification requirements.

### CCPA Compliant and CCPA Exempt
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/CCPA%201.png)
Fully Homomorphic Encryption complies with CCPA. System exempt from CCPA obligations and data breach notification requirements.

### BIPA Compliant and BIPA EXEMPT
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/BIPA%201.png)
Fully Homomorphic Encryption complies with CCPA. System exempt from CCPA obligations and data breach notification requirements.

### Certified Compliant IEEE 2410-2019
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/IEEE%202410%201.png)
Open standard requires Fully Homomorphic Encryption to protect biometric at rest, in transit and in use.









