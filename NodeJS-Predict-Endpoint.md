### Overview 

This document explains how to utilize the NodeJS endpoints, which can handle API requests and send them back to the Python endpoints.

### Predict Overview

The NodeJS endpoint provides a interface for Prediction, and enrollment, or any other provided service. The following example, illustrates the prediction process through the NodeJS server.


**Face And/Or Prediction Request -**

The format of this API call is: 

POST “/node/ptPredict”

|Parameter      |            Value|
|----------|--------------| 
|modality | The modality determines whether the face, voice, and, or fingerprint biometrics are called. |
|api_key       |         The api string is necessary to process the api requests, contact Private Identity to obtain the designated key |
|images[]       | The images parameter correlates to the face modality, images inputted here are sent to the server in a base64 array |
|audio | The audio parameter correlates to the voice modality, a voice file is inputted here |
|fingerprint[]  | The fingerprint parameter correlates to the fingerprint modality, images inputted here are sent to the server in a base64 array |

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

The response of a Predict request, if meeting confidence thresholds, returns PII data in the following format:
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

The Postman application illustrates a use case for the API calls, such as predict. The example includes a =file download at the bottom of this passage in example API call for the face and voice modalities. Included with the sample input files are voice and face instances.  Use these files to demonstrate the prediction.

This is a step by step instructional on how to use postman to view the api calls and their responses:

1. Download Postman, and ensure it is functioning by logging into the application and viewing the user interface

[Download Postman Here](https://www.postman.com/downloads/)
![Postman User Interface](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman%20UI.png)
2. Download the package located here "". You will have to unzip the file in order for Postman to access it. 

3. Import the package into Postman using the import feature and selecting the .json that has the API calls stored on it. 

4. On the left hand side of the screen you will now be able to view the varying API calls, these address the different modalities and whether you are predicting or enrolling. 

5. Select the API call you want to address, and then go over to the "body" tab in the center of the screen.

6. Select the files you want to address. The package that was downloaded will have a test set of images, and a test voice file you can try enrolling and predicting with. 

7. Once the files were selected, you can now send the request by clicking the top right button, and then the response should show up in the center bottom of the screen.


