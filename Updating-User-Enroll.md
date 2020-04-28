This page documents how to update enrolled user modalities. This document assumes a user is already enrolled by only one modality (like face or voice) and want to add another one on top of it.

The following workflow must start with the user predicting with one modality to get his subject_id. Afterwards, the user should manually go to the application interface, with the newly requested modality equaling to true.

**Example**

A certain user is enrolled with face, and can successfully predict with that. This user wants to enroll with voice, too. The subject_id parameter must be retrieved from the face predict. Next, the URL the user should have the following parameters to enroll with voice:

GET “/apiKey=xxxx&voice=true&face=false&action=enroll&subject_id=x”

NOTE: the other modality should be set to false for this feature to work.

**Response**
After the user enroll with voice, the response from the server will be looking as follows:

```
{"guid":1,"message":"OK","status":0}
```
