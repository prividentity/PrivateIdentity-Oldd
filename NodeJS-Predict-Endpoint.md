### Overview 

This document explains how to utilize the NodeJS endpoints, which can handle API requests and send them back to the Python endpoints.

### Predict Overview

The NodeJS endpoint provides a interface for Prediction, and enrollment, or any other provided service. The following example, illustrates the prediction process through the NodeJS server.


**Face And/Or Prediction Request -**

The format of this API call is: 

POST “/node/ptPredict”

|Parameter      |            Value|
|----------|--------------| 
|modality | The modality parameter determines the biometric: "face, voice, fingerprint" |
|api_key       |         The api string is necessary to process the api requests. Contact Private Identity to obtain the designated key |
|images[]       | The images parameter is an array of facial image files |
|audio | The audio parameter correlates to the voice modality, input the voice file here |
|fingerprint[]  | The fingerprint parameter correlates to the fingerprint modality, input the fingerprint images here |

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

The response of a Predict request, if successful, returns PII data in the following format:
```
{
    "PII": {
        "name": "Nguyen",
	"id": "1008023",
        ...
        "address": "23 Scott Street"
    },
    "message": "OK",
    "status": 0,
    "subject_id": 4,
}
```

### Postman Example Project for Predict

The Postman application illustrates a use case for the API calls, such as predict. The example includes a file download at the bottom of this passage. Included with the sample input files are voice and face instances.  Use these files to demonstrate the prediction.

This is a step by step instructional on how to use postman to view the api calls and their responses:

1. Download Postman, and ensure it is functioning by logging into the application and viewing the user interface

[Download Postman Here](https://www.postman.com/downloads/)
![Postman User Interface](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman%20UI.png)
2. Download the package located here "". Unzip the file for Postman to import it. 

3. Import the package into Postman using the import feature and select the .json that has the API calls.

4. The left hand side of the screen contains the API calls necessary to predict and enroll a variety of modaliies.

5. Select the relevant API call and then go over to the "body" tab in the center of the screen.

6. Select the files you want to address. Use the files with a .jpg suffix for face or a .wav suffix for voice.  

7. After file selection, process the request by clicking the "send" button.


