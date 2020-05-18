### Overview 


In this document, the enrollment process will be documented for each modality. Namely, face, voice, and fingerprint modalities. This document utilizes NodeJS endpoints, which handles requests and sends them back to Python endpoints. 

### Enroll Overview

NodeJS endpoints can be called directly to execute predict, enroll, or any other provided service. In the following examples, we will be exploring the enrollment process initiated from any device, to the NodeJS server.

**Request**

The format of this API call is:  

POST “/node/enroll”

|Parameter     |         Value| 
|-----|----|
|PII           |         Tag/Value pairs|
|Features      |         Type, Name, Feature Array. Type is voice, face or fingerprint.|
|api_key      |         api_key value in string.|

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
    ]
    "api_key": "xxxxx"
}
```

**Response**

The response of an Enroll request returns O as Success given data validation and database storage success.
The response returns -1 if the user already exists in the model.
The response returns -2 if the embedding distance is too far caused by at least one bad enroll embedding (usually caused by a bad enroll image).

If the api_key is not present in the request payload, an error message will be returned and the user will not be enrolled.