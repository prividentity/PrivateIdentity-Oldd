## BOPS API Overview

Format: RESTful JSON format

Test Request URL: https://server1.privatebiometrics.com:5443/trueid/hello

Request Method: GET

Request Example:
curl https://server1.privatebiometrics.com:5443/trueid/hello

### Enroll endpoint


**Overview**

To enroll a user, we take as input  the enrollment Data which is a set of tag/value pairs. Using a Global UUID a new identity is created in the persistent engine  corresponding to the enrollment data provided.


**Request**

Request URL: https://server1.privatebiometrics.com:5443/trueid/enroll

Request Method: POST

Request Payload Example:

```
{
    "enrollment data": {
	"id": "1008023",
    },
    "images": [
	["image_1", "base64_image_1"],
	["image_2", "base64_image_2"],
	...
	["image_n", "base64_image_n"]
    ],
    “Voices”:[
        [ “voice_name_1”, “base64_voice_1],
        [ “voice_name_2”, “base64_voice_2],
        ...
    ]
}
```


**Response**

The response of an Enroll request returns 0 as  Success given data validation and database storage success.


### Predict endpoint


**Overview**

Once enrolled a caller can call the Predict API to perform an attempt to use the tranied system to identify the individual subject based upon images provided in the call.


**Request**

Request URL: https://server1.privatebiometrics.com:5443/trueid/predict

Request Method: POST

Request Payload Example:

```
{
    "images": [
	["image_1", "base64_image_1"],
	["image_2", "base64_image_2"],
	...
	["image_n", "base64_image_n"]
    ],  
    “Voices”:[
        [“voice_name_1”, “base64_voice_1],
        [“voice_name_2”, “base64_voice_2],
        ...
    ]
}
```


**Response**

The response of a Predict request, if meeting confidence thresholds, returns enrollment data in the following format:

```
{
    "enrollment data": {
	"id": "1008023",
    },
    "message": "OK",
    "status": 0,
    "subject_id": 4,
    "undetected_images": [
        "321519721025_.pic_hd"
    ]
}
```


### Liveness endpoint


**Overview**

To recognize liveness, a mechanism to affirm interaction with a live individual, we take in audio files along with their respective expected text. Returns the certainty the audio samples match what is expected.  Video  may be used through the same API call.   All input is in .wav format. 


**Request**

Request URL: https://server1.privatebiometrics.com:5443/trueid/liveness

Request Method: POST

Request Payload Example:

```
{
    "audio": [
	["audio_1", "base64_audio_1", "text_expected_1"],
	["audio_2", "base64_audio_2", "text_expected_2"],
	...
	["audio_n", "base64_audio_n", "text_expected_n"]
    ]
}
```


**Response**

The response of a liveness request Returns accuracy data as a ratio from 0 to 1, with a value of .9 denoting 90% accuracy.

```
{
    "accuracy": [
        ["accuracy_1": ".9"],
        ["accuracy_2": ".8"],
        ...
        ["accuracy_n": ".85"]
    ],
}
```

### Delete subject endpoint

**Overview**

Once enrolled a caller can call the Delete subject API to perform an attempt to use the tranied system to delete the individual subject, its roles and enrollment data based upon images or subject id or enrollment data  provided in the call.

**Request**

Request URL: https://server1.privatebiometrics.com:5443/trueid/deleteSubject

Request Method: POST

Request Payload Example:

```
{
    "subject_id": "1008023",
    "enrollment data": {
	"id": "1008023",
    },
    "images": [
	["image_1", "base64_image_1"],
	["image_2", "base64_image_2"],
	...
	["image_n", "base64_image_n"]
    ]
}
```

**Response**

The response of a Delete subject request returns O as  Success.


### Create subject role endpoint

**Overview**

**Request**

Request URL: https://server1.privatebiometrics.com:5443/trueid/createSubjectRole

Request Method: POST

Request Payload Example:

```
{
    "subject_id": "1008023",
    "role_id": "123",
    "role_name": "IDDATAWEB"
}
```

**Response**

The response of a Create subject role request returns O as  Success.


### Delete subject role endpoint

**Overview**

**Request**

Request URL: https://server1.privatebiometrics.com:5443/trueid/deleteSubjectRole

Request Method: POST

Request Payload Example:

```
{
    "subject_id": "1008023",
    "role_id": "123",
    "role_name": "IDDATAWEB"
}
```

**Response**

The response of a Delete subject role request returns O as  Success.


### Create role endpoint

**Overview**

**Request**

Request URL: https://server1.privatebiometrics.com:5443/trueid/createRole

Request Method: POST

Request Payload Example:

```
{
    "tag": "AAPL",
    "value": "Stock Data Service"
}
```

**Response**

The response of a Create role request returns O as  Success.

### Create enrollment data endpoint

**Overview**

Once enrolled a caller can call the Create enrollment data API to add enrollment data.

**Request**

Request URL: https://server1.privatebiometrics.com:5443/trueid/createEnrollment-Data

Request Method: POST

Request Payload Example:

```
{
    "subject_id": "1008023",
}
```

**Response**

The response of a Create enrollment data request returns O as  Success.


### Change enrollment data endpoint

**Overview**

Once enrolled a caller can call the Change enrollment data API to modify enrollment data.

**Request**

Request URL: https://server1.privatebiometrics.com:5443/trueid/changeEnrollment-Data

Request Method: POST

```
{
    "subject_id": "1008023",
    "tag": "name",
    "old_value": "Nguyen",
    "new_value": "Nguyen"
}
```

**Response**

The response of a Change enrollment data request returns O as  Success.


### Delete enrollment data endpoint

**Overview**

Once enrolled a caller can call the Delete enrollment data API to remove enrollment data.

**Request**

Request URL: https://server1.privatebiometrics.com:5443/trueid/deleteEnrollment-Data

Request Method: POST

```
{
    "subject_id": "1008023",
    "tag": "name",
    "value": "Nguyen"
}
```

**Response**

The response of a Delete enrollment data request returns O as  Success.
