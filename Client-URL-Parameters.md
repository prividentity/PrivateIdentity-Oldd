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
|redirect|link to redirect to|null|Redirection link after processing.|
|idp|okta / azure/ gsuite|null|Set SAML destination|
|client_id|string value|null|Set client ID retrieved from our endpoints.|
|responseType|string value|null|Set response type for oAuth|
|redirect_uri|String value for a link|null|Set redirect URL for oAuth|
|sessionid|Session ID|null|Set session ID for oAuth|
|oauthState|oAuth State|null|Set state value for oAuth|
|oauthScope|Scope value|null|Set scope value for oAuth|
|subject_id|Subject ID in numbers|null|Set subject ID of user|
|isEdge|True / false|false|Imitate Edge browser experience|
|antiVideoSpoof|True / false|false|Video spoofing|
|eyeOpenThreshold| 0 - 1|0.99|Threshold for an open eye|
|eyeCloseThreshold| 0 - 1|0.01|Threshold for a closed eye|
|RelayState| Link for SAML Relay state|null||
|samlRequest| Encoded XML|null|Encoded XML request|
|eyeCloseThreshold| 0 - 1|0.01|Threshold for a closed eye|
|okta|True / false|false|Use Okta as an SP|
|hslType|1 / 2|2|Normalization algorithm used. 1 for HSL, 2 for CLAHE|
|clientDebug|True / false|null|Debug glasses check and download images in browser.|
|showPermissionDialog|True / false|false|Show permission dialog on oAuth|
|role_id|Numeric value|null|User role ID to update|
|tag|Numeric value|null|Tag to update for a user|
|value|Numeric value|null|Value for user tag we want to update|



### WebAuthN
|URL|Status|
|---|---|
|http://private.id/webauthN/|In Progress|
|https://private.id/webAuthNv2/|In Progress|