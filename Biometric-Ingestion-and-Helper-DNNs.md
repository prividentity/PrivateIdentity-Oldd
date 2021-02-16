## GEOMETRY DETECTION, VALIDATION AND EMBEDDING DNNs

![Facial Recognition Workflow](https://github.com/openinfer/PrivateIdentity/blob/master/images/Workflow%20-%20Face.png)

![Fingerprint recognition workflow](https://github.com/openinfer/PrivateIdentity/blob/master/images/Workflow%20-%20Fingerprint.png)

### FACE, FACE w/MASK, AND FINGERPRINT GEOMETRY DETECTION DNNs
* <b>Transforms images into geometric primitives</b> to measure the relative position, width, and other parameters of eyes, mouth(s), nose(s), chin(s), and finger(s)
* <b>Returns X and Y coordinates</b> of each modality in an image, video frame or video stream.
* YOLO architecture, 100kB

The Face Geometry Detection DNN accurately locates face(s) in an image by transforming each image into geometric primitives and measuring the relative position, width, and other parameters of eyes, mouth(s), nose(s), and chin(s). Likewise, the Fingerprint Geometry Detection DNN accurately locates finger(s) in an image by transforming each image into geometric primitives and measuring each finger’s relative position, width, and other parameters.  

Each DNN returns X and Y coordinates of each modality in an image, video frame or video stream. This DNN is on (true) by default and is required to return an accurate result.   

### FACE, FACE WITH MASK & FINGERPRINT VALIDATION DNNs
* <b>Returns a validation score</b> between 0 to 100, where 100 is a perfect image.  
* MobileNetV2 architecture, 1.5MB

The Face Validation DNN accurately validates each frontalized face input image. Likewise, the Fingerprint Validation DNN accurately validates each fingerprint input image. Each DNN returns a validation score between 0 to 100, where 100 is a perfect image. This DNN is on (true) by default and is required to return an accurate result.   

### 3 CLASS (GOOD, EYEGLASSES, FACE MASK) VALIDATION DNN
The three classes detection algorithm determines if a subject is in good quality, wearing eyeglasses or wearing a face mask. Wearing eyeglasses or a face mask during enrollment lowers subsequent enrollment or prediction performance. The three classes Detection DNN accepts one frontalized face input image returns 3 values summing to 100. The largest value among these 4 values will be the predicted class. 

The eyeglass detection algorithm determines if a subject is wearing eyeglasses before allowing enrollment. Eyeglasses used during enrollment lower subsequent prediction performance. The Eyeglasses On/Off Detection DNN accepts one frontalized face input image returns a value 0 to 100, where 0 is eyeglasses off and 100 is eyeglasses on. This DNN is on (true) by default during enrollment only. The URL parameter for enrollment and prediction “eyeGlassCheck=false” disables real-time instructions to the user to remove eyeglasses. 

The face mask detection algorithm determines if a subject is wearing a mask. Masks used during enrollment lower subsequent prediction performance. The Face Mask On/Off Detection DNN accepts one frontalized face input image returns a value 0 to 100, where 0 is mask off and 100 is mask on. This DNN is on (true) by default during enrollment only. The URL parameter “maskCheck=false” disables the real-time instructions to the user to remove the mask.     

### BLURRY IMAGE DETECT DNN
The Blurry Image Detection DNN accurately finds images that are extremely blurry and unable to be accurately processed by the Embedding DNN. The DNN returns a score between 0 and 100, where 100 is not blurry.  This DNN is on (true) by default during enrollment and is required to return an accurate result. The URL parameter "blurryDetect=false" disables the DNN during prediction only.  

### ACTIVE LIVENESS DNN (Spoofing Prevention)
The Eyes Open/Closed DNN provides real-time passive facial liveness.  This algorithm mitigates risk of a photo spoofing attack during unattended operation. The DNN receives an input image of an eye and outputs a validation score between 0 and 100, where 0 is eyes closed and 100 is eyes open. The user cannot proceed until the detection of a pair of eye-open/eye-closed events. A URL parameter “faceLiveness=true” allows the overriding of default functionality by enabling the eye-blink check. 

### IMAGE SPOOFING DETECTION DNN (Spoofing Prevention)
The Image Spoofing Detection DNN provides real-time passive facial liveness. This mitigates risk of a print image spoofing attack during unattended operation. The DNN receives an input image and outputs a validation score between 0 and 100, where 0 is real image and 100 is a spoof. The user cannot proceed until the detection is not a playback. This DNN is on (true) by default. The URL parameter “antiImageSpoof=false” allows the default anti-spoofing functionality to be disabled. 

### VIDEO SPOOFING DETECTION DNN (Spoofing Prevention)
The Video Spoofing Detection DNN provides real-time passive facial liveness. This mitigates risk of a video image spoofing attack during unattended operation. The DNN receives an input image and outputs a validation score between 0 and 100, where 0 is real image and 100 is a spoof. The user cannot proceed until the detection is not a playback. This DNN is on (true) by default. The URL parameter “antiVideoSpoof=false” allows the default anti-spoofing functionality to be disabled. 

### FACIAL AND FINGERPRINT DATA AUGMENTATION
Data augmentation generalizes the enrollment, improves accuracy and performance during subsequent prediction and allows the DNN to handle real-world conditions. Every enrollment requires >50 biometric input images to maintain accuracy and performance. The algorithm augments all valid input images to reach or exceed 50. The set of images are then broadened to add boundary conditions to generalize the enrollment.  The broadening includes enhanced image rotations and flips, and color and lighting homogenizations.  Augmentations must increase the distance metric (Euclidean distances or cosine similarity) but not surpass class boundaries. The algorithm removes any images that exceed class boundaries. The remaining images challenge the distance metric boundaries without surpassing them.  

If only one image is available for enrollment, the Encryption Engine will augment the frontal facial input image 60 times, remove the outliers and then enroll the user. The Web client captures 8 images, morphs each image 9 times, removes any outliers and then enrolls the user.  

Enrollment requires >50 augmented biometric input images to maintain the health, accuracy and performance of the recognition algorithm. The Encryption Engine accepts biometric input image(s), morphs and homogenizes the lighting and contrast once, and discards the original images. 

There is no intrinsic requirement to morph images for prediction.  However, we find that homogenized images perform better than non-homogenized images. Image homogenization occurs through convenience libraries in Python and JavaScript. For prediction, the Web client captures 3 images, morphs and homogenizes the lighting and contrast once, and discards the original images. 

### FACE, FACE+MASK, FINGERPRINT and VOICE EMBEDDING DNNs
* <b>FHE transforms the biometric input image </b>to a distance measurable 1-way encryption (embedding, or vector encryption) consisting of a two-dimensional positional array of 128 floating-point numbers 
* <b>Face, Face+Mask, and Fingerprint maintain full accuracy</b> through real-world boundary conditions including poor lighting; inconsistent camera positioning; expression; image rotation of up to 22.5°; variable distance; focus impacted by blur and movement; occlusions of 20-30% including facial hair, glasses, scars, makeup, colored lenses and filters, and abrasions; and B/W and grayscale images.  
* Produces (output) FHE payload in < 100ms
* MobileNetV2 architecture, 1.3MB for Face and 900kB for Fingerprint 
* FHE transforms one 2-dimensional array of frequencies (input) to a 4kB, 2-dimensional positional array of 128 floating-point numbers (Cosine-measurable embedding) 
* Produces FHE payload in < 100ms
* MobileNetV2 architecture, 3.5MB

The Face, Face+Mask, and Fingerprint Embedding DNNs FHE transform the biometric input image to a distance measurable 1-way encryption (embedding, or vector encryption) consisting of a two-dimensional positional array of 128 floating-point numbers. The Voice Embedding DNN accepts input of one 2-dimensional array of frequencies, FHE transforms the input to a 4kB, 2-dimensional positional array of 128 floating-point numbers (Cosine-measurable embedding, or 1-way vector encryption), and then deletes the original biometric. 

### VOICE (SPEAKER) IDENTIFICATION
![Voice recognition workflow](https://github.com/openinfer/PrivateIdentity/blob/master/images/Workflow%20-%20Voice.png)

### VOICE VALIDATION DNN
* <b>Validates audio input</b> for a quality human voice to discriminate between a voice and external noise
* YOLO architecture, 100kB

The Voice Validation DNN accepts a sound wave as input and returns a validation score between 0 to 100, where 100 is a perfect audio where the voice is isolated enough to create a valid embedding. 

### VOICE PULSE CODE MODULATION (PCM) TRANSFORMATION
Pulse Code Modulation lessens the input to two times the frequency range allowing for the smallest possible Fourier transform without computational loss.  

### VOICE FAST FOURIER TRANSFORMATION (FFT) 
The Voice Fast Fourier Transform (FFT) moves the pulse code modulated audio signal from the time domain to a representation in the frequency domain.  The transform output is a 2-dimensional array of frequencies that is input to the Voice Embedding DNN.

### VOICE DATA AUGMENTATION
Voice data augmentation generalizes the enrollment, improves accuracy and performance during subsequent prediction and allows the DNN to handle real-world conditions. Every enrollment requires >50 biometric voice inputs to maintain accuracy and performance. The algorithm augments all valid input audio to reach or exceed 50. The set of audio inputs is then broadened to add boundary conditions to generalize the enrollment. The broadening includes digital signal processing to emulate noise-canceling microphones, normalizing speaker distance from the microphone, and adding a variety of background noises as augmentations.  Augmentations must increase the distance metric (cosine similarity) but not surpass class boundaries. The algorithm removes any embeddings that exceed class boundaries. The remaining embeddings challenge the distance metric boundaries without surpassing them. If not enough audio is available for enrollment, the Encryption Engine will augment the audio 60 times, remove the outliers and then enroll the user.   

### VOICE EMBEDDING DNN
* FHE transforms one 2-dimensional array of frequencies (input) to a 4kB, 2-dimensional positional array of 128 floating-point numbers (Cosine-measurable embedding) 
* Produces FHE payload in < 100ms
* MobileNetV2 architecture, 3.5MB

The Voice Embedding DNN accepts input of one 2-dimensional array of frequencies, FHE transforms the input to a 4kB, 2-dimensional positional array of 128 floating-point numbers (Cosine-measurable embedding, or 1-way vector encryption), and then deletes the original biometric. 
