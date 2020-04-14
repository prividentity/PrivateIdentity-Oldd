[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

### SBP API Overview

**Format**

All API communicate RESTful using JSON.  

**Developer API_Key**

Individual developers need to apply for an API_Key for their applications that shall use SBP. Once individual developers have their own API_Key, all of the API calls their applications make use this API_Key as one of the parameters.

### API Enroll Overview

To enroll a user, we take as input the PII Data which is a set of tag/value pairs (any tag, such as an ID number or GUID is acceptable; this does not need be PII) and the feature vectors used for training given as input under the “PII” and “features” fields respectively. Using a Global UUID a new identity is created in the persistent engine corresponding to the PII provided.

**Request**

The format of this API call is:  

POST “/trueid/v1.1/enroll”

|Parameter     |         Value| 
|-----|----|
|api_key       |         api_key string to use this service|
|PII           |         Tag/Value pairs|
|features      |         Type, Name, Feature Array. Type is voice, face or fingerprint.|

An Enroll API request example is as follows:
```
{
    "api_key": "XXXXXXXXXXXXXXXXXX",
    "PII": {
       "name": "Nguyen",
	"id": "1008023",
	...
       "address": "23 Scott Street"
    },
    "features": [
	{“type”: “voice”, name: “voice1.wav”,  “embedding_vector”: [...] },
	{“type”: “face”, name: “face1.png”, “embedding_vector”: [...]},
        {“type”: “fingerprint”, name: “fingerprint1.png”, “embedding_vector”: [...]},

	…
	{}
    ]

}
```

**Response**

The response of an Enroll request returns O as Success given data validation and database storage success.
The response returns -1 if the user already exists in the model.
The response returns -2 if the embedding distance is too far caused by at least one bad enroll embedding (usually caused by a bad enroll image).


### Predict Overview

Once enrolled, a caller shall call the Predict API to perform an attempt to use the trained system to identify the individual subject based upon images provided in the call.

**Request**

The format of this API call is: 

POST “/trueid/v1.1/predict”

|Parameter      |            Value|
|----------|--------------| 
|api_key       |         api_key string to use this service|
|features       |            Type, Name, Feature Array. Type is voice, face or fingerprint.|


A Predict API request example is as follows:
```
{
    "api_key": "XXXXXXXXXXXXXXXXXX",
    "features": [
	{“type”: “voice”, name: “voice1.wav”,  “embedding_vector”: [...] },
	{“type”: “face”, name: “face1.png”, “embedding_vector”: [...]},
        {“type”: “fingerprint”, name: “fingerprint1.png”, “embedding_vector”: [...]},
	…
	{}
    ]
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
    ]
}
```
Format
All API names are in the RESTful JSON format.  All feature vectors have a type: “voice”, “face”, or “fingerprint”.

Developer API_Key
Individual developers need to apply for an API_Key for their applications. Once individual developers have their own API_Key, all of the API calls their applications make insert this API_Key as one of the parameters. The use of an API key is not mandatory and implementers shall use a variety of implementation strategies or no API key whatsoever. The examples below show an API_KEY through the URL property of key=.

API
Enroll
Overview
To enroll a user, we take as input  the PII Data which is a set of tag/value pairs and the feature vectors used for training given as input under the “PII” and “features” fields respectively. Using a Global UUID a new identity is created in the persistent engine  corresponding to the PII provided.
Request
The format of this API call is:  

POST “/trueid/v1.1/enroll”

|Parameter  |  Value|
|---------|--------|
|PII        |   Tag/Value pairs|
|api_key       |         api_key string to use this service|
|Features   | Type, Name, Feature Array. Type is voice, face or fingerprint.|

An Enroll API request example is as follows:
```
{
    "PII": {
       "name": "Nguyen",
	"id": "1008023",
	...
       "address": "23 Scott Street"
    },
    "features": [
	{“type”: “voice”, name: “voice1.wav”,  “embedding_vector”: [...] },
	{“type”: “face”, name: “face1.png”, “embedding_vector”: [...]},
        {“type”: “fingerprint”, name: “fingerprint1.png”, “embedding_vector”: [...]},

	…
	{}
    ],
    "api_key": "xxxxx"
}
```

**Response**

The response of an Enroll request returns O as Success given data validation and database storage success.
Predict
Overview
Once enrolled a caller shall call the Predict API to perform an attempt to use the trained system to identify the individual subject based upon images provided in the call.
Request
The format of this API call is: 

POST “/trueid/v1.1/predict”

|Parameter   | Value|
|----------|--------|
|Features    | Type, Name, Feature Array.  Type is voice, face or fingerprint.|




A Predict API request example is as follows:
```
{
    "features": [
	{“type”: “voice”, name: “voice1.wav”,  “embedding_vector”: [...] },
	{“type”: “face”, name: “face1.png”, “embedding_vector”: [...]},
        {“type”: “fingerprint”, name: “fingerprint1.png”, “embedding_vector”: [...]},
	…
	{}
    ]
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
    ]
}
```
### Liveness Overview

To recognize liveness, a mechanism to affirm interaction with a live individual, we take in audio files along with their respective expected text. The API call returns a value related to the certainty that the audio samples match what is expected.  Video  shall be used through the same API call.   All input is in .wav format.  Liveness is a local client call, typically, but is supported on the server in the format listed below.  The best practice is for a local liveness call so that plaintext is not transmitted.  

**Request**

The format of this API call is: 

POST “/trueid/v1.1/liveness”
```
{
    "voice": [
        ["voice_1", "base64_audio_1", "text_expected_1"],
        ["voice_2", "base64_audio_2", "text_expected_2"],
        ...
        ["voice_n",  "base64_audio_n", text_expected_n"]
    ],
    "api_key": "xxxxxx"
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
### Add Role Overview

This API helps add role parametres to the database. The role helps us assign different levels to the subjects enrolled in the database. Role consists of two parameters named as <tag> and <value>. For ex., <tag> can define the name of the role such as admin, developer etc., whereas the <value> defines the level of access that can be granted to the user level1, tier1 etc.,. The <tag> and <value> can be anything depending upon the convenience of the user. The request must be a post with the values passed in the request body as JSON.


**Request**

The format of this API call is: 

POST  “/trueid/v1.1/add_role”

|Parameter | Value             |
|----------|-------------------|
|tag       | String, Role Name |
|value     | String, Role value|
|api_key     | api_key in string value|
```
{
    "tag": "admin",
    "value": "L1"
}
```
**Response**

The response of add role request returns <role_id> of the <tag> and <value> added to the database with a status of 0, where the <role_id> will be an auto-generated number from the system. This <role_id> is then used for adding the role to the particular subject. If the add role fails, API will return a status of -2 with the reason in the message.
```
{
   “status”: 0
   “role_id” : 1
   “message” : “Role Successfully added.”
}
{
   “status”: -2
   “message” : “Role exists in database”
}
```
### Delete Role Overview

This API helps delete a role parametres from the database. To delete the role from the database, the user must know the <role_id> acquired during the addition of role to the database. The request must be a post with the values passed in the request body as JSON.


**Request**

The format of this API call is: 

POST  “/trueid/v1.1/delete_role”

|Parameter | Value           |
|----------|-----------------|
|role_id   | Number, Role ID |
|api_key     | api_key in string value|

```
{
    "role_id": 1,
    "api_key": "xxxxx"
}
```
**Response**

The response of delete role request returns a status of 0 upon successful deletion. <role_id> must be passed in the request body. If the delete role fails, API will return a status of -2 with the reason in the message.
```
{
   “status”: 0
   “message” : “Role Successfully deleted.”
}

{
   “status”: -2
   “message” : “RoleID does not exists in database”
}
```
### Add Role to Subject

This API helps to add an existing role to a particular subject. Request must provide both the <role_id> and the <subject_id> they want to add. The request must be a post with the values passed in the request body as JSON.


**Request**

The format of this API call is: 

POST  “/trueid/v1.1/add_role_to_subject”

|Parameter | Value              |
|----------|--------------------|
|role_id   | Number, Role ID    |
|subject_id| Number, Subject ID |
|api_key     | api_key in string value|
```
{
    "role_id": 1,
    "subject_id":4,
    "api_key": "xxxxxx"
}
```
**Response**

The response of add role to subject request returns a status of 0 upon successful addition. <role_id> and <subject_id> must be passed in the request body. If the API fails, it will return a status of -2 with the reason in the message. The API will also fail if there is no specified <role_id> or <subject_id> present in the database.
```
{
   “status”: 0
   “message”: “Role Successfully added to the Subject.”
}

{
   “status”: -2
   “message” : “Not a valid subject/Role. (or) Role exists in database”
}
```
### Delete Role from Subject

This API helps to delete a role from a particular subject. Request must provide both the <role_id> and the <subject_id> they want to remove. The request must be a post with the values passed in the request body as JSON.

**Request**

The format of this API call is: 

POST  “/trueid/v1.1/delete_role_from_subject”

|Parameter | Value              |
|----------|--------------------|
|role_id   | Number, Role ID    |
|subject_id| Number, Subject ID |
|api_key     | api_key in string value|
```
{
    "role_id": 1,
    "subject_id":4,
    "api_key": "xxxxx"
}
```
**Response**

The response of delete role from subject request returns a status of 0 upon successful deletion. <role_id> and <subject_id> must be passed in the request body. If the API fails, it will return a status of -2 with the reason in the message. The API will also fail if there is no specified <role_id> or <subject_id> present in the database.
```
{
   “status”: 0
   “message”: “Role Successfully deleted from Subject.”
}

{
   “status”: -2
   “message” : “Not a valid subject/Role. (or) Role does not exist in database”
}
```


### API Verify Overview

To check the distance between the given embeddings_1 array with the given embeddings_2 array or the embeddings of enrolled person with given subject_id

**Request**

The format of this API call is:  

POST “/trueid/v1.1/verify”

|Parameter     |         Value| 
|-----|----|
|api_key       |         api_key string to use this service|
|type          |         a string (face, voice, fingerprint)|
|embeddings_1  |         a list of embeddings of the first person |
|embeddings_2  |         a list of embeddings of the second person if subject_id is not provided|
|subject_id    |         Number, Subject ID of the enrolled person to retrieve embeddings if embeddings_2 is not provided|

An API request example is as follows:
```
{
   "api_key": "xxxxx",
   "type": "face",
   "embeddings_1": [
  		[...],
                [...],
                 …
  	],
   "embeddings_2": [
	  	[...],
                [...],
                 …
	]
}
```

Another API request example is as follows:
```
{
   "api_key": "xxxxx",
   "type": "face",
   "embeddings_1": [
  		[...],
                [...],
                 …
  	],
   "subject_id": 1
}
```

**Response**

The response returns -1 if there is error. If return 0, it's success and provide information as:
```
{
    "status": 0,
    "distance": {
        "max": 1.3864889343185174,
        "mean": 1.3714485861588377,
        "min": 1.3531817732607498
    },
    "threshold": {
        "max": 0.55,
        "mean": 0.5,
        "min": 0.3
    }
}
```

