# Demo Video 
[![Press here to play video](https://github.com/openinfer/PrivateIdentity/blob/master/images/Fingerprint%20Video%20Image.png)](https://youtu.be/C-rnRqbDS5E "JavaScript API Demonstration")

# Fingerprint Identification Documentation 

![man's finger](https://github.com/openinfer/PrivateIdentity/blob/master/images/fingerprint%20recogni%201.png)
| Accuracy | Type I Error | Type II Error | Speed |
|---|---|---|---|
| **1:1 Verification** | | |
| TMR=99.99% | FMR=0.0001% | FNMR=0.0001% | Speed=300ms |
| **1:Many Identification** | | |
| IR=96.30% | FPIR=0.0001% | FNIR=3.70% | Speed=300ms |
* Recognizes fingerprints using optical scan (camera) or capacitive sensor 
* Supports any Webcams or phone with camera ≥720P (1MP)
* Enrolls an unlimited number of users (“unlimited gallery size”) 
* Operates in polynomial time irrespective of gallery size 
* Trained using the NIST Special Database 4 and CASIA-FingerprintV5 
* Massively scalable using elastic, fault-tolerant, load balanced Kubernetes clusters
* Minimum Imaging Requirements: Fingerprint ≥ 320×240 pixels. Camera ≥720P.  
* MobileNetV2 Architecture, 900kB
* Accepts images using any finger 

# How to call 
## Single Component JavaScript App
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

## JavaScript API

## Encryption Engine

## SBP Server (RESTful API)





