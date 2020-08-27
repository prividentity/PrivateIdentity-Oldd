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
* Powered by TensorFlow.js
* Runs on [90% of all modern devices](https://caniuse.com/#feat=wasm) (this are the same devices as TensorFlow) 
* Synchronously acquires biometric images, videos and audio 
* Preserves privacy using FHE transformations at the Edge 
* Provides exception processing 

Provides users with a convenient, browser-based omni-channel UX that operates all modern browsers, platforms and more than [90% of all modern devices](https://caniuse.com/#feat=wasm) (every device that runs TensorFlow). 

The Cloud Biometric MFA Javascript client is powered by TensorFlow.js and supports biometric acquisition and high-throughput FHE transformation at the Edge. It provides a consistent UX across all modern browsers, devices, platforms and clouds. It runs on 90% of all modern hardware. The client is easy to deploy as it does not require any additional software, plugins or extensions to be installed. It uses general-purpose hardware (phones and Webcams) and/or input from specialized biometric acquisition systems and does not require new hardware to be purchased. [Link this to embedded Div]




. The client provides a consistent UX across all modern browsers, devices, platforms and clouds.  It runs on [90% of all modern devices](https://caniuse.com/#feat=wasm).  The client is easy to deploy as it does not require any additional software, plugins or extensions to be installed.  It uses general-purpose hardware (phones and Webcams) and/or input from specialized biometric acquisition systems and does not require new hardware to be purchased. [Link this to embedded Div] 

### Built-in Privacy
Built-in patented fully homomorphic encryption (FHE) complies with privacy laws worldwide including GDPR, CCPA and BIPA and IEEE 2410 Standard for Biometric Privacy. 

### Flexible Deployment
![Flexible Deployment Graphic](https://github.com/openinfer/PrivateIdentity/blob/master/images/Flex%20Deploy%201.png)<br>
Go to market faster with built-in integrations for popular IAM solutions, SAML 2.0 and OAuth/OIDC. Use SaaS or PaaS running in the cloud or on the edge. REST APIs and Javascript APIs are available for embedded apps.

### No Discrimination
![Image of No Discrimination](https://github.com/openinfer/PrivateIdentity/blob/master/images/No%20Discrim%201.png)<br>
Private Identity’s deep learning technology maintains absolute accuracy across all ethnicities, skin tones, genders, age, and faces and fingerprints. Recognition is accurate with up to 30% occlusions including facial hair, abrasions, masks, blurry images and image rotations. 

### Facial Recognition 
![woman's face](https://github.com/openinfer/PrivateIdentity/blob/master/images/Face%20Recogni%201.png)<br>
Authenticate, verify, identify and search an unlimited gallery in real time. Absolute accuracy (IR=99.99%) with almost no false positives (FPIR=0.0001% ). Runs on any modern browser, device, platform or cloud with any standard camera >256kB. Returns identity in 300ms.

### Face + Mask Recognition  
![woman wearing face mask](https://github.com/openinfer/PrivateIdentity/blob/master/images/Face%20w%20Mask%201.png)
Authenticate, verify, identify and search an unlimited gallery in real time. Highly accurate (IR=98.59%) with almost no false positives (FPIR=0.0001% ). Runs on any modern browser, device or platform with any standard camera >256kB. Returns identity in 300ms.

### Voice (Speaker) Identification 
![man speaking into phone](https://github.com/openinfer/PrivateIdentity/blob/master/images/voice%20recogni%201.png)
Authenticate, verify, identify and search an unlimited gallery of human voices in real time. Voice identity is text, language and accent agnostic and highly accurate (IR=92.5%) with nearly zero false positives (FPIR=0.0001%). Requires at least one second of any spoken voice at 8.1kHz (telephone audio quality). Runs on any modern browser, device, platform or cloud. Returns identity in 300ms. 

### Fingerprint Identification
![man's finger](https://github.com/openinfer/PrivateIdentity/blob/master/images/fingerprint%20recogni%201.png)
Authenticate, verify, identify and search an unlimited number of user’s fingerprints in real time. Absolute accuracy (IR=99.99%) with nearly zero false positives (FPIR=0.0001%). Runs on any modern browser, device, platform or cloud with any standard camera >2MB. Returns identity in 300ms. 

### Additional Features

#### Image and Video Anti-Spoofing (Liveness)
Determines if the image source is a photo or video attack. 

#### Blink Detection
Determines if a user's is blinking his or her eyes.

#### Mask Detection
Detects if a user is wearing a face mask.

#### Eyeglass Detection
Detects if a user is wearing eyeglasses.

#### Voice Liveness
Requires the user to read a random sentence. User must say the correct words. Supports eight languages.

#### Offline Authentication
Web clients automatically switch to Local Mode for face and fingerprint recognition after loss of network connectivity.

## SOLUTIONS

### IAM Integrations
![IAM Logos](https://github.com/openinfer/PrivateIdentity/blob/master/images/IAM%20Integr%201.png)
Integrates with your existing Enterprise directory using SAML 2.0 or OAuth/OIDC. 

### Identity Verification
![hand holding drivers license](https://github.com/openinfer/PrivateIdentity/blob/master/images/Identity%20Verification%201.png)
Compare photo on ID cards and passports to the user's face and verify ID. No personal data leaves the local device. 

### Account Recovery
![woman gesturing that she forgot her password](https://github.com/openinfer/PrivateIdentity/blob/master/images/Account%20Recovery%201.png)
Quickly and accurately identify locked-out accountholders to restore access.

## OPEN STANDARDS, ENCRYPTION & PRIVACY 
![Image of lego blocks ](https://github.com/openinfer/PrivateIdentity/blob/master/images/Open%20Stanards%201.png)
### IEEE 2410 Standard for Biometric Privacy 
Standard requires fully homomorphic encryption (FHE) for private identity assertion and authentication and guarantees compliant systems do not incur GDPR, CCPA, BIPA or HIPAA privacy obligations. [[link](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-STANDARD-FOR-BIOMETRIC-PRIVACY-%5BDRAFT%5D)]  

### W3C WebAuthn
Web API that enables the creation and use of strong, attested, scoped, public key-based credentials by Web applications for the purpose of strongly authenticating users.

### US ODNI ICD 503
Applies to all US government organizations, their commercial contractors, and Allied governments information systems that process, store, or communicate intelligence information.

### US DOD Standard Trusted Computer System Evaluation Criteria (TCSEC)
DoD 5200.28-STD. Mandatory for use by all DoD Components in carrying out technical security evaluation activities applicable to the processing and storage of classified and other sensitive DoD information “Orange Book.” 

### FIPS 197 Advanced Encryption Standard (AES)
NIST Special Publication 800-21,Guideline for Implementing Cryptography in the US Federal Government. 

### TLS / IPSEC / SS
Standard protocols to provide privacy and data integrity between two or more communicating computer applications. 

## OPEN STANDARDS, SECURITY ARCHITECTURE 

### ISO 27001:2013 Information Security Management Standard
International Standard includes all legal, physical and technical controls involved in the information risk management processes.

### ISO 9001:2015 Quality Management Standard
International Standard ensures software meets the needs of customers, other stakeholders and satisfies statutory and regulatory requirements.

### OAuth 2.0 / OpenID Connect / SAML 2.0
Standards that cover authorization, federation, identity management and single sign-on (SSO). 

### DoD Multiple Independent Levels of Security/Safety (MILS) Architecture
Compartmentalized approach to the design of security-critical, safety-critical, high-assurance computing systems. 

## FLEXIBLE DEPLOYMENT

### SAML 2.0

### Single Component JavaScript Application (Embedded DIV)
![Javascript](https://github.com/openinfer/PrivateIdentity/blob/master/images/JS%20Deploy%202.png)
Users quickly and intuitively enroll and authenticate using any modern device, browser or platform. The included JavaScript component deploys effortlessly with no software to install and no hardware to buy. End users enroll in four seconds without username, password, token, PIN or any private information. Users authenticate in 300ms.

***

### JavaScript APIs (Predict Enroll API)
![Image of Javascript API ](https://github.com/openinfer/PrivateIdentity/blob/master/images/JS%20API%202.png)
Easily integrates into Web and mobile apps with the included JavaScript APIs.

> Method: window.enroll(uuid, apiKey, 'face', images1, 'voice', voiceFile, 'fingerprint', images2);

> Method: window.predict(apiKey, 'face', images1, 'voice', voiceFile, 'fingerprint', images2);

***

### REST APIs (Setup) (IEEE 2410 Standard for Biometric Privacy Compliant)
![RESTful API image](https://github.com/openinfer/PrivateIdentity/blob/master/images/REST%20API2.png)
Eight RESTful APIs receive FHE payloads, return UUIDs and run all ciphertext business methods. These Web services provide resilience and scalability, enable customers to go to market faster and easily integrate and deploy with legacy and third-party services.

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









