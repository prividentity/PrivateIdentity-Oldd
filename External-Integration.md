In this section, we will have an overview of how PrivateIdentity has configured as an Identity Provider for some of the leading secure identity management (IM) providers.

Integration with external IM providers can be achieved in a lot of ways. Security Assertion Markup Language (SAML) 2.0 is one of the widely used techniques used for authentication. A general overview of the flow is explained in the link [SAML 2.0](https://github.com/openinfer/PrivateIdentity/wiki/SAML-2.0)

There are two parties involved in the process:

* Service Provider (SP) - one who facilitates the IM by using APIs
* Identity Provider (IP) - one who authenticates the user based on the available modalities.

Workflow used for the SAML authentication in case of Okta/ping:

1. Applications that require IM can be integrated into the Okta Dashboard / Ping Services (SP).
2. IP, in our case Private Identity, setup is configured in Okta / Ping services by setting up the URL and certificates.
3. Modality to be used can be configured via the URL.
4. When authentication is requested via applications configured, a SAML Request will be sent to the private id with the parameters embedded.
5. Upon receiving the request, the application validates the request and use the modality to identify the user (Private Identity provides face and voice currently) for building the response.
6. A SAML response will be sent as a post request to the requester with the user details requested by the SP by signing the response with the Identity provider's private key.
7. SP reads the response, validating the signature with the public key, and extracts the user information sent from IP.
8. If the user information matches with the SP configuration, the user is authenticated successfully and allowed for login.

## Okta
<br/>
Okta, Inc. is a publicly-traded identity and access management company based in San Francisco. It provides cloud software that helps companies manage and secure user authentication into modern applications, and for developers to build identity controls into applications, website web services, and devices.   

Okta provides authentication services across many identity management firms. In our case, we have used Okta as an SP while using private identity services as an IP. This is achieved by handshaking the SAML authentication during the verification process between Okta and Private Identity.

Okta currently verifies the user through email ID, so the SAML response <Subject.Name.Id> should contain the email from the IP.

The following screenshots show a sample demonstration of authentication done with face modality.

1. Logging into okta as a service provider [Sample URL](https://private.okta.com).

![Okta Login](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_login.png)

2. Okta uses a multi-factor authentication followed by a password prompt, redirecting the user to IP authentication.

![Okta Multi Factor](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_multi_factor.png)

3. The user gets authenticated by the requested modality e.g., face and if the user is authenticated successfully a success response will be sent to SP.

![IP Face Modality](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_IP_predict.png)

4. If the user gets authenticated successfully, the user will be redirected to the successful login page.

![Okta Success](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_success.png)

## Ping Identity
<br/>
PingFederate is an enterprise federation server that enables user authentication and single sign-on. It serves as a global authentication authority that allows employees, customers, and partners to securely access all the applications they need from any device.

Ping Identity currently verifies the user via Active Directory, so the SAML response <Subject.Name.Id> should contain the UUID from the IP.

Ping Identity can differentiate between successful and unsuccessful attempts. Currently, the modality that has been configured with face, voice, and face & voice.

Ping Identity provides the subject name in the SAML Request which expects to be sent back in the SAML response. If the user is not found on predict it will proceed with the enroll flow to register the user in the Active directory.

The following screenshots show a sample demonstration of authentication done with face modality.

1. Logging into the dropbox application as a service provider [Sample URL](https://www.dropbox.com/sso/7879772650).
2. Ping Identity redirects the user to IP authentication.
![Ping Predict](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_predict.png)

3. The user gets authenticated by the requested modality e.g., face and if the user is authenticated successfully a success response will be sent to SP.
4. If the user gets authenticated successfully, the user will be redirected to the successful login page.
![Ping Success](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_success.png)

5. If the user does not get authenticated, Ping identity redirects it to the enroll flow followed by active directory authentication.
![Ping Enroll flow](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_enroll.png)

6.  Upon successful enroll the user details are updated in the active directory. The authentication followed by that would work on successful prediction.
![Ping Success](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_success.png)