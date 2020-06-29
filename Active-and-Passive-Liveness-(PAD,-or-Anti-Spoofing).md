1. Eye Blink
2. Photo
3. Video 
4. Voice

# Eye Blink Detect DNN
The Eyes Open/Closed DN provides real-time passive facial liveness. This algorithm mitigates risk of a photo spoofing attack during unattended operation by ensuring that the video input contains a person who is blinking.  The eye blink detect capability is built with two models.  The first, the Eye Geometry Detect DNN, accurately locates eye(s) in an image and returns X,Y coordinates. The Eyes Open/Closed Detection DNN receives an input image of an eye and outputs a validation score between 0 and 100, where 0 is eyes closed and 100 is eyes open

## EYE GEOMETRY DETECT DNN
The Eye Geometry Detection DNN accurately locates eye(s) in an image by transforming each frontal facial image into geometric primitives and measuring relative position. The DNN returns X,Y coordinates of each eye in an image, video frame or video stream.  

## EYES OPEN/CLOSED DETECTION DNN (Photo Spoofing Prevention)
The Eyes Open/Closed DN provides real-time passive facial liveness. This algorithm mitigates risk of a photo spoofing attack during unattended operation. The DNN receives an input image of an eye and outputs a validation score between 0 and 100, where 0 is eyes closed and 100 is eyes open. The user cannot proceed until the detection of a pair of eye-open/eye-closed events. A URL parameter “faceLiveness=true” allows the overriding of default functionality by enabling the eye-blink check. 

## IMPLEMENTATION
To enable Eye Blink Liveness of the user, either add the URL parameter **faceLiveness=true**.

Sample Demonstration of Eyeblink success:
![Eye Blink Demo](https://github.com/openinfer/PrivateIdentity/blob/master/images/eye_blink_demo.png)

Eye Blink Demo
