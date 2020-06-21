## Overview 

This document explains how to utilize the NodeJS endpoints, which can handle API requests and send them back to the Python endpoints.

## Predict Overview
<br/>

The NodeJS endpoint provides an interface for prediction, and enrollment, or any other provided service. The following example illustrates the prediction process through the NodeJS server.


**Face And/Or Prediction Request -**

The format of this API call is: 

POST “/node/ptPredict”

|Parameter      |            Value|
|----------|--------------| 
|modality | The modality parameter determines the biometric: "face, voice, fingerprint" |
|api_key       |         The api string is necessary to process the api requests. Contact Private Identity to obtain the designated key |
|images[]       | The images parameter is an array of facial image files |
|audio | The audio parameter is a voice file |
|fingerprint[]  | The fingerprint is an array of fingerprint image files |

Accepted images are 224 pixels in height and width. Format the request payload as FormData. For more information visit: https://developer.mozilla.org/en-US/docs/Web/API/FormData

A Predict API request example is as follows:
```
{
    "api_key": "XXXXXXXX",
    "modality": "voice, face, fingerprint"
    "images[]": "base64 image",
    "images[]": "base64 image",
    "images[]": "base64 image", 
    "images[]": "base64 image",
    ...
    "audio": "audio file",
    "fingerprint[]": "base64 image",
    "fingerprint[]": "base64 image",
    "fingerprint[]": "base64 image", 
    "fingerprint[]": "base64 image",

}
```

**Response**

The response of a Predict request, if successful, returns enrollment data in the following format:
```
{
    "enrollment data": {
	"id": "1008023",
    },
    "message": "OK",
    "status": 0,
    "subject_id": 4,
}
```

## Enroll Overview
<br/>

The NodeJS endpoint provides an interface for prediction, and enrollment, or any other provided service. The following example illustrates the enrollment process through the NodeJS server.


**Enrollment Request -**

The format of this API call is: 

POST “/node/ptEnroll”

|Parameter      |            Value|
|----------|--------------| 
|modality | The modality parameter determines the biometric: "face, voice, fingerprint" |
|api_key       |         The api string is necessary to process the api requests. Contact Private Identity to obtain the designated key |
|images[]       | The images parameter is an array of facial image files |
|audio | The audio parameter is a voice file |
|fingerprint[]  | The fingerprint parameter is an array of fingerprint image files |

Images that are accepted are 224 pixels in height and width. Format the request payload as FormData. For more information visit: https://developer.mozilla.org/en-US/docs/Web/API/FormData

An enroll API request example is as follows:
```
{
    "api_key": "XXXXXXXX",
    "modality": "voice, face, fingerprint"
    "images[]": "base64 image",
    "images[]": "base64 image",
    "images[]": "base64 image", 
    "images[]": "base64 image",
    ...
    "audio": "audio file",
    "fingerprint[]": "base64 image",
    "fingerprint[]": "base64 image",
    "fingerprint[]": "base64 image", 
    "fingerprint[]": "base64 image",

}
```

**Response**

The response of an Enroll request, if successful, returns a new enrollment, or an error if the user is already enrolled:
```
{
     {
     "status: 0"
     "UUID:" "XXXXXX"
     "subject id:" "XXXXX"
     }
  or {
     "status: -1"
     "subject id:"User found in registry"
     "subject id:" "XXXXX"
        
}
```

## Postman Example Project
<br/>

The Postman application illustrates a use case for the API calls, such as predict. The example includes a file download at the bottom of the passage. The file download includes voice and face instances and a .json file that makes the API calls.  Use these files to demonstrate the API calls.

This is a step by step instructional on how to use postman to view the API calls and their responses:

1. Download Postman, and ensure it is functional by logging into the application and viewing the user interface

[Download Postman Here](https://www.postman.com/downloads/)
![Postman User Interface](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_1.png)
2. Download the package located here [Postman Package](https://github.com/openinfer/PrivateIdentity/blob/master/JSEndpoint/EnrollMaterialandCalls.zip). Uncompress the file for Postman to import it. 

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman2.png)

3. Import the package into Postman using the import feature and select the .json that has the API calls.
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_2.png)
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_4.png)
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_5.png)
4. The left hand side of the screen contains the API calls necessary to predict and enroll a variety of modalities.
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_6.png)
5. Select the relevant API call and then go over to the "body" tab in the center of the screen.
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_7.png)
6. Select the files you want to address. Use the files with a .jpg suffix for face or a .wav suffix for voice.  
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_8.png)
7. After file selection, process the request by clicking the "send" button.
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman_9.png)
8. The request response displays on the bottom of the screen.


