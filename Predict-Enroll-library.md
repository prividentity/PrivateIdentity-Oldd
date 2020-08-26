## Predict Enroll library  ##

Predict Enroll Library is a javascript library that will help you to Enroll and Predict by selecting the images from your browser. This library will send images to a Private Identity server or your own hosted Private Identity server for enrollment and prediction.

## Local Web Server Setup ##

To run Predict Enroll library you need a web server like apache2 or nginx

**Note**: If you already have a web server you can skip below steps to install apache2 and simply unzip the downloaded code and move it to /var/www/html/ directory.

#### Option 1: Apache2 #### 

1. Download Zip file form URL https://private.id/predict-enroll-library.zip

2. Install apache2  `sudo apt-get install apache2`

3. Unzip predict library `unzip predict-enroll-library.zip` 

4. Move code to the following location `mv predict-enroll-library /var/www/html/`

5. Start apache2 service `sudo service apache2 start`

#### Option 2: Nginx #### 

1. Download Zip file form URL an https://private.id/predict-enroll-library.zip

2. Install nginx `sudo apt-get install nginx`

3. Unzip predict library `unzip predict-enroll-library.zip` 

4. Move code to the following location `mv predict-enroll-library /var/www/html/` 

5. sudo service nginx start


After this, you will able to access predict and enroll from the demo page app. 

Launch the below-mentioned URL in your browser and replace XXXX with apiKey value provided by Private identity:

http://localhost/predict-enroll-library/?apiKey=XXXX

By default, the NodeJS endpoints are located at `https://private.id/node/`. If you want to change this setting, you can use the URL parameter `nodeServer` to your own private hosted server.

To host your own private server, please have a look at this [link](https://github.com/openinfer/PrivateIdentity/wiki/cluster-setup) which will give detailed step-by-step instructions on how to configure the endpoint.

For ex., if your own server is `https://company.privateidentity.com` then the URL will be

 http://localhost/predict-enroll-library/?apiKey=XXXX&nodeServer=https://company.privateidentity.com/

---------------------------------------------------------------------
This is the demo page app for Enroll and predict using Voice,Face.
1. Sample Demo Page

[[ images/Title.png ]]

2. Load 10 face images and Voice file and Click Enroll

![Load Image and Voice](https://github.com/openinfer/PrivateIdentity/blob/master/images/Load%20images%20and%20voice.png)

3. Sample Enroll Response

![Enroll Result](https://github.com/openinfer/PrivateIdentity/blob/master/images/Enroll%20Result.png)

4. Load 3 face images or voice file and click predict. Sample predict response is shown below.

![Predict Result](https://github.com/openinfer/PrivateIdentity/blob/master/images/Predict%20result.png)

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

1- Face is detected in input or not. 
2- Face is very close or far away in the image.
3- Face is blurry or not. 
4- Input is spoof or not. 

