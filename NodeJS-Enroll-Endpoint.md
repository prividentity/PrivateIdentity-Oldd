### Overview 

This document explains how to utilize the NodeJS endpoints, which can handle API requests and send them back to the Python endpoints.

### Enroll Overview

Prediction, and enrollment, or any other provided services are called through the NodeJS endpoints. In the following examples, the enrollment process is illustrated through the NodeJS server.


**Enrollment Request -**

The format of this API call is: 

POST “/node/ptEnroll”

|Parameter      |            Value|
|----------|--------------| 
|modality | The modality parameter determines the biometric: "face, voice, fingerprint" |
|api_key       |         The api string is necessary to process the api requests, contact Private Identity to obtain the designated key |
|images[]       | The images parameter correlates to the face modality, input the facial images here |
|audio | The audio parameter correlates to the voice modality, input the voice file here |
|fingerprint[]  | The fingerprint parameter correlates to the fingerprint modality, input the fingerprint images here |

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

The response of a Enroll request, if meeting confidence thresholds, returns a new enrollment, or an error if the user is already enrolled:
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

### Postman Example Project for Predict

The Postman application illustrates a use case for the API calls, such as predict. The example includes a file download at the bottom of this passage. Included with the sample input files are voice and face instances.  Use these files to demonstrate the prediction.

This is a step by step instructional on how to use postman to view the api calls and their responses:

1. Download Postman, and ensure it is functioning by logging into the application and viewing the user interface

[Download Postman Here](https://www.postman.com/downloads/)
![Postman User Interface](https://github.com/openinfer/PrivateIdentity/blob/master/images/Postman%20UI.png)
2. Download the package located here "". Unzip the file for Postman to import it. 

3. Import the package into Postman using the import feature and select the .json that has the API calls stored on it. 

4. The API calls are located on the left hand side of the screen, these address the different modalities and whether you are predicting or enrolling. 

5. Select the API call you want to address, and then go over to the "body" tab in the center of the screen.

6. Select the files you want to address. The package will have a test set of images, and a test voice file you can try enrolling and predicting with. 

7. Once the files are selected, you can now send the request by clicking the top right button, and the response is located at the bottom of the screen.