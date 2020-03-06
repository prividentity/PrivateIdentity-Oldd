This page list the possible web URL parameters that can be used with the application to enable or disable various functionalities.

### Demo Parameters

To enable add the URL parameters to the default URL. One or more parameters can be added by using the '&' symbol. For ex., ?voice=true&liveness=true

#### Business Functions

|URL Parameter | Possible values |Default Value|Function | 
|-----|----|---|-----|
|private.id/demo|||Enroll/Predict with face only|
|voice|true / false|false|Enroll & Predict with voice|
|liveness|true / false|false|Verify the user by validating live sentences|
|faceLiveness| true / false|false|Check for Face liveness (Eye blink) during predict / enroll|
|action|predict|No default|Prediction only Default:face can be combined with voice|
|action|enroll|No default|Enroll only Default:face can be combined with voice|
|fingerPrint|true / false|false|Prediction using Fingerprint (In Progress)|

### WebAuthN
|URL|Status|
|---|---|
|http://private.id/webauthN/|In Progress|
|https://private.id/webAuthNv2/|In Progress|