### How to find your Subject ID on /a/
<br/>

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

## Merging Face and Voice Enrollments
<br/>

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

## User Interface Demonstration
<br/>

There are two versions of the demonstration app, the first one is version 0.9, and the parameters are selected manually. The second version, version 1.0, has an interface from which you can select parameters.

You can access version 1.0 with this link: [Version 1.0 Demo](https://private.id/demo/index.htm?apiKey=1962)

Version 1.0 and Version 0.9 are functionally the same, so an enrollment made on one version, can be accessed on another.

A picture with the panel layout explained is shown below, or you can view a demonstration video from this link
[Demonstration](https://www.youtube.com/watch?v=6x0b5FckhIA)

![Version 1.0 User Interface](https://github.com/openinfer/PrivateIdentity/blob/master/images/Version%201.0%20UI.png)

## Anti Spoofing Technique
<br/>

Spoofing is a well-known scenario when a user with malicious intent tries to bypass the biometric security by playing a recorded video/printed image.

To enable the anti-spoofing in the application, add the URL parameter `antiVideoSpoof=true` while launching the application. This enables the application to check whether the stream of images captured from the webcam is a recorded one or a live one. This is achieved by a machine learning model running in the browser that checks the image passed to it and gives back a probability of whether the image is a spoofed one or not. If the spoofing is detected, the application won't allow the user to perform the requested operation until it is a live one. There are two models to detect when someone is spoofing, the first one detects if the spoof origin is a video on a device or an image on a device. The second one detects if the spoof origin is a print image. So for example if someone tried using a spoof printed image of a face, it will pass through the device image or device video model, but will be caught on the print image model and be detected as spoof.

Sample Demonstration of Video Spoofing:

![Video Spoof Demo](https://github.com/openinfer/PrivateIdentity/blob/master/images/Spoof_Icon_Example.png)

Another way to check the spoofing is to check whether the liveness of the user can be verified. This can be detected by checking the user's eye blink from the sequence of captured images. To enable the liveness of the user, either add the URL parameter `faceLiveness=true` or double click on the face icon before performing a enroll/prediction.

Sample Demonstration of Eyeblink success:

![Eye Blink Demo](https://github.com/openinfer/PrivateIdentity/blob/master/images/eye_blink_demo.png)