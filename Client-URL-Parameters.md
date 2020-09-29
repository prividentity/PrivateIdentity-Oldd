This page lists the possible web URL parameters that can be used with the application to enable or disable various functionalities.

The main URL is private.id/demo/

### URL Parameters

To enable a certain parameter add the URL parameters to the default URL. One or more parameters can be added by using the '&' symbol.  

For ex., ?voice=true&liveness=true, resulting in a URL that looks like, private.id/demo/?voice=true&liveness=true

#### Business Functions

|URL Parameter | Possible values |Default Value|Function | 
|-----|----|---|-----|
|action|predict / enroll|No default|Prediction only Default:face can be combined with voice: Enroll with face by default, can be combined with voice|
|antiVideoSpoof|true / false|false|Video spoofing|
|apiKey| Value of apiKey|No default|Set apiKey for requests to execute|
|attempts|Numeric value|3|Number of attempts to try prediction when action=predict|
|clientDebug|true / false|null|Debug glasses check and download images in browser.|
|client_id|string value|null|Set client ID retrieved from our endpoints.|
|debug|true / false|false|Set debug mode to help fix issues|
|email|Email ID|null|Email id for enrollment data when action=enroll|
|redirect|Domain name|null|Domain name with or without https, to redirect to after prediction|
|eyeCloseThreshold| 0 - 1|0.01|Threshold for a closed eye|
|eyeOpenThreshold| 0 - 1|0.99|Threshold for an open eye|
|faceLiveness| true / false|false|Check for Face liveness (Eye blink) during predict / enroll [[1](https://github.com/openinfer/PrivateIdentity/wiki/Client-URL-Parameters#reference)]|
|face| true / false|true|Enroll & predict with face|
|fingerPrint|true / false|false|Prediction using Fingerprint (In Progress)|
|glassCheck|true / false|false|Turn glasses check on predict/enroll to on/off|
|hslType|1 / 2|2|Normalization algorithm used. 1 for HSL, 2 for CLAHE|
|idp|okta / ping / azure/ gsuite|null|Set SAML destination|
|isEdge|true / false|false|Imitate Edge browser experience|
|liveness|true / false|false|Verify the user by validating live sentences|
|livenessImages| 1 or more images|10|Number of images to gather on face liveness|
|livenessMSInterval| Time in millisecond |190|Time interval between each image gather on face liveness|
|localMode|true / false|false|Local mode to [work offline](https://github.com/openinfer/PrivateIdentity/wiki/Client-URL-Parameters#offline-web-client-biometric-acquisition-local-mode)|
|oauthScope|Scope value|null|Set scope value for oAuth|
|oauthState|oAuth State|null|Set state value for oAuth|
|okta|true / false|false|Use Okta as an SP|
|oktaDomain|Okta domain without https://|null|Okta domain for SAML implementation|
|redirect|link to redirect to|null|Redirection link after processing.|
|redirect_uri|String value for a link|null|Set redirect URL for oAuth|
|RelayState| Link for SAML Relay state|null||
|responseType|string value|null|Set response type for oAuth|
|role_id|Numeric value|null|User role ID to update|
|SAMLRequest| Encoded XML|null|Encoded XML request|
|sessionid|Session ID|null|Set session ID for oAuth|
|showPermissionDialog|true / false|false|Show permission dialog on oAuth|
|subject_id|Subject ID in numbers|null|Set subject ID of user|
|tag|String value|null|Tag to update for a user|
|token|String value|null|Set token value|
|value|Numeric value|null|Value for user tag we want to update|
|voice|true / false|false|Enroll & Predict with voice|
|whereToProcess|browser / nodeServer|browser|Set the processing destination.|
|antiVideoSpoof|true / false|false|Check the webcam capture is a spoofed one or not. [[1](https://github.com/openinfer/PrivateIdentity/wiki/Client-URL-Parameters#reference)]|
|profileFaceEnroll|true / false|false|Face enroll with profile images.|
|faceMask|true / false|true|Use face mask embedding model.|
### WebAuthN
|URL|Status|
|---|---|
|http://private.id/webauthN/|In Progress|
|https://private.id/webAuthNv2/|In Progress|

## Offline Web Client Biometric Acquisition (Local Mode)
* Private Identity MFA Web client acquires biometrics at the edge with or without a network 
* Web client automatically switches to Local Mode after it detects loss of network 

The Web client supports offline operation (“Local Mode”) using Edge computing. The device in Local Mode authenticates a user using face and fingerprint recognition in 10ms with intermittent or no Internet connection as long as the user authenticates at least once to the device while online. The device stores the user’s FHE (embeddings) locally using the Web Storage API during the first prediction. The client automatically detects the loss of network connectivity. The URL parameter “localMode=true” directs the Web client to use the offline embedding store to authenticate.

#### Reference:
1. To know more about the video spoofing identification technique, please refer the [Anti-Spoofing](https://github.com/openinfer/PrivateIdentity/wiki/Demo-Parameter-Usage#anti-spoofing-technique) documentation