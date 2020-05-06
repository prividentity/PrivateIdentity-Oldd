This page lists the possible web URL parameters that can be used with the application to enable or disable various functionalities.

The main URL is private.id/demo/

### URL Parameters

To enable a certain parameter add the URL parameters to the default URL. One or more parameters can be added by using the '&' symbol.  

For ex., ?voice=true&liveness=true, resulting in a URL that looks like, private.id/demo/?voice=true&liveness=true

#### Business Functions

|URL Parameter | Possible values |Default Value|Function | 
|-----|----|---|-----|
|action|predict / enroll|No default|Prediction only Default:face can be combined with voice: Enroll with face by default, can be combined with voice|
|antiVideoSpoof|True / false|false|Video spoofing|
|apiKey| Value of apiKey|No default|Set apiKey for requests to execute|
|attempts|Numeric value|3|Number of attempts to try prediction when action=predict|
|clientDebug|True / false|null|Debug glasses check and download images in browser.|
|client_id|string value|null|Set client ID retrieved from our endpoints.|
|debug|true / false|false|Set debug mode to help fix issues|
|email|Email ID|null|Email id for PII data when action=enroll|
|eyeCloseThreshold| 0 - 1|0.01|Threshold for a closed eye|
|eyeOpenThreshold| 0 - 1|0.99|Threshold for an open eye|
|faceLiveness| true / false|false|Check for Face liveness (Eye blink) during predict / enroll|
|face| true / false|True|Enroll & predict with face|
|fingerPrint|true / false|false|Prediction using Fingerprint (In Progress)|
|glassCheck|true / false|false|Turn glasses check on predict/enroll to on/off|
|hslType|1 / 2|2|Normalization algorithm used. 1 for HSL, 2 for CLAHE|
|idp|okta / ping / azure/ gsuite|null|Set SAML destination|
|isEdge|True / false|false|Imitate Edge browser experience|
|liveness|true / false|false|Verify the user by validating live sentences|
|livenessImages| 1 or more images|10|Number of images to gather on face liveness|
|livenessMSInterval| Time in millisecond |190|Time interval between each image gather on face liveness|
|localMode|true / false|false|Local mode to work offline.|
|oktaDomain|Okta domain without https://|null|Okta domain for SAML implementation|

|whereToProcess|browser / nodeServer|browser|Set the processing destination.|


|token|String value|null|Set token value|
|redirect|link to redirect to|null|Redirection link after processing.|

|responseType|string value|null|Set response type for oAuth|
|redirect_uri|String value for a link|null|Set redirect URL for oAuth|
|sessionid|Session ID|null|Set session ID for oAuth|
|oauthState|oAuth State|null|Set state value for oAuth|

|subject_id|Subject ID in numbers|null|Set subject ID of user|

|RelayState| Link for SAML Relay state|null||
|SAMLRequest| Encoded XML|null|Encoded XML request|
|okta|True / false|false|Use Okta as an SP|

|showPermissionDialog|True / false|false|Show permission dialog on oAuth|
|role_id|Numeric value|null|User role ID to update|
|tag|String value|null|Tag to update for a user|
|value|Numeric value|null|Value for user tag we want to update|
|voice|true / false|false|Enroll & Predict with voice|


### WebAuthN
|URL|Status|
|---|---|
|http://private.id/webauthN/|In Progress|
|https://private.id/webAuthNv2/|In Progress|