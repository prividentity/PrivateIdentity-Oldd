This page list the possible web URL parameters that can be used with the application to enable or disable various functionalities.

### Demo Parameters

To enable add the URL parameters to the default URL. One or more parameters can be added by using the '&' symbol. For ex., ?voice=true&liveness=true

#### Business Functions

|URL Parameter | Possible values |Default Value|Function | 
|-----|----|---|-----|
|private.id/demo|||Enroll/Predict with face only|
|voice|true / false|false|Enroll & Predict with voice|
|face| true / false|True|Enroll & predict with face|
|liveness|true / false|false|Verify the user by validating live sentences|
|faceLiveness| true / false|false|Check for Face liveness (Eye blink) during predict / enroll|
|action|predict|No default|Prediction only Default:face can be combined with voice|
|action|enroll|No default|Enroll only Default:face can be combined with voice|
|apiKey| Value of apiKey|No default|Set apiKey for requests to execute|
|fingerPrint|true / false|false|Prediction using Fingerprint (In Progress)|
|debug|true / false|false|Set debug mode to help fix issues|
|glassCheck|true / false|false|Turn glasses check on predict/enroll to on/off|
|livenessImages| 1 or more images|10|Number of images to gather on face liveness|
|livenessMSInterval| Time in millisecond |190|Time interval between each image gather on face liveness|
|whereToProcess|browser / nodeServer|browser|Set the processing destination.|
|oktaDomain|Okta domain without https://|null|Okta domain for SAML implementation|
|localMode|true / false|false|Local mode to work offline.|
|token|String value|null|Set token value|
|debug|true / false|false|Set debug mode to help fix issues|


### WebAuthN
|URL|Status|
|---|---|
|http://private.id/webauthN/|In Progress|
|https://private.id/webAuthNv2/|In Progress|