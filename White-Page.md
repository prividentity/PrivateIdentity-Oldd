### TABLE OF CONTENTS ###
#### 1  [EXECUTIVE SUMMARY](https://github.com/openinfer/PrivateIdentity/wiki/White-Page#Executive-Summary) ####
#### 2  [INTRODUCTION](https://github.com/openinfer/PrivateIdentity/wiki/White-Page#Introduction) #####
#### 3  [BACKGROUND](https://github.com/openinfer/PrivateIdentity/wiki/White-Page#Background) ####
      3.1 TEMPLATE-BASED BIOMETRIC MATCHING
      3.2 CLOUD-BASED BIOMETRIC MATCHING
#### 4  [THE PRIVATE IDENTITY SOLUTION](https://github.com/openinfer/PrivateIdentity/wiki/White-Page#The-Private-Identity-Solution) ####
#### 5  [OPEN STANDARDS](https://github.com/openinfer/PrivateIdentity/wiki/White-Page#Open-Standards) #### 
#### 6  [ETHICAL PRINCIPLES FOR USE OF RECOGNITION TECHNOLOGY](https://github.com/openinfer/PrivateIdentity/wiki/White-Page#Ethical-Principles-for-Use-of-Recognition-Technology)  #### 
#### 7  [BIOMETRIC PRIVACY AND DATA PRIVACY](https://github.com/openinfer/PrivateIdentity/wiki/White-Page#Biometric-Privacy-and-Data-Privacy) #### 
      7.1 BIOMETRIC PRIVACY
      7.1 DATA PRIVACY
#### 8  [GDPR, CCPA AND BIPA COMPLIANCE] #### 
      8.1 EXEMPT FROM GDPR OBLIGATIONS
      8.2 EXEMPT FROM CCPA OBLIGATIONS
      8.3 EXEMPT FROM BIPA OBLIGATIONs
#### 9  [BIOMETRIC ACQUISITION] ####
      9.1 WEB CLIENT BIOMETRIC ACQUISITION 
      9.1.1 FACE, FACE+MASK & FINGERPRINT GEOMETRY DETECTION DNNs
      9.1.2 FACE & FINGERPRINT VALIDATION DNNs
      9.1.3 FACE+MASK ON/OFF DETECTION DNN
      9.1.4 EYEGLASSES ON/OFF DETECTION DNN
      9.1.5 EYE GEOMETRY DETECT DNN
      9.1.6 EYES OPEN/CLOSED DETECTION DNN (Spoofing Prevention)
      9.1.7 FACIAL AND FINGERPRINT DATA AUGMENTATION
      9.1.8 FACE, FACE+MASK, AND FINGERPRINT EMBEDDING DNNs
      9.1.9 VOICE INPUT SEGMENTATION
      9.1.10 VOICE PULSE CODE MODULATION (PCM) TRANSFORMATION
      9.1.11 VOICE FAST FOURIER TRANSFORMATION (FFT)
      9.1.12 VOICE EMBEDDING DNN
      9.2 OFFLINE WEB CLIENT BIOMETRIC ACQUISITION (LOCAL MODE)
      9.3 ENCRYPTION ENGINE™
      9.4 PRIVATE IDENTITY SEARCH™
#### 10  [BIOMETRIC MATCHING ALGORITHMS] #### 
      10.1 FACIAL RECOGNITION ALGORITHM
      10.2 FACE+MASK RECOGNITION ALGORITHM
      10.3 FINGERPRINT RECOGNITION ALGORITHM
      10.4 VOICE / SPEAKER IDENTIFICATION ALGORITHM
#### 11  [ENTERPRISE INTEGRATIONS]	#### 
#### 12  [KNOWN PROCESSING ISSUES]	####
#### 13  [FORMAL PERFORMANCE TESTING OF ALGORITHM]	####

</br>

#### Executive Summary ####

Mike Pollard and Scott Streit co-founded Private Identity® in Washington, D.C. in 2017. Private Identity solved fully homomorphic encryption (FHE) in 2018 and USPTO granted patents in 2019 and 2020.  The company collaborated with Google’s TensorFlow® team in 2019 to bring FHE to the edge.

Private Identity’s FHE algorithm is a 1-way hash (embedding, or vector encryption) that irreversibly encrypts data while enabling match and search operations on the encrypted dataset. This mitigates the regulatory and legal privacy risk of biometric data by eliminating all requirements to store, transmit or use a plaintext biometric or template.
 
Indeed, the Private Identity solution preserves privacy so effectively that it allows businesses and organizations to use biometric identification without being subject to GDPR, CCPA or BIPA obligations. FHE-transformed data is not “Personal Data” under GDPR or CCPA and is not “Biometric Information” under the BIPA. 
Today, Private Identity provides contactless face, face with mask, voice and fingerprint recognition algorithms with unmatched accuracy, speed and privacy using an elastic AI/ML/FHE solution. The company’s FHE algorithm reduces false positive identification rates to nearly zero and reduces payload size and network traffic to the cloud by 99.5%.
   
Users interact with the Private Identity solution using a massively scalable, convenient, browser-based experience powered by Google Tensorflow® that operates on more than 90% of all browsers, platforms and devices. The Web client does not require on-device training, expensive hardware, GPUs or specialized cameras. 
The Private Identity recognition algorithm uses two Deep Neural Networks (DNNs) per biometric modality and a set of helper DNNs for biometric acquisition. The algorithm acquires biometrics and FHE transforms using the following solutions: <br>
       1. Private Identity MFA™ provides a massively scalable Web browser client for user identification, authentication and Account Recovery; <br> 
       2. Encryption Engine™ provides a cross-platform, elastic high-throughput AI/ML/FHE transformation service that runs anywhere; <br>
       3. Private Identity Search™ provides a polynomial, sub-second massively scalable, elastic high-throughput AI/ML/FHE identification service that runs anywhere.

Private Identity provides pre-configured SaaS Enterprise Integrations for Google Identity®, PING Identity®, Okta® Factor Authentication, SAML 2.0, OAuth/OIDC, WebAuthn, Azure® Active Directory and AWS® IAM.  PaaS Integrations are hosted on GCP and AWS.

#### Introduction ####
</br>

#### Background ####
</br>

#### The Private Identity Solution ####
</br>

#### Open Standards ####
</br>

#### Ethical Principles for use of Recognition Technology ####
</br>

#### Biometric Privacy and Data Privacy ####
</br>

#### GDPR, CCPA and BIPA Compliance ####
</br>

#### Biometric Acquisition ####
</br>

#### Biometric Matching Algorithms ####
</br>

#### Enterprise Integrations ####
</br>

#### Known Processing Issues ####
</br>

#### Formal Performance Testing of Algorithm ####
</br>
