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