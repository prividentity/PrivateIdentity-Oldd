[![logo-name](https://github.com/openinfer/PrivateIdentity/blob/master/images/CBMFA%20White%20Space%20on%20Right.png)](https://www.private.id/)

## VIDEO INTRODUCTION
[![IMAGE ALT TEXT](https://github.com/openinfer/PrivateIdentity/blob/master/images/CBMFA%20Overview%20Video%20Img3.png)](https://youtu.be/G33UR87I81E "Quick Introduction to Cloud Biometric MFA")

It took us three years and seventeen patents to build Cloud Biometric MFA. This all-new AI/ML/Fully Homomorphic Encryption (FHE) recognition algorithm is developed entirely in-house and powered by TensorFlow. It features absolute accuracy, 300ms response time, 4kB FHE payloads, unlimited users and full privacy.

Now, for the first time, digital identity is no longer tied to a device, username, password, token or shared secret.

## `OVERVIEW`

* [Face](https://github.com/openinfer/PrivateIdentity/wiki#facial-recognition), [Face w/ Mask](https://github.com/openinfer/PrivateIdentity/wiki#face--mask-recognition), [Voice](https://github.com/openinfer/PrivateIdentity/wiki#voice-speaker-identification) and [Fingerprint](https://github.com/openinfer/PrivateIdentity/wiki#fingerprint-identification) 1:n Identity and MFA

* <b>[Guarantees Privacy](https://github.com/openinfer/PrivateIdentity/wiki#built-in-privacy-exempt-from-gdpr-ccpa-bipa--hipaa-privacy-law-obligations) with Fully Homomorphic Encryption</b>
* <b>Enroll once</b>, then authenticate on almost any device
* <b>[[Deploys instantly](https://github.com/openinfer/PrivateIdentity/wiki/Single-Component-JavaScript-App)](https://github.com/openinfer/PrivateIdentity/wiki#flexible-deployment-1) with no software to install and no hardware to buy
* <b>[Integrates easily](https://github.com/openinfer/PrivateIdentity/wiki#flexible-deployment-1) into Web and mobile apps</b>, Enterprise IAM solutions and high-throughput biometric pipelines
* <b>[Unbiased algorithms]([https://github.com/openinfer/PrivateIdentity/wiki#no-discrimination](https://github.com/openinfer/PrivateIdentity/wiki#no-discrimination))</b> recognize everyone equally
* <b>[Exempt](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS) from GDPR, CCPA, BIPA and HIPAA </b>privacy law obligations

## `RESOURCES`

* <b>Short Video Introduction</b> [[AWS]](https://www.youtube.com/watch?v=G33UR87I81E&feature=youtu.be "Short Video Introduction AWS Flavored") [[GCP]](https://youtu.be/CuE3x543qKo "Short Video Introduction GCP Flavored")
* <b>Getting Started with Private Identity</b> [YouTube]
* <b>[Architecture](https://github.com/openinfer/PrivateIdentity/wiki/Technical-Overview) </b>[Developer Wiki]
* <b>[Discussion with Demos](https://youtu.be/Zn-pNJ0svJg) </b>[YouTube Channel]
* <b>[Private Biometrics](https://en.wikipedia.org/wiki/Private_biometrics) </b>[Wikipedia]
* <b>[Video Introduction to the Developer's Sandbox](https://youtu.be/6x0b5FckhIA) </b>[YouTube Channel]
* <b>Developer's Sandbox: [https://private.id/demo](https://private.id/demo/?apiKey=00000000000000001962) </b> [Try it now!]

## `FEATURES`
  
### `Micro-App MFA Client`
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Single%20Compoent%20App%201.png)

* Single Page interactive JavaScript module designed to perform like a fully coded application
* Supports all biometric acquisitions, workflows and FHE transformations -- online and offline 
* Runs on 90%+ of all modern devices, browsers and platforms 
* Simple, fast, secure and intuitive for users and developers
* <b>[Link](https://github.com/openinfer/PrivateIdentity/wiki/Single-Component-JavaScript-App)</b> For Setup and Documentation 

Deploy the MFA Client in just a few minutes as an embedded DIV or HTTPS to add biometric enrollment, identity, MFA and account recovery. The Micro-App Client uses an ensemble of pre-trained mobile TensorFlow models to acquire, validate, align, crop, transform and 1-way encrypt the biometric.

The MFA Client does not require on-device training and its small footprint runs well on low-end devices. Modern devices multi-threaded kernels operate in millisecond response time. High-end devices equipped with GPUs and Edge TPUs operate 70-100x faster.   

### `Built-in Privacy:` "Exempt from GDPR, CCPA, BIPA & HIPAA Privacy Law Obligations"

![Privacy graphic](https://github.com/openinfer/PrivateIdentity/blob/master/images/Built%20in%20privacy%201.png)

* Built-in [<b>fully homomorphic encryption</b>](https://en.wikipedia.org/wiki/Private_biometrics) (<b>FHE</b>) enables encrypted match and search operations on encrypted data without allowing any third party to observe the actual data.
* [<B>IEEE 2410 Standard for Biometric Privacy</b>](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D) (SBP) <b>requires FHE</b> for private identity assertion and authentication.
* IEEE 2410 certified compliance, "...<b>guarantees the SBP system does not incur [GDPR](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#gdpr-analysis), [CCPA](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#ccpa-analysis), [BIPA](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#bipa-analysis) or [HIPAA](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#hipaa-analysis) privacy obligations." </b>

Organizations using Cloud Biometric MFA guarantee user privacy and limit risk by irreversibly anonymizing all biometric data and personal data with fully homomorphic encryption (FHE).  FHE payloads are globally unique (i.e. no two payloads are ever the same), positional arrays of 128 floating-point numbers that do not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait.  Anonymized FHE payloads eliminate any known or foreseeable possibility of linking any data to the individual to whom the data originally related.

The [FHE payload is not “Personal Data”](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#951-fhe-payloads-contain-anonymized-data) under General Data Protection Regulation (EU) 2016/679 (“GDPR”), [is not "Personal Information"](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#961-fhe-payloads-contain-deidentified-information) under the California Consumer Privacy Act (“CCPA”), [is not “Biometric Information”](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#971-fhe-payloads-do-not-contain-biometric-identifiers-or-biometric-information) under the Biometric Information Privacy Act (“BIPA”) and [is not "Individually Identifiable Health Information"](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#985-fhe-payloads-do-not-contain-individually-identifiable-health-information) under the Health Insurance Portability and Accountability Act of 1996 ("HIPAA").

### `Flexible Deployment`
![Flexible Deployment Graphic](https://github.com/openinfer/PrivateIdentity/blob/master/images/Flex%20Deploy%201.png)<br>
| Web Apps | Mobile Apps | Enterprise Directories | High-Throughput Biometric Pipelines |
| --- | --- | --- | --- |
| [Embedded DIV](https://github.com/openinfer/PrivateIdentity/wiki#single-component-javascript-application-embedded-div) | [Embedded DIV](https://github.com/openinfer/PrivateIdentity/wiki#single-component-javascript-application-embedded-div) | [SAML/OAuth/OIDC](https://github.com/openinfer/PrivateIdentity/wiki#saml-20-and-oauthoidc-protocols) | [Encryption Engine](https://github.com/openinfer/PrivateIdentity/wiki#encryption-engine-setup) |
| [JavaScript APIs](https://github.com/openinfer/PrivateIdentity/wiki#javascript-apis-predict-enroll-api) | [JavaScript APIs](https://github.com/openinfer/PrivateIdentity/wiki#javascript-apis-predict-enroll-api) | [G Suite®](https://github.com/openinfer/PrivateIdentity/wiki#saml-20-and-oauthoidc-protocols) | [Biometric Search](https://github.com/openinfer/PrivateIdentity/wiki#cloud-biometric-search) |
| | | [PING Identity®](https://github.com/openinfer/PrivateIdentity/wiki#saml-20-and-oauthoidc-protocols) | |
| | | [Okta® Factor Auth](https://github.com/openinfer/PrivateIdentity/wiki#saml-20-and-oauthoidc-protocols) | |

All software tools are included.   The Cloud Biometric MFA solution is available as [SaaS](https://github.com/openinfer/PrivateIdentity/wiki#saas) or [PaaS](https://github.com/openinfer/PrivateIdentity/wiki#paas-deployments) on <b>AWS, GCP and on-premises</b>.

### `No Discrimination`
![Image of No Discrimination](https://github.com/openinfer/PrivateIdentity/blob/master/images/No%20Discrim%201.png)<br>
It took hundreds of experiments and three years to overcome algorithmic bias. We first found a modicum of success moving images into the infrared spectrum. Next, we experimented with homogenized lighting by moving images into the [HSL spectrum](https://en.wikipedia.org/wiki/HSL_and_HSV) and struck gold. HSL filters, it turns out, are quite useful for removing light absorption, skin contour and skin color as distractors. Today, we use hundreds of HSL algorithms during training, prediction, and enrollment (patent pending).

Interestingly, we found moving images into the HSL spectrum did not improve accuracy for Asian faces. We resolved this bias by ethnically balancing our training set with 2K classes from Asian-Celeb.

Our [Face Recognition DNN](https://github.com/openinfer/PrivateIdentity/wiki#facial-recognition) is now 99.9% accurate (absolute accuracy). In a [June 2020 evaluation](https://github.com/openinfer/PrivateIdentity/wiki/EVALUATION-METRICS-FOR-FACE-RECOGNITION-DNN) using 8M images, the face recognition DNN failed to recognize six images. Inspection of the [six images](https://github.com/openinfer/PrivateIdentity/wiki/EVALUATION-METRICS-FOR-FACE-RECOGNITION-DNN#threshold-analysis) found that each was too blurry for recognition.

The face recognition DNN is pre-trained using an ethnically balanced dataset of 50M images (8000 classes) from both Oxford VGGFace2 and Asian-Celeb. The classes in the training dataset are ethnically distributed as follows: 60% Caucasian, 30% Asian, 5% Black and 5% Indian.

### `Facial Recognition`
[![Click for Video Demo of Face w/ Mask Recognition](https://github.com/openinfer/PrivateIdentity/blob/master/images/Face%20PLAY%201.png)](https://youtu.be/Q7gMuVCWAS8 "Face Recognition for Cloud Biometric MFA")

| Accuracy | Type I Error | Type II Error | Speed |
|---|---|---|---|
| 1:1 Verification | | |
| **TMR=99.99%** | FMR=0.0001% | FNMR=0.0001% | Speed=300ms |
| 1:Many Identification | | |
| **IR=99.99%** | FPIR=0.0001% | FNIR=0.0001% | Speed=300ms |

* **Touchless** Face Recognition using any general-purpose camera (webcams, phones) ≥256kB
* Enrolls an unlimited number of users (“unlimited gallery size”)
* Operates in polynomial time irrespective of gallery size
* Trained using the Oxford VGGFace2 dataset ethnically balanced with the Asian-Celeb dataset
* Minimum Imaging Requirements: Face ≥ 224×224 pixels. Camera ≥256kB. Face images smaller than 224×224 pixels may reduce performance.
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters
* MobileNetV2 Architecture, 1.3MB

### `Face + Mask Recognition`
[![Click for Video Demo of Face w/ Mask Recognition](https://github.com/openinfer/PrivateIdentity/blob/master/images/Face%20w%20Mask%20PLAY%201.png)](https://youtu.be/GvtQ-d3TwGc "Face w/ Mask Recognition for Cloud Biometric MFA")

| Accuracy | Type I Error | Type II Error | Speed |
|---|---|---|---|
| 1:1 Verification | | |
| **TMR=99.99%** | FMR=0.0001% | FNMR=0.0001% | Speed=300ms |
| 1:Many Identification | | |
| **IR=98.20%** | FPIR=0.0001% | FNIR=1.80% | Speed=300ms |

* **Touchless** Face w/ Mask Recognition using any general-purpose camera (webcams, phones) ≥256kB
* Enrolls an unlimited number of users (“unlimited gallery size”)
* Operates in polynomial time irrespective of gallery size
* Trained using the Oxford VGGFace2 dataset ethnically balanced with the Asian-Celeb dataset
* Minimum Imaging Requirements: Face ≥ 224×224 pixels. Camera ≥256kB. Face images smaller than 224×224 pixels may reduce performance.
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters
* MobileNetV2 architecture, 1.3MB

### `Fingerprint Identification`
[![Click for Video Demo of Fingerprint Recognition](https://github.com/openinfer/PrivateIdentity/blob/master/images/Fingerprint%20recogni%20PLAY%203.png)](https://youtu.be/J10akfFzxHI "Fingerprint Identification for Cloud Biometric MFA")

| Accuracy | Type I Error | Type II Error | Speed |
|---|---|---|---|
| 1:1 Verification | | |
| **TMR=99.99%** | FMR=0.0001% | FNMR=0.0001% | Speed=300ms |
| 1:Many Identification | | |
| **IR=96.30%** | FPIR=0.0001% | FNIR=3.70% | Speed=300ms |

* **Touchless** Fingerprint Identification using optical scan (camera) or capacitive sensor
* Supports any general-purpose camera (Webcams, phones) ≥720P (1MP)
* Enrolls an unlimited number of users (“unlimited gallery size”)
* Operates in polynomial time irrespective of gallery size
* Trained using the NIST Special Database 4 and CASIA-FingerprintV5
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters
* Minimum Imaging Requirements: Fingerprint ≥ 320×240 pixels. Camera ≥720P.
* MobileNetV2 Architecture, 900kB
* Accepts images from any finger

### `Voice (Speaker) Identification`
[![Click for Video Demo of Voice Recognition](https://github.com/openinfer/PrivateIdentity/blob/master/images/Voice%20PLAY%201.png)](https://youtu.be/eCfB8ixRapw "Voice Recognition for Cloud Biometric MFA")

| Accuracy | Type I Error | Type II Error | Speed |
|---|---|---|---|
| 1:1 Verification | | |
| **TMR=99.99%** | FMR=0.0001% | FNMR=0.0001% | Speed=300ms |
| 1:Many Identification | | |
| **IR=95.20%** | FPIR=0.0001% | FNIR=4.80% | Speed=300ms |

* **Touchless** Text-, language- and accent-independent voice identification with 1 second of audio
* Enrolls an unlimited number of users (“unlimited gallery size”)
* Operates in polynomial time irrespective of gallery size
* Minimum Audio Requirements: Voice ≥1 second. Audio ≥8.1kHz (telephone quality). The minimum voice input size is 100ms. Voice input < 1 second may reduce performance.
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters
* MobileNetv2 architecture, 3.5MB

### `Helper Networks` (Geometry DNN → Validation DNN → Embedding DNN)

| Helper DNN | Description | Biometric Modalities |
| --- | --- | --- |
| <b>Geometry DNNs</b> | Transforms valid biometric images into geometric primitives. Returns x,y coordinates. | [Face, Face with Mask, Fingerprint](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-face-wmask-and-fingerprint-geometry-detection-dnns) |
| <b>Validation DNNs</b> | Aligns and crops and detects video and image spoofing, eye blinks, face masks, eyeglasses and quality human voice. Returns a validation score between 0 and 100. | [Face, Face with Mask, Fingerprint](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-face-with-mask--fingerprint-validation-dnns), [Voice](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-validation-dnn) |
| <b>Embedding DNNs<b/> | FHE transforms validated biometric input into a distance-measurable two-dimensional positional array of 128 floating-point numbers (embedding, or “FHE payload”) | [Face, Face with Mask, Fingerprint](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-facemask-and-fingerprint-embedding-dnns), [Voice](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#voice-embedding-dnn) |

### `Offline Authentication`

* <b>Acquires biometrics at the edge</b> with or without a network (TensorFlow at the Edge)
* <b>Automatically switches to Local Mode</b> after it detects loss of network
* <b>Authenticate user in 10ms</b> with intermittent or no Internet connection as long as the user authenticates at least once to the device while online
* <b>Automatically detects</b> the loss of network connectivity.

### `IAM Integrations`
![IAM Logos](https://github.com/openinfer/PrivateIdentity/blob/master/images/IAM%20Integr%201.png)

* Integrates with your existing Enterprise directory using SAML 2.0 or OAuth/OIDC
* [Google G Suite Integration](https://github.com/openinfer/PrivateIdentity/wiki/SAML-2.0#integration-with-gsuite)
* [Ping Identity PingFederate® Integration](https://github.com/openinfer/PrivateIdentity/wiki/Enterprise-Integrations#ping-identity)
* [Okta® Factor Authentication Integration](https://github.com/openinfer/PrivateIdentity/wiki/Enterprise-Integrations#okta)
* [Azure Active Directory (AAD) Integration](https://github.com/openinfer/PrivateIdentity/wiki/SAML-2.0#integration-with-microsoft-azure)

### `Digital Identity Verification`

![hand holding drivers license](https://github.com/openinfer/PrivateIdentity/blob/master/images/Identity%20Verification%201.png)

* <b>Meets AML/KYC identity-proofing requirements </b>for remote presentation of identifying materials or information by an end user for KYC
* Allows organizations to verify user to [Enrollment Level 2](https://arch.idmanagement.gov/usecases/12_proofidentityloa2/)</b> using an official Photo ID card or passport.
* <b>Compares ID cards or passport photo</b> to enrolled user's face
* <b>Compares name and contact information on ID card </b>or passport to mobile phone billing records
* <b>Verifies phone owner with SMS </b>message to phone
* <b>Preserves privacy</b> by having no personal data leave the local device
* [Link to documentation on Github](https://github.com/openinfer/PrivateIdentity/wiki/Verified-Enroll)

### `Account Recovery`
![woman gesturing that she forgot her password](https://github.com/openinfer/PrivateIdentity/blob/master/images/Account%20Recovery%201.png)

* <b>Users enroll once</b> using multiple biometric modalities (face, fingerprint, voice) to ensure future access.
* <b>Quickly and accurately identifies locked-out account holders</b> and restores access

## `OPEN STANDARDS, ENCRYPTION & PRIVACY`

![Image of lego blocks ](https://github.com/openinfer/PrivateIdentity/blob/master/images/Open%20Stanards%201.png)

Private Identity is certified compliant with IEEE 2410 Standard for Biometric Privacy, ISO 27001:2013 International Standard for Information Security Management, ISO 9001:2015 International Standard for Quality Management Systems, US DoD Standard Trusted Computer System Evaluation Criteria (TCSEC), US ODNI ICD 503 Intelligence Community Technology Systems Security Risk Management, Certification and Accreditation and US DoD Multiple Independent Levels of Security/Safety (MILS) Architecture, and compliant with W3C Web Authentication API (WebAuthn), FIPS 197, TLS, IPSEC and SSL.
> <b>Third-party accredited certification</b> (3PAO) is provided by [GMS Registrar](https://gmsaudit.com/)

| Open Standards for Privacy & Encryption | Description | Link |
| --- | --- | --- |
| **IEEE 2410 Standard for Biometric Privacy (SBP)** Certified Compliant | Guarantees compliant systems do not incur GDPR, CCPA, BIPA or HIPAA privacy obligations. Requires fully homomorphic encryption (FHE) for private identity assertion and authentication. | [Link]([https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D)) to approved Draft Standard |
| **W3C WebAuthn** Compliant | Enables creation and use of strong, attested, scoped, public key-based credentials by Web applications | [Link](https://www.w3.org/TR/webauthn/) to Standard |
| **US ODNI ICD 503** Certified Compliant | Applies to all US Government organizations, their commercial contractors, and Allied Government information systems that process, store, or communicate intelligence information. | [Link]([https://www.dni.gov/files/documents/ICD/ICD_503.pdf](https://www.dni.gov/files/documents/ICD/ICD_503.pdf)) to ICD |
| **US DOD Standard Trusted Computer System Evaluation Criteria (TCSEC)** Certified Compliant | Original standard for processing and storage of classified and other sensitive DoD information. | [Link](https://csrc.nist.gov/csrc/media/publications/conference-paper/1998/10/08/proceedings-of-the-21st-nissc-1998/documents/early-cs-papers/dod85.pdf) to Standard |
| **FIPS 197 Advanced Encryption Standard (AES)** Compliant | Guideline for Implementing Cryptography in the US Government. | [Link](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf) to NIST 800-21 |
| **TLS / IPSEC / SSL** | Standard protocols providing privacy and data integrity between two or more communicating computer applications. | [Link](https://tools.ietf.org/html/rfc8446) to IETF |

<br>

| Open Standards for Security Architecture | Description | Link |
| --- | --- | --- |
| **ISO 27001:2013** Information Security Management Standard - Certified Compliant | International Standard for information risk management process includes all legal, physical and technical controls. | [Link](https://www.iso.org/isoiec-27001-information-security.html) to ISO/IEC 27001 |
| **ISO 9001:2015** Quality Management Standard Certified Compliant | International Standard ensures software satisfies statutory and regulatory requirements and meets the needs of customers and other stakeholders. | [Link](https://www.iso.org/iso-9001-quality-management.html) to ISO 9000
| **SAML 2.0/ OAuth 2.0 / OIDC** | Standard protocols for authorization, federation, identity management and single sign-on (SSO). | [Link](https://tools.ietf.org/html/rfc8252) to IETF |
| **DoD MILS** Multiple Independent Levels of Security/Safety (MILS) Architecture | Compartmentalized approach to the design of security-critical, safety-critical, high-assurance computing systems. | [Link](https://mils.community/) to MILS |

## `FLEXIBLE DEPLOYMENT`

### `SAML 2.0 and OAuth/OIDC`

* Supports SAML 2.0 and OAuth/OIDC protocols
* Integrates with your existing Enterprise directory
* [Google G Suite Integration](https://github.com/openinfer/PrivateIdentity/wiki/SAML-2.0#integration-with-gsuite)
* [Ping Identity PingFederate® Integration](https://github.com/openinfer/PrivateIdentity/wiki/Enterprise-Integrations#ping-identity)
* [Okta® Factor Authentication Integration](https://github.com/openinfer/PrivateIdentity/wiki/Enterprise-Integrations#okta)
* [Azure Active Directory (AAD) Integration](https://github.com/openinfer/PrivateIdentity/wiki/SAML-2.0#integration-with-microsoft-azure)

***

### `Micro-App MFA Client` (Embedded DIV)
![Javascript](https://github.com/openinfer/PrivateIdentity/blob/master/images/JS%20Deploy%202.png)
* Deploys effortlessly with no software to install and no hardware to buy
* Users enroll in four seconds, authenticate in 300ms
* Powered by TensorFlow.js
* Preserves privacy by acquiring and FHE transforming biometric data at the edge
* Runs on 90%+ of all modern devices
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/Client-Applications) for additional information.
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/DIV-HTML)


***

### JavaScript APIs (Predict Enroll API)
[![Click for Video Demo of JavaScript APIs](https://github.com/openinfer/PrivateIdentity/blob/master/images/JS%20API%20PLAY%201.png)](https://youtu.be/wjaFHuELTJA "JavaScript APIs for Cloud Biometric MFA")

* Lightweight Javascript library with 2 API calls (enroll and predict)
* Accepts image and audio inputs and returns UUID
* Includes a Web sandbox to exercise the API
* Deploys effortlessly with no software to install and no hardware to buy
* Users enroll in four seconds, authenticate in 300ms
* Preserves privacy by acquiring and FHE transforming biometric data at the edge
* Runs on 90% of all modern devices
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/JavaScript-API) for setup.

> **Method: window.enroll**(uuid, apiKey, 'face', images1, 'voice', voiceFile, 'fingerprint', images2);

> **Method: window.predict**(apiKey, 'face', images1, 'voice', voiceFile, 'fingerprint', images2);

***

### ENCRYPTION ENGINE (Setup)

![Picture of shield with lock on front](https://github.com/openinfer/PrivateIdentity/blob/master/images/Encryption%20Engine%202.png)

* Asynchronous pre-processing engine for massive plaintext biometric ingestion
* Accepts Base-64 plaintext images, video or audio using directory scanning or RESTful API
* Elastic, fault-tolerant and load balanced Kubernetes clusters
* Decoupled from back-end cluster for privacy

The Encryption Engine identifies multiple faces and fingerprints per frame, identifies voice in audio, provides data augmentation as needed, creates a 1-way hash (FHE transformation) for subsequent processing, and then immediately discards the original biometrics. FHE transformation requires 10ms _constant time_ using cloud or on-premise AI services. [Link for setup](https://github.com/openinfer/PrivateIdentity/wiki/pb-utils).

***

### Cloud Biometric Search
![Cloud Biometric Search icon](https://github.com/openinfer/PrivateIdentity/blob/master/images/Biometric%20Search%201.png)

* <b>Asynchronous pre-processing engine</b> for massive biometric match
* Accepts Base-64 plaintext images, video or audio by directory scanning or RESTful API
* Elastic, fault-tolerant, load balanced Kubernetes identification service that runs anywhere
* Maintains full accuracy and performance through real-world boundary conditions
* Decoupled from back-end cluster for privacy (See [link](https://github.com/openinfer/PrivateIdentity/wiki/pb-utils))

Cloud Biometric Search provides high-demand identification tasks including asynchronous face, face+mask, fingerprint and voice identification with unlimited throughput using elastic, load-balanced, fault-tolerant Kubernetes clusters.

Built on the same infrastructure as the [Encryption Engine](https://github.com/openinfer/PrivateIdentity/wiki#encryption-engine-setup), Biometric Search identifies multiple faces and fingerprints per frame, identifies voice in audio, provides data augmentation as needed, FHE transforms biometrics and then immediately discards the original biometrics (to preserve privacy). Search returns identity in 300ms constant time using Cloud AI services and load-balanced, elastic, fault-tolerant Kubernetes clusters.

***

### REST APIs
![RESTful API image](https://github.com/openinfer/PrivateIdentity/blob/master/images/REST%20API2.png)

* Four APIs that communicate RESTful using JSON
* Receives FHE payloads as input (use the JavaScript app, JavaScript APIs or Encryption Engine to create payloads)
* Enrolls in four seconds, authenticates in 300ms
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-2020-Standard-for-Biometric-Privacy-(SBP)-Server#SBP-API-Overview) for additional information

> POST “/trueid/v1.1/enroll”

> POST “/trueid/v1.1/predict”

> POST “/trueid/v1.1/liveness”

> POST “/trueid/v1.1/verify”

***

### `SaaS`
![Picture of cloud](https://github.com/openinfer/PrivateIdentity/blob/master/images/SaaS%20Deploy%202.png)

#### SaaS (Open)

* <b>The AWS Marketplace</b> listing is not yet public. Please send your AWS account to api@private.id to be added to the whitelist.
* <b>Provides API Key access to shared </b>elastic, load balanced and fault tolerant Web services managed and run on AWS by Private Identity.

#### SaaS (Dedicated for a single customer)`

* <b>Click here for AWS Marketplace</b> Listing (_Not yet public -- send us your AWS account for access_)
* <b>Provides API Key access to private </b>elastic, load balanced and fault tolerant Web services managed and run on AWS by Private Identity

***

### PaaS Deployments
![PaaS icon](https://github.com/openinfer/PrivateIdentity/blob/master/images/PaaS%20DEploy%202.png)

* Please send an email to api@private.id to request the Cloud Templates.

#### Google Cloud Platform (GCP)
<b>For PaaS integrations on GCP,</b> Private Identity leverages TensorFlow.js, Cloud AI Platform, Cloud Compute, K8s Engine, Memory Store (Redis), MySQL clustered & fault tolerant, Cloud Storage buckets & data lakes, Cloud Speech to Text, Cloud Vision API, Cloud DNS and Cloud Identity.

#### Amazon Web Services (AWS)
<b>For PaaS integrations on AWS</b>, Private Identity leverages TensorFlow.js, Sagemaker, Compute, EKS, In Memory Store (Redis), MySQL clustered & fault tolerant, S3, AIM, and Cloud Speech to Text, Cloud Vision API and Route 53.

#### PaaS Web Tier (Setup)
Docker image of the Web tier that runs in elastic, load balanced, fault tolerant Kubernetes clusters on-premise or any public or private cloud. Connects to Private Identity Web services managed and run on AWS by Private Identity.

#### PaaS Entire Tier (Setup)
Docker images of all software that runs in elastic, load balanced, fault tolerant Kubernetes clusters on-prem or any public or private cloud. Includes all backend services and has no requirement to connect to Private Identity.
