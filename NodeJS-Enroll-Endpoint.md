### Overview 

This document specifies the enrollment process for face, voice, and fingerprint modalities. This document utilizes NodeJS endpoints, which handles requests and sends them back to Python endpoints. 

### Enroll Overview

NodeJS endpoints can be called directly to execute predict, enroll, or any other provided service. In the following examples, we will be exploring the enrollment process initiated from any device, to the NodeJS server.

**Enrollment Request**

The format of this API call is: 

POST “/node/ptEnroll”

|Parameter      |            Value|
|----------|--------------| 
|api_key       |         api_key string to use this service|
| server_extract_embedding       |         Should be false for the NodeJS endpoint to structure the embeddings|
|images[]       |         Only needed to send debug images, should be base64 array containing images, and image file name for each one|
|audio | Only needed to send a debug voice file |
|modality  | "voice" or "face", 

Images should have the size of 224 for height and width. Also the request payload must be in the format of FormData. For more information: https://developer.mozilla.org/en-US/docs/Web/API/FormData

An Enroll API request example is as follows:
```
{
    "api_key": "XXXXXXXX",
    "files_photo[]": [[]]
}
```
Response

{

### Postman Example Project for Enroll

You can use the Postman application to make these API calls, such as enroll. There is a file download at the bottom of this passage that will include an example API call for the face and voice modalities. Along with that file will include images and a voice file that you can select to demo the enroll
