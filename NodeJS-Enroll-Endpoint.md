### Overview 

This document explains how to utilize the NodeJS endpoints, which can handle API requests and send them back to the Python endpoints.

### Enroll Overview

Prediction, and enrollment, or any other provided services are called through the NodeJS endpoints. In the following examples, the enrollment process is illustrated through the NodeJS server.


**Enrollment Request -**

The format of this API call is: 

POST “/node/ptEnroll”

|Parameter      |            Value|
|----------|--------------| 
|modality | The modality determines whether the face, voice, and, or fingerprint biometrics are called. |
|api_key       |         The api string is necessary to process the api requests, contact Private Identity to obtain the designated key |
|images[]       | The images parameter correlates to the face modality, images inputted here are sent to the server in a base64 array |
|audio | The audio parameter correlates to the voice modality, a voice file is inputted here |
|fingerprint[]  | The fingerprint parameter correlates to the fingerprint modality, images inputted here are sent to the server in a base64 array |

Accepted images are 224 pixels in height and width. Format the request payload as FormData. For more information visit: https://developer.mozilla.org/en-US/docs/Web/API/FormData

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

### Postman Example Project for Enroll

You can use the Postman application to make these API calls, such as enroll. There is a file download at the bottom of this passage that will include an example API call for the face and voice modalities. Along with that file will include images and a voice file that you can select to demonstrate the enrollment.

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


