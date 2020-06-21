### Predict Overview

In this document, the process of prediction will be explained in terms of SaaS architecture. For any prediction request to execute, an api_key must be sent inside the request payload. 

** Request **

The format of this API call is:

POST “/node/predict”

|Parameter      |            Value|
|----------|--------------| 
|Features       |            Type, Name, Feature Array. Type is voice, face or fingerprint.|
|api_key       |            api_key value in string.|


A Predict API request example is as follows:
```
{
    "features": [
	{“type”: “voice”, name: “voice1.wav”,  “embedding_vector”: [...] },
	{“type”: “face”, name: “face1.png”, “embedding_vector”: [...]},
        {“type”: “fingerprint”, name: “fingerprint1.png”, “embedding_vector”: [...]},
	…
	{}
    ],
    "api_key": "xxxx"
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
}
```

If the api_key is not present in the request payload, an error message will be returned. 