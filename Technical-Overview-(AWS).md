# Solution Overview
![Solution Diagram](https://github.com/openinfer/PrivateIdentity/blob/master/images/mfa%20solution%20diagram%201.png)
Private Identity’s biometric recognition algorithm, Cloud Biometric MFA, uses FHE to provide secure storage and secure computation by allowing the cloud to calculate the similarity (geometric distance) between two sets of vector data in their encrypted form. 

To accomplish this, Cloud Biometric MFA acquires biometrics using one pre-trained embedding DNN per biometric modality and a set of helper DNNs. These DNNs acquire the biometric using a biometric acquisition workflow and then discard (delete) the plaintext biometric after embedding creation. 

Cloud Biometric MFA then performs encrypted match and encrypted search using a second set of classifying DNNs. These DNNs classify an unlimited number of FHEs and return identity in constant time when deployed on load-balanced, elastic, fault-tolerant Kubernetes clusters and GCP’s Cloud AI service. Testing at 100,000 FHE payloads/second (simulating 8B authentications/day, or similar to the daily volume of Azure Active Directory) using the above configuration responded in 235ms constant time. 

# Basic Architecture
[[images/cluster_image.png]]

## Client Applications
* <b>Cloud Biometric MFA</b> - a [single-component Javascript application](https://github.com/openinfer/PrivateIdentity/wiki/Client-Applications#web-applications)
* <b>Cloud Biometric API</b> - accepts plaintext images, video or audio ([Javascript APIs](https://github.com/openinfer/PrivateIdentity/wiki/JavaScript-API) and [Encryption Engine](https://github.com/openinfer/PrivateIdentity/wiki/pb-utils)) 
* <b>Cloud Biometric Encryption Engine</b> - elastic, high-throughput Kubernetes [FHE transformation service](https://github.com/openinfer/PrivateIdentity/wiki/pb-utils) that deploys anywhere
* <b>Cloud Biometric Search</b> - elastic, high-throughput Kubernetes identification service that runs anywhere 
* Mobile pre-trained embedding DNNs powered by TensorFlow FHE transform biometric data 
* Less capable devices operate by offloading processing to Node.js  
* Creates FHE payloads using biometric workflow ([Geometry DNN](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-and-face-wmask-geometry-detection-dnn) --> [Validation DNN](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#4-classes-good-blurry-eyeglasses-facemask-validation-dnn) --> [Embedding DNN](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-facemask-and-fingerprint-embedding-dnns)) 
* Makes API call to [enroll](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#API-Enroll-Overview).	
* Makes API call to [predict](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#predict-overview).  
* Makes API call for [liveness](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#liveness-overview).
* [Link](https://github.com/openinfer/PrivateIdentity/wiki/Client-Applications) to documentation

The [SPB Server](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-2020-Standard-for-Biometric-Privacy-(SBP)-Server) is responsible for:
* Saving Enrollment Data during [enrollment](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#API-Enroll-Overview) process for subsequent [predict](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#predict-overview) API calls. 
* Retrieving Enrollment Data to support the [predict](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#predict-overview) API call.  
* Retrieving the probability that the [liveness](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#liveness-overview) data and result match.

# BIOMETRIC ACQUISITION 
* Acquires and ingests variety of synchronous and asynchronous biometric inputs
* Accepts images, videos and audio from phones and Webcams
* Does not store, transmit or use biometric data
* Decoupled from back-end cluster for privacy 
* Provides exception processing 

Private Identity provides a single-component Javascript Web client and two elastic services to support biometric acquisition and high-throughput FHE transformation at the edge. This enables Private Identity to accept a variety of synchronous and asynchronous biometric inputs (i.e. phones, Webcams, legacy devices and applications, and plaintext images, video, audio and input from third-party biometric acquisition systems) without any requirement to store, transmit or use plaintext biometrics.  

The Cloud Biometric MFA single-component Javascript Web client provides users with a massively scalable, convenient, browser-based enrollment, identity, MFA and account recovery experience that operates on more than 90% of all browsers, platforms and devices (every device that runs TensorFlow). 

The Cloud Biometric API accepts plaintext or FHE images, video or audio using Javascript APIs or RESTful APIs. 
The Cloud Biometric Encryption Engine service provides high-throughput, high-demand identification tasks with unlimited asynchronous throughput for face, face with mask, fingerprint and voice enrollment and identification using elastic, load-balanced, fault-tolerant Kubernetes clusters. 

Similarly, the Cloud Biometric Search service provides high-throughput, high-demand identification tasks with unlimited asynchronous face, face with mask, fingerprint and voice identification using elastic, load-balanced, fault-tolerant Kubernetes clusters. 

The Cloud Biometric MFA Web client, API, Encryption Engine and Search use an ensemble of pre-trained TensorFlow™ models to detect and recognize faces (50ms), fingerprints (50ms) and voices (100ms) with high accuracy.


## 