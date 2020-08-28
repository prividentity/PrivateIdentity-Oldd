## GEOMETRY DETECTION, VALIDATION AND EMBEDDING DNNs

![Facial Recognition Workflow](https://github.com/openinfer/PrivateIdentity/blob/master/images/Workflow%20-%20Face.png)

![Fingerprint recognition workflow](https://github.com/openinfer/PrivateIdentity/blob/master/images/Workflow%20-%20Fingerprint.png)
### FACE, FACE w/MASK and FINGERPRINT RECOGNITION

### Face and Face w/Mask Geometry Detection DNN
The Face Geometry Detection DNN accurately locates face(s) in an image by transforming each image into geometric primitives and measuring the relative position, width, and other parameters of eyes, mouth(s), nose(s), and chin(s). Likewise, the Fingerprint Geometry Detection DNN accurately locates finger(s) in an image by transforming each image into geometric primitives and measuring each finger’s relative position, width, and other parameters.  

Each DNN returns X and Y coordinates of each modality in an image, video frame or video stream. 

### FACE & FINGERPRINT VALIDATION DNNs
The Face Validation DNN tightly aligns, crops and accurately validates each frontalized face input image. Likewise, the Fingerprint Validation DNN tightly aligns, crops and accurately validates each fingerprint input image. Each DNN returns a validation score between 0 to 100, where 100 is a perfect image.  

### FACE+MASK ON/OFF DETECTION DNN

The face mask detection algorithm determines if a subject is wearing a mask.  Masks used during enrollment lower subsequent prediction performance. The Face+Mask On/Off Detection DNN accepts one frontalized face input image returns a value 0 to 100, where 0 is mask off and 100 is mask on. The URL parameter for enrollment and prediction “maskCheck=true” provides real-time instructions to the user to remove the mask or can be set to automatically select the Face+Mask Embedding DNN.     

### EYEGLASSES ON/OFF DETECTION DNN
The eyeglass detection algorithm determines if a subject is wearing eyeglasses before allowing enrollment. Eyeglasses used during enrollment lower subsequent prediction performance. The Eyeglasses On/Off Detection DNN accepts one frontalized face input image returns a value 0 to 100, where 0 is eyeglasses off and 100 is eyeglasses on. The URL parameter for enrollment and prediction “eyeGlassCheck=true” provides real-time instructions to the user to remove eyeglasses.  

### 4 CLASSES (GOOD, BLURRY, EYEGLASSES, FACE+MASK) DETECTION DNN
The 4 classes detection algorithm determines if a subject is in good quality, blurry, wearing eyeglasses or wearing facemask.  Blurry images, wearing eyeglasses or facemask during enrollment lower subsequent prediction performance. The 4 Classes Detection DNN accepts one frontalized face input image returns 4 values summing to 100. The largest value among these 4 values will be the predicted class.   

### EYE GEOMETRY DETECT DNN
The Eye Geometry Detection DNN accurately locates eye(s) in an image by transforming each frontal facial image into geometric primitives and measuring relative position. The DNN returns X,Y coordinates of each eye in an image, video frame or video stream.  

### EYES OPEN/CLOSED DETECTION DNN (Spoofing Prevention)
The Eyes Open/Closed DNN provides real-time passive facial liveness.  This algorithm mitigates risk of a photo spoofing attack during unattended operation. The DNN receives an input image of an eye and outputs a validation score between 0 and 100, where 0 is eyes closed and 100 is eyes open. The user cannot proceed until the detection of a pair of eye-open/eye-closed events. A URL parameter “faceLiveness=true” allows the overriding of default functionality by enabling the eye-blink check. 

### VIDEO AND IMAGE SPOOFING DETECTION DNN (Spoofing Prevention)
The Video ad Image Spoofing Detection DNN provides real-time passive facial liveness. This algorithm mitigates risk of a video or print image spoofing attack during unattended operation. The DNN receives an input image and outputs a validation score between 0 and 100, where 0 is real image and 100 is spoof video or print image. The user cannot proceed until the detection of images are real. A URL parameter “antiVideoSpoof=true” allows the overriding of default functionality by enabling video and image spoofing check. 

### FACIAL AND FINGERPRINT DATA AUGMENTATION
Data augmentation generalizes the enrollment, improves accuracy and performance during subsequent prediction and allows the DNN to handle real-world conditions. Every enrollment requires >50 biometric input images to maintain accuracy and performance. The algorithm augments all valid input images to reach or exceed 50. The set of images are then broadened to add boundary conditions to generalize the enrollment.  The broadening includes enhanced image rotations and flips, and color and lighting homogenizations.  Augmentations must increase the distance metric (Euclidean distances or cosine similarity) but not surpass class boundaries. The algorithm removes any images that exceed class boundaries. The remaining images challenge the distance metric boundaries without surpassing them.  

If only one image is available for enrollment, the Encryption Engine will augment the frontal facial input image 60 times, remove the outliers and then enroll the user. The Web client captures 8 images, morphs each image 9 times, removes any outliers and then enrolls the user.  

Enrollment requires >50 augmented biometric input images to maintain the health, accuracy and performance of the recognition algorithm. The Encryption Engine accepts biometric input image(s), morphs and homogenizes the lighting and contrast once, and discards the original images. 

There is no intrinsic requirement to morph images for prediction.  However, we find that homogenized images perform better than non-homogenized images. Image homogenization occurs through convenience libraries in Python and JavaScript. For prediction, the Web client captures 3 images, morphs and homogenizes the lighting and contrast once, and discards the original images. 

### FACE, FACE+MASK, AND FINGERPRINT EMBEDDING DNNs
The Face, Face+Mask, and Fingerprint Embedding DNNs FHE transform the biometric input image to a distance measurable 1-way encryption (embedding, or vector encryption) consisting of a two-dimensional positional array of 128 floating-point numbers. 

The Face, Face+Mask, and Fingerprint Embedding DNNs maintain full accuracy through real-world boundary conditions including poor lighting; inconsistent camera positioning; expression; image rotation of up to 22.5°; variable distance; focus impacted by blur and movement; occlusions of 20-30% including facial hair, glasses, scars, makeup, colored lenses and filters, and abrasions; and B/W and grayscale images.  The embedding DNNs use the MobileNetV2 architecture and output a 1-way encrypted payload in <100ms. 

### VOICE (SPEAKER) IDENTIFICATION
![Voice recognition workflow](https://github.com/openinfer/PrivateIdentity/blob/master/images/Workflow%20-%20Voice.png)
### VOICE INPUT SEGMENTATION 
Voice Input Segmentation generalizes the enrollment, improves accuracy and performance during prediction, and allows the DNN to handle real-world conditions. Every enrollment requires >50 10ms voice samples to maintain accuracy and performance. The algorithm uses a sliding 10ms window across one second of input to reach or exceed 50 samples. 

### VOICE PULSE CODE MODULATION (PCM) TRANSFORMATION
Pulse Code Modulation lessens the input to two times the frequency range allowing for the smallest possible Fourier transform without computational loss.  

### VOICE FAST FOURIER TRANSFORMATION (FFT) 
The Voice Fast Fourier Transform (FFT) moves the pulse code modulated audio signal from the time domain to a representation in the frequency domain.  The transform output is a 2-dimensional array of frequencies that is input to the Voice Embedding DNN.

## VOICE EMBEDDING DNN
The Voice Embedding DNN accepts input of one 2-dimensional array of frequencies, FHE transforms the input to a 4kB, 2-dimensional positional array of 128 floating-point numbers (Cosine-measurable embedding, or 1-way vector encryption), and then deletes the original biometric. 
