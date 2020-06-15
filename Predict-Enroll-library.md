## Setup Predict Enroll library ##

### To run this you need a web server like apache2 or nginx ###

**Note**: If you already have web server you can skip below steps to install apache2 and simply unzip the downloaded code and move it to /var/www/html/ directory.

#### If you want to install an apache2 follow below steps #### 

1. Downlaod Zip file form URL https://private.id/predict-enroll-library.zip

2. Install apache2  `sudo apt-get install apache2`

3. unzip predict library `unzip predict-enroll-library.zip` 

4. move code to html location `mv predict-enroll-library /var/www/html/`

5. start apache2 service `sudo service apache2 start`



#### If you want to install an nginx follow below steps #### 

1. Downlaod Zip file form URL an https://private.id/predict-enroll-library.zip

2. Install nginx `sudo apt-get install nginx`

3. unzip predict library `unzip predict-enroll-library.zip` 

4. move code to html location `mv predict-enroll-library /var/www/html/` 

5. sudo service nginx start


After this you will able to access predict and enroll from the demo page app. 

http://localhost/predict-enroll-library/?apiKey=XXXX

By default, the NodeJS endpoints are located at `https://private.id/node/`. If you want to change this setting, you can use URL parameter `nodeServer`. 

Example: http://localhost/predict-enroll-library/?apiKey=XXXX&nodeServer=https://example.com/

---------------------------------------------------------------------
This is the demo page app for Enroll and predict using Voice,Face.

[[ images/Title.png ]]

**Note:** You will get the API key from Private Identity.


**Predict Requests**

`Method: window.predict(apiKey, 'face', images1, 'voice', voiceFile, 'fingerprint', images2);`


|Parameter     |         Value| 
|-----|----|
|apiKey           |         API Key retrieved from URL parameter |
|’face’      |         Modality type for face prediction.|
|images1      |         Array of ImageData.|
|’voice’      |         Modality type for voice prediction.|
|voiceFile      |         Type File voice.|
|’fingerprint’      |         Modality type for fingerprint prediction.|
|images2      |         Array of ImageData.|

The method window.predict can be used for face, voice, or fingerprint prediction. This method can be used for any of them, or all together. 

**Response**


The response of a Predict request, if meeting confidence thresholds, returns PII data in the following format:
```
{
    "PII": {
        "uuid": random_hexstring
    },
    "message": "OK",
    "status": 0,
    "subject_id": subject_id_from_system,
}
```

**Enroll Requests**

`Method: window.enroll(uuid, apiKey, 'face', images1, 'voice', voiceFile, 'fingerprint', images2);`


|Parameter     |         Value| 
|-----|----|
|uuid           |         String value of UUID |
|apiKey           |         API Key retrieved from URL parameter |
|’face’      |         Modality type for face prediction.|
|images1      |         Array of ImageData.|
|’voice’      |         Modality type for voice prediction.|
|voiceFile      |         Type File voice.|
|’fingerprint’      |         Modality type for fingerprint prediction.|
|images2      |         Array of ImageData.|

The method window.enroll can be used for face, voice, or fingerprint prediction. This method can be used for any of them, or all together. 

**Response**

The response of an Enroll request returns O as Success given data validation and database storage success. The response returns -1 if the user already exists in the model. The response returns -2 if the embedding distance is too far caused by at least one bad enroll embedding (usually caused by a bad enroll image).
