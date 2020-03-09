### Liveness Overview

To recognize liveness, a mechanism to affirm interaction with a live individual, we take in audio files along with their respective expected text. The API call returns a value related to the certainty that the audio samples match what is expected.  Video  shall be used through the same API call.   All input is in .wav format.  Liveness is a local client call, typically, but is supported on the server in the format listed below.  The best practice is for a local liveness call so that plaintext is not transmitted.  

For a liveness request to execute, an api_key must be sent inside payload. 

**Request**

The format of this API call is: 

POST “/node/liveness”
```
{
    "voice": [
        ["voice_1", "base64_audio_1", "text_expected_1"],
        ["voice_2", "base64_audio_2", "text_expected_2"],
        ...
        ["voice_n",  "base64_audio_n", text_expected_n"]
    ], 
    "api_key": "xxxx"
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

If the api_key parameter is not present in request payload, an error message will be returned. 