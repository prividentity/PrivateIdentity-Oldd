
## `Embedded DIV` Implementation Guide (Video)
![missing video plugs in here](https://github.com/openinfer/PrivateIdentity/blob/master/images/Single%20Compoent%20App%20PLAY%201.png)

## `Getting Started`

### STEP 1.  Obtain an API Key from the AWS Marketplace
The AWS Marketplace listing is currently private.  Please send your AWS account number to api@private.id to request access to the listing.

### STEP 2. Setup the Embedded DIV and Run Demo 
```
<!doctype html>
<html lang="en" style="height: 100%;">

<head>
  <meta charset="UTF-8">
</head>

<body style="height: 100%;">
  <iframe width="100%" height="100%" src="https://private.id/demo/?apiKey=####"></iframe>
</body>

</html>
```
### STEP 3.  Enroll and Predict Using URL Parameters Only
Enroll the user using the URL parameter example below. 
> `https://private.id/mfa/index.htm?apiKey=XXXX&action=enroll` 

Predict the user using the URL parameter example below. 
> `https://private.id/mfa/index.htm?apiKey=XXXX&action=predict` 

### STEP 4. Store UUID From the Previous Calls
The two calls above return the UUID as an HTTP response. The UUID is in JSON format as shown in the example below. 

```
{Private Response: {…}, facemask: {…}, message: "OK", status: 0}
PR:
enroll_level: "1"
modality: "facemask"
**uuid: "f669af15b6af1f23665e"**
__proto__: Object
facemask: {additional_info: "frobenius_pred_subject_id", status: 0, top_k_rank_frobenius: Array(1)}
message: "OK"
status: 0
__proto__: Object
```

### STEP 5.  Finished!
Use the URLs from Step 3 and the URL parameters described below in your application.  

## Control All Functions Using URL Parameters 
URL parameters are used to control all functions of the Web client. The Web client conforms to the [W3C Usage Patterns For Client-Side URL parameters](https://www.w3.org/2001/tag/doc/hash-in-url-20080211.html).  Common URL parameters are listed below.

An URL parameter example is as follows:  
> https://private.id/demo/?apiKey=1962&debug=true

| **Common URL Parameters*** | Possible values | Default Value | Function | 
|-----|----|---|-----|
|action|predict / enroll|No default|Prediction only Default:face can be combined with voice: Enroll with face by default, can be combined with voice|
|antiVideoSpoof|true / false|false|Video spoofing|
|apiKey| Value of apiKey|No default|Set apiKey for requests to execute|
|faceMask|true / false|true|Use face mask embedding model.|
|face| true / false|true|Enroll & predict with face|
|fingerPrint|true / false|false|Prediction using Fingerprint (In Progress)|
|voice|true / false|false|Enroll & Predict with voice|
|glassCheck|true / false|false|Turn glasses check on predict/enroll to on/off|
|idp|okta / ping / azure/ gsuite|null|Set SAML destination|
|antiVideoSpoof|true / false|false|Check the webcam capture is a spoofed one or not.

* The full list of Web Client URL parameters is found [here.](https://github.com/openinfer/PrivateIdentity/wiki/Client-URL-Parameters)
* The full list of Administrative URL parameters is found [here.](https://github.com/openinfer/PrivateIdentity/wiki/Admin-URL-Parameters)

### Eyeglasses Check

During enrollment or prediction, you can adjust the eye glasses check to be on or off. For each mode, there are pros and cons. The following table explains it:

| Mode | Pros | Cons |
| --- | --- | --- |
| true | Better enrollment images  | Slightly lower performance |
| false | Slightly reduced accuracy | Faster performance and more convenient for user |

Example:
> https://private.id/demo/?apiKey=1962&glassCheck=on
 
### Video Spoof Check

During enrollment, video spoof check can be turned on/off with the URL parameter antiVideoSpoof. The default value for it is `true`. It can be disabled by setting the value to `false`. 

Example: 
> `https://private.id/demo/index.htm?apiKey=XXXX&antiVideoSpoof=false`

### Require Eyes Open/Closed (Blinking)

Eyes blink on average every 0.2 seconds. To ensure that the subject’s eyes are blinking, turn the `faceLiveness` URL parameter on.  If no blinking is detected, the prediction or enrollment will not proceed. 

The default value for this parameter is false. To turn it on, follow the example below.

> `https://private.id/mfa/index.htm?apiKey=XXXX&faceLiveness=true&action=enroll`

### Enrollment using Multiple Biometrics 
Enroll subjects with multiple biometrics (face, voice, faceMask, fingerprint) by combining URL parameters. Each biometric modality can be used separately, or mixed with one or more parameters. 

The only exception to this is face and faceMask. At the most, one is allowed. 

Example to use voice modality:  
> `https://private.id/mfa/index.htm?apiKey=XXXX&action=enroll&voice=true`

Example to use face modality:  
> `https://private.id/mfa/index.htm?apiKey=XXXX&action=enroll&face=true`

Example to use faceMask modality:  
> `https://private.id/mfa/index.htm?apiKey=XXXX&action=enroll&faceMask=true`

Example to use fingerprint modality: 
> `https://private.id/mfa/index.htm?apiKey=XXXX&action=enroll&fingerprint=true`

Example to use all modalities:  
> `https://private.id/mfa/index.htm?apiKey=XXXX&action=enroll&fingerprint=true&faceMask=true&voice=true`

## Updating Existing Enrollments:
A new UUID is created for every enrolled subject. This value is used to add a new biometric modality to an existing enrollment without creating a new UUID. For example, if a user enrolled with `voice` and wants to add `faceMask` modalities, the URL will be: 

> `https://private.id/mfa/index.htm?apiKey=XXXX&action=enroll&uuid=XXXX&faceMask=true`

### Secure the API Key in the JSON payload (Optional)
The API key can be passed as a URL parameter (as shown in Step 2) or as part of the JSON payload. The server will not execute the desired process unless a valid apiKey value is available in the URL parameter or request header.

Below is an example of the `apiKey` sent as a HTTP parameter. 
> `https://private.id/a/index.htm?apiKey=XXXX` 

**To secure the apiKey using the HTTPS header,** send the `apiKey` to the server using HTTPS headers. The field is named `x-api-key`. The API key is accessed through the header field and can be assigned with application software or a tool (e.g. PostMan). The value is a string. 

### Minimum Hardware, Browser and Platform Requirements
| Environment | Minimum Version |
| -- | -- |
| Google Chrome | 73 |
| Google Chrome for Android | 73 |
| Microsoft Edge | 80 |
| FireFox | 60 |
| Safari | 12 |
| iOS Safari | 13 |
| Microsoft Internet Explorer | Not supported |
| Microsoft Windows | 7 | 
| Ubuntu | 16.04 | 
| MacOS | 10.12.6 (Sierra) |
| Raspbian | 9.0 | 
| Python | 3.5 - 3.8 |

| Sensors | Minimum Specs |
| -- | -- |
| Camera for Facial Recognition | ≥256kB |
| Camera for Fingerprint Identification | ≥720P (1MP) |
| Microphone for Voice Identification | ≥8.1kHz (telephone quality) |

### Enrollment Consent Forms

The subject is usually asked for his/her consent prior to enrollment. 

The first form looks like this: 

<img src="https://github.com/openinfer/PrivateIdentity/blob/master/images/first-enroll-form.png" alt="Your image title" width="450"/>

If the subject clicks on “continue” button, the next consent form appears as follows:

<img src="https://github.com/openinfer/PrivateIdentity/blob/master/images/second-enroll-form.png" alt="Your image title" width="450"/>

These forms may be customized for your organization. 

*** 

# How It Works 
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Single%20Compoent%20App%202.png)
1. Acquire user biometrics 
1. Create FHE payloads 
1. Send payload to server using SBP RESTful API
1. Return response (UUID)

The embedded DIV authenticates an unlimited number of users by transmitting FHE payloads to a server, private or public cloud. Identity returns in 300ms. In “off-line mode,” where a network is not present, the client authenticates a maximum of 50 offline users on a modern phone and a few thousand offline users on a laptop. Offline authentication is limited by system resources and returns identity in <10ms. 

Multiple biometric modalities (face, voice, fingerprint) allow additional biometric authentication mechanisms for step-up authentication. This provides system administrators with the flexibility of requiring a single convenient biometric authentication modality for low-risk applications or more rigorous authentication as needed. The fingerprint biometric disambiguates difficult cases such as identical twins.

The Web client provides automated visual guidance during prediction and enrollment to assist unsupervised and supervised users in acquiring quality biometrics. The system creates an enrollment package 50 FHE payloads to bind the trusted user identifier (a UUID generated by the system) with the authorized user’s private biometric identity. After enrollment, the Cloud Biometric MFA system may store the enrollment package in the secure element of the user’s device to support offline authentication and/or on a server, within the Cloud Biometric MFA system.

The Cloud Biometric MFA system’s prediction capability uses a payload of 3 FHE vectors and returns the UUID or (-1) if not found.

## Architecture Discussion
![Logical Boundaries Diagram for Single Component Web app](https://github.com/openinfer/PrivateIdentity/blob/master/images/Single%20Compoent%20App%20Logic%20Boundaries%201.png)
> Single Component Web app - Logical Block Diagram

The embedded DIV uses fully homomorphic encryption (FHE) methods to ensure privacy, security and confidentiality of the prediction and enrollment packages. To accomplish this, the embedded DIV acquires biometrics using a set of helper DNNs and one pre-trained mobile embedding DNN per biometric modality. These DNNs acquire the biometric using a biometric acquisition workflow and then discard (delete) the plaintext biometric after embedding creation.

The biometric acquisition workflow is implemented as follows. 
* [**Biometric Capture.**](https://github.com/openinfer/PrivateIdentity/wiki/Client-Applications#Web-applications)  The sensor (e.g. phone camera, Webcam, microphone, etc.) acquires a sample of the user’s biometric. 
* [**Geometry DNN**](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-and-face-wmask-geometry-detection-dnn) - The Geometry DNN determines the (x,y) coordinates of the biometric. 
* [**Validation DNN**](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#4-classes-good-blurry-eyeglasses-facemask-validation-dnn) - Validation DNN provides real-time user guidance for acquiring quality biometrics and validates the biometric sample and determines liveness (anti-spoofing).  
* [**Embedding DNN**](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Ingestion-and-Helper-DNNs#face-facemask-and-fingerprint-embedding-dnns) – The Embedding DNN transforms the validated biometric sample into an encrypted payload (“FHE payload”). 
* **Delete Biometric** – The system then discards (deletes) the original biometric data to eliminate risk of loss and prevent any possible future linkage. 

Discuss the workflow that is followed for enrollment.
1. Capture user's biometrics using built-in sensors, Webcams, USB microphones, etc. Captures 10 for enrollment and 3 for prediction.
1. Validate Biometrics. If any of the images are not suitable for training, a message is returned and the image is removed. The user must add more images until at least 10 images meeting the minimum quality standards have been provided.
1. FHE Transform Biometrics
1. Delete Biometrics
1. Server validates FHE enrollment package
1.  Server attempts to match enrollment to an existing user. If existing user is matched, server returns UUID without enrolling subject
1. If no match is found, the system extracts the features from the images and stores the features in the system.


