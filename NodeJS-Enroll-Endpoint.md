### Overview 

This document explains how to utilize the NodeJS endpoints, which can handle API requests and send them back to the Python endpoints.

### Enroll Overview

The NodeJS endpoint provides an interface for prediction, and enrollment, or any other provided service. The following example illustrates the enrollment process through the NodeJS server.


**Enrollment Request -**

The format of this API call is: 

POST “/node/ptEnroll”

|Parameter      |            Value|
|----------|--------------| 
|modality | The modality parameter determines the biometric: "face, voice, fingerprint" |
|api_key       |         The api string is necessary to process the api requests, contact Private Identity to obtain the designated key |
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

### Postman Example Project for Enroll

The Postman application illustrates a use case for the API calls, such as enroll. The example includes a file download at the bottom of this passage. The file download includes voice and face instances and a .json file that makes the API calls.  Use these files to demonstrate the prediction.

This is a step by step instructional on how to use postman to view the api calls and their responses:

1. Download Postman, and ensure it is functioning by logging into the application and viewing the user interface

[Download Postman Here](https://www.postman.com/downloads/)
![Postman User Interface](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman%20UI.png)
2. Download the package located here "". Unzip the file for Postman to import it. 

3. Import the package into Postman using the import feature and select the .json that has the API calls stored on it. 

4. The left hand side of the screen contains the API calls necessary to predict and enroll a variety of modalities. 

5. Select the API call you want to address, and then go over to the "body" tab in the center of the screen.

6. Select the files you want to address. The package will have a test set of images, and a test voice file you can try enrolling and predicting with. 

7. Once the files are selected, you can now send the request by clicking the top right button, and the response is located at the bottom of the screen.