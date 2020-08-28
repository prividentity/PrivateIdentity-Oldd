# Solution Overview
![Solution Diagram](https://github.com/openinfer/PrivateIdentity/blob/master/images/mfa%20solution%20diagram%201.png)
Private Identity’s biometric recognition algorithm, Cloud Biometric MFA, uses FHE to provide secure storage and secure computation by allowing the cloud to calculate the similarity (geometric distance) between two sets of vector data in their encrypted form. 

To accomplish this, Cloud Biometric MFA acquires biometrics using one pre-trained embedding DNN per biometric modality and a set of helper DNNs. These DNNs acquire the biometric using a biometric acquisition workflow and then discard (delete) the plaintext biometric after embedding creation. 

Cloud Biometric MFA then performs encrypted match and encrypted search using a second set of classifying DNNs. These DNNs classify an unlimited number of FHEs and return identity in constant time when deployed on load-balanced, elastic, fault-tolerant Kubernetes clusters and GCP’s Cloud AI service. Testing at 100,000 FHE payloads/second (simulating 8B authentications/day, or similar to the daily volume of Azure Active Directory) using the above configuration responded in 235ms constant time. 

# Basic Architecture

[[images/cluster_image.png]]

The [Client Applications](https://github.com/openinfer/PrivateIdentity/wiki/Client-applications) are responsible for:
* Creation of the biometric feature vector. 	
* Making an API call to [enroll](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#API-Enroll-Overview).	
* Making an API call to [predict](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#predict-overview).  
* Making an API call for [liveness](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#liveness-overview).


The [SPB Server](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#sbp-api-overview) is responsible for:
* Saving Enrollment Data during [enrollment](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#API-Enroll-Overview) process for subsequent [predict](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#predict-overview) API calls. 
* Retrieving Enrollment Data to support the [predict](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#predict-overview) API call.  
* Retrieving the probability that the [liveness](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#liveness-overview) data and result match.
