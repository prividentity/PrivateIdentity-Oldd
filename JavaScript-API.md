# JavaScript API Demo Video 
[![Press here to play video](https://github.com/openinfer/PrivateIdentity/blob/master/images/Javascript%20API%20Video%201.png)](https://youtu.be/C-rnRqbDS5E "JavaScript API Demonstration")

# JavaScript API Documentation 
The JavaScript API is a lightweight javascript library that will send encrypted payloads to a Private Identity server (SaaS or PaaS) for enrollment and prediction. A Web page is also hosted at the same URL that provides a sandbox to exercise Enroll and Predict by selecting the images from your browser. 

Launch the below-mentioned URL in your browser and replace XXXX with apiKey value provided by Private identity.

http://private.id/predict-enroll-library/?apiKey=XXXXXXXXXXXXXXXXX

---------------------------------------------------------------------
This is the demo page app for Enroll and Predict using Face, Voice or Fingerprint.
1. Sample Demo Page

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/JavascriptAPI%201.png)

2. Load 10 face images and Voice file and Click Enroll

![Load Image and Voice](https://github.com/openinfer/PrivateIdentity/blob/master/images/JavascriptAPI%202%20a.png)

3. Sample Enroll Response

![Enroll Result](https://github.com/openinfer/PrivateIdentity/blob/master/images/JavascriptAPI%203%20a.png)

4. Load 3 face images or voice file and click predict. Sample predict response is shown below.

![Predict Result](https://github.com/openinfer/PrivateIdentity/blob/master/images/JavascriptAPI%204%20a.png)


## Predict Request

`Method: window.predict(apiKey, 'face', images1, 'voice', voiceFile, 'fingerprint', images2);`


|Parameter     |         Value| 
|-----|----|
|apiKey           |         API Key retrieved from URL parameter |
|’face’      |         Modality type for face prediction.|
|images1      |         Array of image files.|
|’voice’      |         Modality type for voice prediction.|
|voiceFile      |         Type File voice.|
|’fingerprint’      |         Modality type for fingerprint prediction.|
|images2      |         Array of image files.|

The method window.predict predicts for face, voice, or fingerprint modalities. It can use single or multiple modalities. 

The image1, and image2 parameters are file objects. Voice files utilizes the HTML file input element to be added in the method argument.


**Example**

```
{
   "apiKeyValue",
   "face",
   [
       {File:
          lastModified: 1592228890000,
          name: image1.png,
          type: "image/png",
          size: 1073218
       },
       {File:
          lastModified: 1592228891234,
          name: image2.png,
          type: "image/png",
          size: 1073218
       }
       ...,
       ...
   ],
   'voice',
   {File:
       lastModified: 1592228891234,
       name: testWav.wav,
       type: "audio/wav",
       size: 1073218
   },
   'fingerprint',
   [
       {File:
          lastModified: 1592228890000,
          name: image3.png,
          type: "image/png",
          size: 1073218
       },
       {File:
          lastModified: 1592228891234,
          name: image4.png,
          type: "image/png",
          size: 1073218
       }
       ...,
       ...
   ]
}
```

**Response**


The response of a predicted request, if threshold confidence are met, returns enrollment data in the following format:
```
{
    "enrollment data": {
        "enroll_level": "1"
        "modality": "voice,face"
        "uuid": "l1a25w8x2a9f4e3x8s1a"
    },
    "message": "OK",
    "status": 0,
    "subject_id": "100045",
}
```


## Enroll Requests

`Method: window.enroll(uuid, apiKey, 'face', images1, 'voice', voiceFile, 'fingerprint', images2);`


|Parameter     |         Value| 
|-----|----|
|uuid           |         String value of UUID |
|apiKey           |         API Key retrieved from URL parameter |
|’face’      |         Modality type for face prediction.|
|images1      |         Array of image files.|
|’voice’      |         Modality type for voice prediction.|
|voiceFile      |         Type File voice.|
|’fingerprint’      |         Modality type for fingerprint prediction.|
|images2      |         Array of image files.|

The method window.enroll enrolls for face, voice, or fingerprint modalities. It can use single or multiple modalities. 


**Example**

```
{
   "uuidValue",
   "apiKeyValue",
   "face",
   [
       {File:
          lastModified: 1592228890000,
          name: image1.png,
          type: "image/png",
          size: 1073218
       },
       {File:
          lastModified: 1592228891234,
          name: image2.png,
          type: "image/png",
          size: 1073218
       }
       ...,
       ...
   ],
   'voice',
   {File:
       lastModified: 1592228891234,
       name: testWav.wav,
       type: "audio/wav",
       size: 1073218
   },
   'fingerprint',
   [
       {File:
          lastModified: 1592228890000,
          name: image3.png,
          type: "image/png",
          size: 1073218
       },
       {File:
          lastModified: 1592228891234,
          name: image4.png,
          type: "image/png",
          size: 1073218
       }
       ...,
       ...
   ]
}
```

**Response**

The response of an Enroll request returns `O` as a success given data validation and database storage success. The response returns `-1` if the user already exists in the model. The response returns `-2` if the embedding distance is too far caused by at least one bad enroll embedding (usually caused by a bad enroll image).

```
{
    "enrollment data": {
        "enroll_level": "1"
        "modality": "voice,face"
        "uuid": "l1a25w8x2a9f4e3x8s1a"
    },
    "guid": "100045",
    "message": "OK",
    "status": 0,
}
```


## Validation

`Method: window.validate(imageFiles);`

|Parameter     |         Value| 
|-----|----|
|imageFiles      |         Array of image files.|


The method window.validate accepts image files as input. The input can be one or a group of images. In the browser console you can see the result of validation. The method check to see if:

1. Face is detected in input or not.
2. Face is very close or far away in the image.
3. Face is blurry or not.
4. Input is spoof or not.
5. Face has glasses or not. 
6. Face has masks or not. 


**Example**

```
{
   {File:
      lastModified: 1592228890000,
      name: image1.png,
      type: "image/png",
      size: 1073218
    }
}
```


**Response**


```
{"0":
   {"faceStatus":"Face detected",
   "spoofStatus":"Spoof not detected",
   "distanceStatus":"Face is at good distance",
   "imageStatus":"Face is acceptable"}
}
```

**Possible Results**


|Field     |         Possible Values| 
|-----|----|
|faceStatus      |         Face detected or Face not detected.|
|spoofStatus      |         Spoof detected or Spoof not detected.|
|distanceStatus      |         Face is close to the camera, Face is far away from the camera or Face is at good distance.|
|blurryStatus      |         Blurry or Not blurry.|
|glassesStatus      |         Glasses detected or Glasses not detected.|
|maskStatus      |         Face mask detected or Face mask not detected.|

## Sample Code

Here are sample code examples for each of the three described methods. 

**JavaScript**

```javascript
predictButton.addEventListener('click', async function(e) {
    document.getElementById('status-textarea').innerText = '';
    const modalitiesList = getModalities();
    const result = await window.predict(apiKey, ...modalitiesList);
    console.log('result');
    console.log(result);
    result != null ? document.getElementById('status-textarea').innerText = JSON.stringify(result) : '';
  });

  enrollButton.addEventListener('click', async function(e) {
    document.getElementById('status-textarea').innerText = '';
    const modalitiesList = getModalities();
    const result = await window.enroll(undefined, apiKey, ...modalitiesList);
    console.log('result');
    console.log(result);
    result != null ? document.getElementById('status-textarea').innerText = JSON.stringify(result) : '';
  });

validate.addEventListener('click', async function handleFiles() {
    document.getElementById('status-textarea').innerText = '';
    let files = document.getElementById('pb-fileToUpload').files;
    files = files.length == 0 ? faceImagesFiles : files;
    let result = await window.validate(files);
    console.log(result);
    result != null ? document.getElementById('status-textarea').innerText = result : '';
  }, false);
```
## Sample code discussed in video 
