This page list the possible web URL parameters that can be used with the application to enable or disable various functionalities.

### Demo Parameters

To enable add the URL parameters to the default URL. One or more parameters can be added by using the '&' symbol. For ex., ?voice=true&debug=true

#### Business Functions

|URL Parameter | Possible values |Default Value|Function | 
|-----|----|---|-----|
|private.id/demo|||Enroll/Predict with face only|
|voice|true / false|false|Enroll & Predict with voice|
|liveness|true / false|false|Verify the user by validating live sentences|
|faceLiveness| true / false|false|Check for Face liveness (Eye blink) during predict / enroll|
|apiKey| Value of apiKey|No default|Set apiKey for requests to execute|
|action|predict|No default|Prediction only Default:face can be combined with voice|
|action|enroll|No default|Enroll only Default:face can be combined with voice|
|fingerPrint|true / false|false|Prediction using Fingerprint (In Progress)|

#### Admin Functions

|URL Parameter | Possible values |Default Value|Function | 
|-----|----|---|-----|
|glassCheck|true / false|false|Disables the glass check|
|hlsType|1 / 2|2|1: Histogram Equalization 2:CLAHE method|
|action|deleteSubject|No default|Delete the subject from the system combined with subject_id|
|action|addRole|No default|Add role values to the system combined with tag and value|
|action|deleteRole|No default|Delete role values from the system combined with role_id|
|action|addRoletoSubject|No default|Add role and subject to the system combined with role_id and subject_id|
|action|deleteRolefromSubject|No default|Delete role and subject from the system combined with role_id and subject_id|
|subject_id|subject Id in the system|No default|Subject id in the URL parameter|
|tag|tag string|No default|Tag string to add role to the system|
|value|value string|No default|Value string to add role to the system|
|role_id|role Id in the system|No default|Role id to delete role or add/delete role to the subject|
|whereToProcess|nodeServer / browser |browser|Routing the computation to the node|

#### Debug Functions

|URL Parameter | Possible values |Default Value|Function | 
|-----|----|---|-----|
|debug|true / false|false|Enable debug messages in the page and console|
|clientDebug|true / false|false|Enable more debug messages in the page and console|

### Reset Server

http://devel.privatebiometrics.com/resetServer

### WebAuthN
|URL|Status|
|---|---|
|http://private.id/webauthN/|In Progress|
|https://private.id/webAuthNv2/|In Progress|