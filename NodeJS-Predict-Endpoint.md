### Overview 

This document explains how to utilize the NodeJS endpoints, which can handle API requests and send them back to the Python endpoints.

### Predict Overview

NodeJS endpoints can be called directly to execute a prediction, enrollment, or any other provided service. In the following examples, we will be exploring the prediction process initiated from any device, through the NodeJS server.


**Face And/Or Prediction Request -**

The format of this API call is: 

POST “/node/ptPredict”

|Parameter      |            Value|
|----------|--------------| 
|modality | the modality can be selected to determine whether "face" and/or "voice" is being called
|api_key       |         an api string will be necessary while accessing the api requests|
|images[]       |         A base64 array containing images can be filled to utilize the face modality|
|audio | array containing voice files |

Prediction images should be 224 pixels in height and width. The request payload must be in the format of FormData. For more information: https://developer.mozilla.org/en-US/docs/Web/API/FormData

A Predict API request example is as follows:
```
{
    "api_key": "XXXXXXXX",
    "images[]": "base64 image",
    "images[]": "base64 image",
    "images[]": "base64 image", 
    "images[]": "base64 image",
    ...
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

**Face Prediction Request - Embeddings generated case**


The format of this API call is: 

POST “/node/ptPredict”

|Parameter      |            Value|
|----------|--------------| 
|api_key       |         api_key string to use this service|
| server_extract_embedding       |         Should be false for the NodeJS endpoint to structure the embeddings|
|files_photo[]       |         Embeddings JSON stringified array|
|images[]       |         Only needed to send debug images, should be base64 array containing images, and image file name for each one|

Prediction images should have the size of 224 for height and width.Also the request payload must be in the format of FormData. For more information: https://developer.mozilla.org/en-US/docs/Web/API/FormData

A Predict API request example is as follows:
```
{
    "api_key": "XXXXXXXX",
    "files_photo[]": [[]]
}
```
### Postman Example Project for Predict

You can use the Postman application to make these API calls, such as predict. There is a file download at the bottom of this passage that will include an example API call for the face and voice modalities. Along with that file will include images and a voice file that you can select to demo the enroll.

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


