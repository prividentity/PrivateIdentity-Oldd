[![logo-name](https://github.com/openinfer/PrivateIdentity/blob/master/images/CBMFA%20White%20Space%20on%20Right.png)](https://www.private.id/)

## VIDEO INTRODUCTION
[![IMAGE ALT TEXT](https://github.com/openinfer/PrivateIdentity/blob/master/images/CBMFA%20Overview%20Video%20Img3.png)](https://youtu.be/G33UR87I81E "Quick Introduction to Cloud Biometric MFA")

We threw the old algorithms into the trash and started fresh with a clean-sheet design. Cloud Biometric MFA took three years and seventeen patents to build. This all-new AI/ML/Fully Homomorphic Encryption (FHE) recognition algorithm features absolute accuracy, 300ms response time, unlimited users and full privacy. Now, for the first time, your private identity is no longer tied to a device, username, password, token or shared secret.

## `OVERVIEW`

* [Face](https://github.com/openinfer/PrivateIdentity/wiki#facial-recognition), [Face w/ Mask](https://github.com/openinfer/PrivateIdentity/wiki#face--mask-recognition), [Voice](https://github.com/openinfer/PrivateIdentity/wiki#voice-speaker-identification) and [Fingerprint](https://github.com/openinfer/PrivateIdentity/wiki#fingerprint-identification) 1:1 Verify, 1:n Identity and Authentication
* <b>[Guaranteed Privacy](https://github.com/openinfer/PrivateIdentity/wiki#built-in-privacy-exempt-from-gdpr-ccpa-bipa--hipaa-privacy-law-obligations) with 1-way Fully Homomorphic Encryption</b> 
* <b>Enroll once</b>, then authenticate on almost any device
* <b>[Deploys instantly](https://github.com/openinfer/PrivateIdentity/wiki#mfa-micro-app-web-client) with no software to install and no hardware to buy
* <b>[Integrates easily](https://github.com/openinfer/PrivateIdentity/wiki#flexible-deployment) into Web and mobile apps</b>, Enterprise IAM solutions and high-throughput biometric pipelines
* <b>[Unbiased algorithms](https://github.com/openinfer/PrivateIdentity/wiki#no-discrimination)</b> recognize everyone equally
* <b>[Exempt](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS) from GDPR, CCPA, BIPA and HIPAA </b>privacy law obligations

## `RESOURCES`

* <b>Short Video Introduction</b> [[AWS]](https://www.youtube.com/watch?v=G33UR87I81E&feature=youtu.be "Short Video Introduction AWS Flavored") [[GCP]](https://youtu.be/CuE3x543qKo "Short Video Introduction GCP Flavored")
* <b>Getting Started with Private Identity</b> [YouTube]
* <b>[Architecture](https://github.com/openinfer/PrivateIdentity/wiki/Technical-Overview) </b>[Developer Wiki]
* <b>[Discussion with Demos](https://youtu.be/Zn-pNJ0svJg) </b>[YouTube Channel]
* <b>[Private Biometrics](https://en.wikipedia.org/wiki/Private_biometrics) </b>[Wikipedia]
* <b>[Developer's Sandbox](https://private.id/demo/?apiKey=00000000000000001962) </b> [[Video Tutorial]](https://youtu.be/6x0b5FckhIA)

## `FEATURES`
  
### `MFA Micro-App` Web Client 
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Single%20Compoent%20App%201.png)
* Interactive JavaScript Single Page App that performs like a fully coded application
* Supports all biometric acquisition, workflows and FHE transformations -- online and offline 
* Runs on 90%+ of all modern devices, browsers, platforms and clouds 
* Simple, fast, secure and intuitive for users and developers
* <b>[Link](https://github.com/openinfer/PrivateIdentity/wiki/Tutorials)</b> For Tutorials and Documentation 

Deploy the MFA Micro-App in just a few minutes as an embedded DIV or HTTPS for secure biometric enrollment, identity, MFA and account recovery. The MFA Micro-App uses an ensemble of pre-trained mobile TensorFlow models to acquire, validate, align, crop, transform and 1-way encrypt the biometric.

The MFA Micro-App does not require on-device training and its small footprint runs on low-end devices. Modern, high-end devices with multi-threaded kernels operate in millisecond response time. Modern devices equipped with GPUs and Edge TPUs operate 70-100x faster. 
<br>

### `Built-in Privacy:` "Exempt from GDPR, CCPA, BIPA & HIPAA Privacy Law Obligations"

![Privacy graphic](https://github.com/openinfer/PrivateIdentity/blob/master/images/Built%20in%20privacy%201.png)

* Built-in [<b>1-way fully homomorphic encryption</b>](https://en.wikipedia.org/wiki/Private_biometrics) (<b>FHE</b>) enables encrypted match and search operations on encrypted data without allowing any third party to observe the actual data.
* [<B>IEEE 2410 Standard for Biometric Privacy</b>](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D) (SBP) <b>requires FHE</b> for private identity assertion and authentication.
* IEEE 2410 certified compliance, "...<b>guarantees the SBP system does not incur [GDPR](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#gdpr-analysis), [CCPA](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#ccpa-analysis), [BIPA](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#bipa-analysis) or [HIPAA](https://github.com/openinfer/PrivateIdentity/wiki/EXEMPT-FROM-PRIVACY-OBLIGATIONS#hipaa-analysis) privacy obligations." </b>

Organizations using Cloud Biometric MFA guarantee user privacy and limit risk by irreversibly anonymizing all biometric data and personal data with one-way fully homomorphic encryption (FHE).  FHE payloads are globally unique (i.e. no two payloads are ever the same), positional arrays of 128 floating-point numbers that do not contain biological or behavioral characteristics, imagery or a template of any physiological, biological or behavioral trait.  Anonymized FHE payloads eliminate any known or foreseeable possibility of linking any data to the individual the data originally related.

The FHE payload is [not “Personal Data”](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#951-fhe-payloads-contain-anonymized-data) under General Data Protection Regulation (EU) 2016/679 (“GDPR”), is [not "Personal Information"](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#961-fhe-payloads-contain-deidentified-information) under the California Consumer Privacy Act (“CCPA”), is [not “Biometric Information”](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#971-fhe-payloads-do-not-contain-biometric-identifiers-or-biometric-information) under the Biometric Information Privacy Act (“BIPA”) and is [not "Individually Identifiable Health Information"](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D#985-fhe-payloads-do-not-contain-individually-identifiable-health-information) under the Health Insurance Portability and Accountability Act of 1996 ("HIPAA").
<br>

### `Flexible Deployment`
![Flexible Deployment Graphic](https://github.com/openinfer/PrivateIdentity/blob/master/images/Flex%20Deploy%201.png)<br>
| Web Apps | Mobile Apps | Enterprise Directories | High-Throughput Biometric Pipelines |
| --- | --- | --- | --- |
| [MFA Micro-App](https://github.com/openinfer/PrivateIdentity/wiki#single-component-javascript-application-embedded-div) | [MFA Micro-App](https://github.com/openinfer/PrivateIdentity/wiki#single-component-javascript-application-embedded-div) | [SAML/OAuth/OIDC](https://github.com/openinfer/PrivateIdentity/wiki#saml-20-and-oauthoidc-protocols) | [Encryption Engine](https://github.com/openinfer/PrivateIdentity/wiki#encryption-engine-setup) |
| [JavaScript APIs](https://github.com/openinfer/PrivateIdentity/wiki#javascript-apis-predict-enroll-api) | [JavaScript APIs](https://github.com/openinfer/PrivateIdentity/wiki#javascript-apis-predict-enroll-api) | [G Suite®](https://github.com/openinfer/PrivateIdentity/wiki#saml-20-and-oauthoidc-protocols) | [Biometric Search](https://github.com/openinfer/PrivateIdentity/wiki#cloud-biometric-search) |
| | | [PING Identity®](https://github.com/openinfer/PrivateIdentity/wiki#saml-20-and-oauthoidc-protocols) | |
| | | [Okta® Factor Auth](https://github.com/openinfer/PrivateIdentity/wiki#saml-20-and-oauthoidc-protocols) | |

<br>

### `No Discrimination`<br>
![Image of No Discrimination](https://github.com/openinfer/PrivateIdentity/blob/master/images/No%20Discrim%201.png)<br>
It took hundreds of experiments and three years to overcome algorithmic bias. At first, we found reasonable results moving images into the infrared spectrum to remove light absorption, skin contour and skin color as distractors. An insightful journal article from Microsoft Research then led us to try homogenized lighting. Today, our solution uses hundreds of [HSL](https://en.wikipedia.org/wiki/HSL_and_HSV) filters for training and enrollment and two HSL filters (HSL1 and HSL2) for prediction (patent pending).

Interestingly, moving images into the HSL space did not significantly improve accuracy for Asian faces. We resolved this bias by ethnically balancing our training set with 2K classes from Asian-Celeb.

Our [Face Recognition DNN](https://github.com/openinfer/PrivateIdentity/wiki#facial-recognition) is now 99.9% accurate (absolute accuracy). In a [June 2020 evaluation](https://github.com/openinfer/PrivateIdentity/wiki/EVALUATION-METRICS-FOR-FACE-RECOGNITION-DNN) using 8M images, our Face Recognition DNN failed to recognize [six images](https://github.com/openinfer/PrivateIdentity/wiki/EVALUATION-METRICS-FOR-FACE-RECOGNITION-DNN#threshold-analysis). Visual inspection of the images found that each was too blurry for recognition.
<br><br>

### `Facial Recognition`
[![Click for Video Demo of Face w/ Mask Recognition](https://github.com/openinfer/PrivateIdentity/blob/master/images/Face%20PLAY%201.png)](https://youtu.be/Q7gMuVCWAS8 "Face Recognition for Cloud Biometric MFA")

| Accuracy | Type I Error | Type II Error | Speed |
|---|---|---|---|
| 1:1 Verification | | |
| **TMR=99.99%** | FMR=0.0001% | FNMR=0.0001% | Speed=300ms |
| 1:Many Identification | | |
| **IR=99.99%** | FPIR=0.0001% | FNIR=0.0001% | Speed=300ms |

* **Touchless** Face Recognition using any general-purpose camera (Webcams, phones) ≥256kB
* Enrolls an unlimited number of users (“unlimited gallery size”)
* Operates in _constant time_ irrespective of gallery size
* Trained using the Oxford VGGFace2 dataset ethnically balanced with the Asian-Celeb dataset
* Minimum Imaging Requirements: Face ≥ 224×224 pixels. Face images smaller than 224×224 pixels may reduce performance.
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters
* MobileNetV2 architecture, 1.3MB
<br>

### `Face with Mask Recognition`

[![Click for Video Demo of Face w/ Mask Recognition](https://github.com/openinfer/PrivateIdentity/blob/master/images/Face%20w%20Mask%20PLAY%201.png)](https://youtu.be/GvtQ-d3TwGc "Face w/ Mask Recognition for Cloud Biometric MFA")
<br>
| Accuracy | Type I Error | Type II Error | Speed |
|---|---|---|---|
| 1:1 Verification | | |
| **TMR=99.99%** | FMR=0.0001% | FNMR=0.0001% | Speed=300ms |
| 1:Many Identification | | |
| **IR=98.20%** | FPIR=0.0001% | FNIR=1.80% | Speed=300ms |

* **Touchless** Face w/ Mask Recognition using any general-purpose camera (Webcams, phones) ≥256kB
* Enrolls an unlimited number of users (“unlimited gallery size”)
* Operates in _constant time_ irrespective of gallery size
* Trained using the Oxford VGGFace2 dataset ethnically balanced with the Asian-Celeb dataset
* Minimum Imaging Requirements: Face ≥ 224×224 pixels. Face images smaller than 224×224 pixels may reduce performance.
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters
* MobileNetV2 architecture, 1.3MB
<br>

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
* Accepts input images from any finger
* Enrolls an unlimited number of users (“unlimited gallery size”)
* Operates in _constant time_ irrespective of gallery size
* Trained using the NIST Special Database 4 and CASIA-FingerprintV5
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters
* Minimum Imaging Requirements: Fingerprint ≥ 320×240 pixels. Camera ≥720P.
* MobileNetV2 architecture, 900kB
<br>

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
* Operates in _constant time_ irrespective of gallery size
* Minimum Audio Requirements: Voice ≥1 second. Audio ≥8.1kHz (telephone quality). The minimum voice input size is 100ms. Voice input < 1 second may reduce performance.
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters
* MobileNetv2 architecture, 3.5MB
<br>

### `Offline Authentication`
[![Click for Video Demo of Offline Authentication](https://github.com/openinfer/PrivateIdentity/blob/master/images/Offline%20Auth%20PLAY%201.png)](https://youtu.be/ZexmPgCH9cQ "Offline Auth for Cloud Biometric MFA")

* <b>Acquires biometrics at the edge</b> with or without a network (TensorFlow at the Edge)
* <b>Automatically switches to Local Mode</b> after it detects loss of network
* <b>Authenticate user in 10ms</b> with intermittent or no Internet connection as long as the user authenticates at least once to the device while online
* <b>Automatically detects</b> the loss of network connectivity
<br>

## `Solutions`

### `IAM Integrations`
![IAM Logos](https://github.com/openinfer/PrivateIdentity/blob/master/images/IAM%20Integr%201.png)

* Integrates with your existing Enterprise directory using SAML 2.0 or OAuth/OIDC
* [Google G Suite Integration](https://github.com/openinfer/PrivateIdentity/wiki/SAML-2.0#integration-with-gsuite)
* [Ping Identity PingFederate® Integration](https://github.com/openinfer/PrivateIdentity/wiki/Enterprise-Integrations#ping-identity)
* [Okta® Factor Authentication Integration](https://github.com/openinfer/PrivateIdentity/wiki/Enterprise-Integrations#okta)
* [Azure Active Directory (AAD) Integration](https://github.com/openinfer/PrivateIdentity/wiki/SAML-2.0#integration-with-microsoft-azure)
<br>

### `Digital Identity Verification`

![hand holding drivers license](https://github.com/openinfer/PrivateIdentity/blob/master/images/Identity%20Verification%201.png)

* <b>Meets AML/KYC identity-proofing requirements </b>for remote presentation of identifying materials or information by an end user for KYC
* Allows organizations to verify user to [Enrollment Level 2](https://arch.idmanagement.gov/usecases/12_proofidentityloa2/)</b> using an official Photo ID card or passport.
* <b>Compares ID cards or passport photo</b> to enrolled user's face
* <b>Compares name and contact information on ID card </b>or passport to mobile phone billing records
* <b>Verifies phone owner with SMS </b>message to phone
* <b>Preserves privacy</b> using 1-way fully homomorphic encryption
* [Link to tutorials](https://github.com/openinfer/PrivateIdentity/wiki/Verified-Enroll) and documentation
<br>

### `Account Recovery`
![woman gesturing that she forgot her password](https://github.com/openinfer/PrivateIdentity/blob/master/images/Account%20Recovery%201.png)

* <b>Users enroll once</b> using multiple biometric modalities (face, fingerprint, voice) to ensure future access
* Available anytime after enrollment
* <b>Quickly and accurately identifies locked-out account holders</b> and restores access
<br>

## `OPEN STANDARDS`

![Image of lego blocks ](https://github.com/openinfer/PrivateIdentity/blob/master/images/Open%20Stanards%201.png)

Private Identity is certified compliant with IEEE 2410 Standard for Biometric Privacy, ISO 27001:2013 International Standard for Information Security Management, ISO 9001:2015 International Standard for Quality Management Systems, US DoD Standard Trusted Computer System Evaluation Criteria (TCSEC), US ODNI ICD 503 Intelligence Community Technology Systems Security Risk Management, Certification and Accreditation and US DoD Multiple Independent Levels of Security/Safety (MILS) Architecture, and compliant with W3C Web Authentication API (WebAuthn), FIPS 197, TLS, IPSEC and SSL.
> <b>Third-party accredited certification</b> (3PAO) is provided by [GMS Registrar](https://gmsaudit.com/)

| Open Standards for Privacy & Encryption | Description | Link |
| --- | --- | --- |
| **IEEE 2410 Standard for Biometric Privacy (SBP)** Certified Compliant | Guarantees compliant systems do not incur GDPR, CCPA, BIPA or HIPAA privacy obligations. Requires fully homomorphic encryption (FHE) for private identity assertion and authentication. | [Link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D)) to approved Draft Standard |
| **W3C WebAuthn** Compliant | Enables creation and use of strong, attested, scoped, public key-based credentials by Web applications | [Link](https://www.w3.org/TR/webauthn/) to Standard |
| **US ODNI ICD 503** Certified Compliant | Applies to all US Government organizations, their commercial contractors, and Allied Government information systems that process, store, or communicate intelligence information. | [Link](https://www.dni.gov/files/documents/ICD/ICD_503.pdf) to ICD |
| **US DOD Standard Trusted Computer System Evaluation Criteria (TCSEC)** Certified Compliant | Original DOD standard for processing and storage of classified and other sensitive information. | [Link](https://csrc.nist.gov/csrc/media/publications/conference-paper/1998/10/08/proceedings-of-the-21st-nissc-1998/documents/early-cs-papers/dod85.pdf) to Standard |
| **FIPS 197 Advanced Encryption Standard (AES)** Compliant | Guideline for Implementing Cryptography in the US Government. | [Link](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf) to NIST 800-21 |
| **TLS / IPSEC / SSL** | Standard protocols providing privacy and data integrity between two or more communicating computer applications. | [Link](https://tools.ietf.org/html/rfc8446) to IETF |

<br>

| Open Standards for Security Architecture | Description | Link |
| --- | --- | --- |
| **ISO 27001:2013** Information Security Management Standard - Certified Compliant | International Standard for information risk management process includes all legal, physical and technical controls. | [Link](https://www.iso.org/isoiec-27001-information-security.html) to ISO/IEC 27001 |
| **ISO 9001:2015** Quality Management Standard Certified Compliant | International Standard ensures software satisfies statutory and regulatory requirements and meets the needs of customers and other stakeholders. | [Link](https://www.iso.org/iso-9001-quality-management.html) to ISO 9000
| **SAML 2.0/ OAuth 2.0 / OIDC** | Standard protocols for authorization, federation, identity management and single sign-on (SSO). | [Link](https://tools.ietf.org/html/rfc8252) to IETF |
| **DoD MILS** Multiple Independent Levels of Security/Safety (MILS) Architecture | Compartmentalized approach to the design of security-critical, safety-critical, high-assurance computing systems. | [Link](https://mils.community/) to MILS |
<br>

## Tutorials and Documentation
Click [Here](https://github.com/openinfer/PrivateIdentity/wiki/Tutorials) to Get Started!