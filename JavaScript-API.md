## JavaScript API  ##

JavaScript API is a javascript library that will help you to Enroll and Predict by selecting the images from your browser. This library will send images to a Private Identity server or your own hosted Private Identity server for enrollment and prediction.

Launch the below-mentioned URL in your browser and replace XXXX with apiKey value provided by Private identity:

http://private.id/predict-enroll-library/?apiKey=XXXX


---------------------------------------------------------------------
This is the demo page app for Enroll and predict using Voice,Face.
1. Sample Demo Page

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/first.png)

2. Load 10 face images and Voice file and Click Enroll

![Load Image and Voice](https://github.com/openinfer/PrivateIdentity/blob/master/images/second-enroll2.png)

3. Sample Enroll Response

![Enroll Result](https://github.com/openinfer/PrivateIdentity/blob/master/images/second-enroll2.png)

4. Load 3 face images or voice file and click predict. Sample predict response is shown below.

![Predict Result](https://github.com/openinfer/PrivateIdentity/blob/master/images/predict.png)

**Note:** You will get the API key from Private Identity.


**Predict Request**

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


---------------------------------------------------------------------


**Enroll Requests**

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


---------------------------------------------------------------------

**Face Validation**

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





