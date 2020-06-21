## Customer Integrations ##

### DIV/HTML ###

* Built in React (pluggable)
* Embed as a DIV
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/DIV-HTML)

### PaaS (Web Tier) ###

* Docker Image
* Runs elastic, load balanced, fault tolerant K8s
* Connects to a Server Side Component managed by Private Identity
* Runs on any cloud (AWS, GCP, Azure)
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/PaaS-Web-Application)

### PaaS (Entire Tier) ###

* Docker Images
* Runs elastic, load balanced, fault tolerant K8s
* Includes Server Side Component
* Runs on any cloud (AWS, GCP, Azure)
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/cluster-setup) 

### SaaS (Open) ###

* Entirely managed and run on AWS by Private Identity
* API Key access
* Fully elastic, load balanced, fault tolerant

### SaaS (Dedicated for Customer) ###

* Entire K8s cluster dedicated to Customer
* Entirely managed and run on AWS by Private Identity
* API Key access
* Fully elastic, load balanced, fault tolerant

### RESTful API ###

* Receives fully homomorphic encryption (FHE) payload from client device
* Returns UUIDs
* Runs all ciphertext and plaintext business methods
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/Predict-Enroll-library)

### Encryption Engine ###

* Cluster for biometric ingestion
* Elastic, load balanced, fault tolerant K8s, autoscale to 1000s of nodes
* Javascript API and RESTful API
* [Cluster Setup](https://github.com/openinfer/PrivateIdentity/wiki/Client-Cluster-setup)

### W3C/FIDO2 WebAuthn (polymorphic interface) ###

* Authenticator enrollment -> how enrolling on /demo/ shows your enroll data in /webauthn 
* Authenticator authentication -> how prediction on /demo/ shows your enroll data in /webauthn

### Photo ID Verification ###

* DIV/HTML -> https://private.id/demo/?apiKey=1962&passport=true&version=0.9.
* Javascript API -> The JS Library?
* Server Side RESTful API -> getPhoneNumberDetails, verifyEnrollConfirmation, googleOCR, getDistanceforEmbeddings, getVerifyDistance, getEnrollLevel, verifyEnroll, predict
* [Setup](https://github.com/openinfer/PrivateIdentity/wiki/Verified-Enroll)