### How to find your Subject ID on /a/
**There are two methods of determining your subject ID**

> Note, the usage of console is required, so if you are on a handheld device you will have to link to a computer to view the console. Such as an iPhone linking to a macbook to portray the console. Console is accessible on Safari, Firefox, and Google Chrome, and Microsoft Edge.

**Method 1** (during enrollment):
* Enroll your face and/or voice

* Inspect Element, and then select the Console Tab

> ![](https://github.com/openinfer/PrivateIdentity/blob/master/images/chrome-right-click-inspect.png)
> ![](https://github.com/openinfer/PrivateIdentity/blob/master/images/inspect_console.png)
* Your subject ID will show up as either `subject_id:#` or `guid:#`
> ![](https://github.com/openinfer/PrivateIdentity/blob/master/images/SubjectID_Console_During_Enrollment.png)

**Method 2** (after enrollment):
* In the URL use the parameter &action=predict and run the prediction.

* Inspect Element, and the select the Console Tab
> ![](https://github.com/openinfer/PrivateIdentity/blob/master/images/chrome-right-click-inspect.png)
> ![](https://github.com/openinfer/PrivateIdentity/blob/master/images/inspect_console.png)
* Your subject ID will show up as either `subject_id:#` or `guid:#`
> ![](https://github.com/openinfer/PrivateIdentity/blob/master/images/SubjectID_Console_During_Enrollment.png)

###

This page documents how to update enrolled user modalities. This document assumes a user is already enrolled by only one modality (like face or voice) and they want to add another one on top of it. 

Note that only one modality can be enrolled for this to work, if a face modality is to be added to a voice modality, the face modality can't already exist. In this case use the parameter action=subjectDelete&subject_id=# this will delete your modality specified with the subject id.

The following workflow must start with the user predicting with one modality to get his subject_id. Afterwards, the user should manually go to the application interface, with the newly requested modality equaling to true.

**Request**


The format of this API call is:  


|Parameter     |         Value| 
|-----|----|
|api_key       |         api_key string to use this service|
|action           |         Must be set to enroll|
|subject_id      |         subject_id retrieved from initial predict.|

In addition to the previous parameters, a certain modality must be set to true, while the original one should be set to false.


**Example**

A certain user is enrolled with face, and can successfully predict with that. This user wants to enroll with voice, too. The subject_id parameter must be retrieved from the face predict. Next, the URL the user should have the following parameters to enroll with voice:

GET “/apiKey=xxxx&voice=true&face=false&action=enroll&subject_id=x”

NOTE: the other modality should be set to false for this feature to work.


**Response**

After the merge is complete, the response from the console will be seen as the following, note that the ID will be the same as the original ID:

```
{
    "guid":1,
    "message":"OK",
    "status":0
}
```

