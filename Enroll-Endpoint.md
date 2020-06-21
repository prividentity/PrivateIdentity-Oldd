### Enroll Endpoint

To enroll a user, we take the users Enrollment Data which is a set of tag/value pairs (any tag, such as an ID number or GUID is acceptable). Using a Global UUID a new identity is created in the persistent engine corresponding to the enrollment data provided.

The api_key parameter must be available in request payload, in string value.

**Request**

The format of this API call is:  

POST “/node/enroll”

|Parameter     |         Value| 
|-----|----|
|subject_id, uuid           |         Tag/Value pairs|
|Features      |         Type, Name, Feature Array. Type is voice, face or fingerprint.|
|api_key      |         api_key value in string.|

An Enroll API request example is as follows:
```
{
    "enrollment data": {
	"id": "1008023"
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