### Overview 


In this document, prediction process will be documented for each modality. Namely, face, voice, liveness, and fingerprint modalities. This document utilizes NodeJS endpoints, which handles requests and sends them back to Python endpoints. 

### Predict Overview

NodeJS endpoints can be called directly to execute predict, enroll, or any other provided service. In the following examples, we will be exploring prediction process initiated from any device, to the NodeJS server.


**Face Prediction Request - Base64 images case**

The format of this API call is: 

POST “/node/generateEmbeddingsAndPredict”

|Parameter      |            Value|
|----------|--------------| 
|api_key       |         api_key string to use this service|
|images[]       |         base64 array containing images, and image file name for each one|

Prediction images should have the size of 224 for height and width.Also the request payload must be in the format of FormData. For more information: https://developer.mozilla.org/en-US/docs/Web/API/FormData

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

POST “/node/predict”

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