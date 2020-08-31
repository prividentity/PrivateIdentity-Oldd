# Demo Video 
[![Press here to play video](https://github.com/openinfer/PrivateIdentity/blob/master/images/Fingerprint%20Video%20Image.png)](https://youtu.be/C-rnRqbDS5E "JavaScript API Demonstration")

# Fingerprint Identification Documentation 

![man's finger](https://github.com/openinfer/PrivateIdentity/blob/master/images/fingerprint%20recogni%201.png)
| Accuracy | Type I Error | Type II Error | Speed |
|---|---|---|---|
| **1:1 Verification** | | |
| TMR=99.99% | FMR=0.0001% | FNMR=0.0001% | Speed=300ms |
| **1:Many Identification** | | |
| IR=96.30% | FPIR=0.0001% | FNIR=3.70% | Speed=300ms |
* **CONTACTLESS IDENTIFICATION** using optical scan (camera) or capacitive sensor 
* Supports any Webcams or phone with camera ≥720P (1MP)
* Enrolls an unlimited number of users (“unlimited gallery size”) 
* Operates in polynomial time irrespective of gallery size 
* Trained using the NIST Special Database 4 and CASIA-FingerprintV5 
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters
* Minimum Imaging Requirements: Fingerprint ≥ 320×240 pixels. Camera ≥720P.  
* MobileNetV2 Architecture, 900kB
* Accepts images using any finger 

# How to call 
* Single Component JavaScript App
* [JavaScript API](https://github.com/openinfer/PrivateIdentity/wiki/JavaScript-API)
* Encryption Engine
* [SBP Server (RESTful API)](https://github.com/openinfer/PrivateIdentity/wiki/IEEE-2410-2020-Standard-for-Biometric-Privacy-(SBP)-Server)





