
# JavaScript API Video Tutorial
[![Press here to play video](https://github.com/openinfer/PrivateIdentity/blob/master/images/Javascript%20API%20Video%201.png)](https://youtu.be/wjaFHuELTJA "JavaScript API Demonstration")

# JavaScript API Documentation 
The JavaScript API is a lightweight javascript library that will send encrypted payloads to a Private Identity server (SaaS or PaaS) for enrollment and prediction. A Web page is also hosted at the same URL that provides a sandbox to exercise Enroll and Predict by selecting the images from your browser. 

## Downloading the Library

You can download this library and upload to your domain. The library is available through [this link](http://private.id/MFA-Microapp.zip). Once we unzip this file, we can find a folder called `predict-enroll-library`. This tool consists of one folder, and two files. The `models` folder has all the necessary machine learning models. You can also find `module.js` file, which is responsible for exporting the API methods to the browser. Finally, the `index.html` file has an example of using the models and the `module.js` file.

## Live Demo

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


```html


<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>Predict/Enroll library</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css"
          integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">
    <style>div#canvas-container canvas {
        width: 200px;
        padding: 1%;
        height: 245px;
        border: 1px dotted black;
        margin: 0.5%;
    }</style>
</head>

<body>
<div style="padding: 7%">
    <div class="input-group mb-3">
        <div class="input-group-prepend">
            <span class="input-group-text">Face Images:</span>
        </div>
        <div class="custom-file">
            <input multiple type="file" class="custom-file-input" id="imageFiles">
            <label class="custom-file-label" for="imageFiles">Choose file</label>
        </div>
    </div>

    <div class="input-group mb-3">
        <div class="input-group-prepend">
            <span class="input-group-text">Voice Files:</span>
        </div>
        <div class="custom-file">
            <input multiple type="file" class="custom-file-input" id="voiceFile">
            <label class="custom-file-label" for="imageFiles">Choose file</label>
        </div>
    </div>

    <div class="input-group mb-3">
        <div class="input-group-prepend">
            <span class="input-group-text">Fingerprint images:</span>
        </div>
        <div class="custom-file">
            <input multiple type="file" class="custom-file-input" id="fingeprintImages">
            <label class="custom-file-label" for="imageFiles">Choose file</label>
        </div>
    </div>

    <div class="input-group mb-3">
        <div class="input-group-prepend">
            <span class="input-group-text">Face Validation Images:</span>
        </div>
        <div class="custom-file">
            <input multiple type="file" class="custom-file-input" id="pb-fileToUpload">
            <label class="custom-file-label" for="imageFiles">Choose file</label>
        </div>
    </div>

    <br><br>
    <br>

    <button type="button" id="enroll" class="btn btn-outline-success">Enroll</button>
    <button id="predict" type="button" class="btn btn-outline-primary">Predict</button>
    <button type="button" id="validate" class="btn btn-outline-warning">Validate</button>

    <br>
    <br>
    <br>
    <textarea id="status-textarea" style="margin-top: 0px;margin-bottom: 0px;height: 397px;width: 100%;padding: 2%;">

    </textarea>
    <div id="canvas-container"></div>
</div>

</body>
<script src="module.js"></script>
<script type="module">
  const queryString = window.location.search;
  const urlParams = new URLSearchParams(queryString);
  const apiKey = urlParams.get('apiKey');

  let faceImagesFiles = [];
  let fingerprintImagesFiles = [];
  let voiceFile = null;

  const voiceFileInput = document.getElementById('voiceFile');
  const imagesInput = document.getElementById('imageFiles');
  const validateFiles = document.getElementById('pb-fileToUpload');
  const fingerprintInput = document.getElementById('fingeprintImages');

  const predictButton = document.getElementById('predict');
  const enrollButton = document.getElementById('enroll');

  function getModalities() {
    let faceImages = document.querySelectorAll('canvas.face_canvas');
    let fingerprintImages = document.querySelectorAll('canvas.fingerprint_canvas');
    let params = [];
    if (voiceFile !== null) {
      params = [...params, 'voice', voiceFile];
    }
    if (faceImages.length > 0) {
      params = [...params, 'face', faceImagesFiles];
    }
    if (fingerprintImages.length > 0) {
      params = [...params, 'fp', fingerprintImagesFiles];
    }
    console.log(params);
    return params;
  }

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

  fingerprintInput.addEventListener('change', async function(e) {
    fingerprintImagesFiles = e.target.files;
    removeCurrentCanvases();
    showImagesAsCanvases(e, 'fingerprint');
  });

  imagesInput.addEventListener('change', async function(e) {
    faceImagesFiles = e.target.files;
    removeCurrentCanvases();
    showImagesAsCanvases(e, 'face');
  });
  validateFiles.addEventListener('change', async function(e) {
    removeCurrentCanvases();
    showImagesAsCanvases(e, 'face');
  });

  voiceFileInput.addEventListener('change', async function(e) {
    voiceFile = e.target.files[0];
  });

  function removeCurrentCanvases() {
    document.getElementById('canvas-container').innerHTML = '';
  }

  function showImagesAsCanvases(e, alias) {
    const images = e.target.files;
    console.log('images');
    console.log(images);
    for (let i = 0; i < images.length; i++) {
      let url = URL.createObjectURL(images[i]);
      let image = new Image();
      image.onload = () => {
        console.log('Image loaded!');
        let currentCanvas = document.createElement('canvas');
        currentCanvas.width = image.naturalWidth;
        currentCanvas.height = image.naturalHeight;
        let context = currentCanvas.getContext('2d');
        context.drawImage(image, 0, 0, image.naturalWidth, image.naturalHeight);
        document.getElementById('canvas-container').append(currentCanvas);
        currentCanvas.setAttribute('id', `canvas_${alias}_` + i);
        currentCanvas.setAttribute('class', `canvas ${alias}_canvas`);
      };
      image.setAttribute('id', `image_${alias}_` + i);
      image.setAttribute('class', `image ${alias}_image`);
      image.src = url;
    }
    ;
  }

  const validate = document.getElementById('validate');
  validate.addEventListener('click', async function handleFiles() {
    document.getElementById('status-textarea').innerText = '';
    let files = document.getElementById('pb-fileToUpload').files;
    console.log('files');
    console.log(files);
    console.log('files.length');
    console.log(files.length);
    files = files.length == 0 ? faceImagesFiles : files;
    console.log('files');
    console.log(files);
    let result = await window.validate(files);
    console.log(result);
    result != null ? document.getElementById('status-textarea').innerText = result : '';
  }, false);

</script>
<script src="https://code.jquery.com/jquery-3.2.1.slim.min.js"
        integrity="sha384-KJ3o2DKtIkvYIK3UENzmM7KCkRr/rE9/Qpg6aAZGJwFDMVNA/GpGFF93hXpG5KkN"
        crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.12.9/umd/popper.min.js"
        integrity="sha384-ApNbgh9B+Y1QKtv3Rn7W3mgPxhU9K/ScQsAP7hUibX39j7fakFPskvXusvfa0b4Q"
        crossorigin="anonymous"></script>

<script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/js/bootstrap.min.js"
        integrity="sha384-JZR6Spejh4U02d8jOt6vLEHfe/JQGiRRSQQxSfFWpi1MquVdAyjUar5+76PVCmYl"
        crossorigin="anonymous"></script>

</html>
```
