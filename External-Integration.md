In this section, we will have an overview of how PrivateIdentity has configured as an Identity Provider for some of the leading secure identity management (IM) providers.

Integration with external IM providers can be achieved in lot of ways. Security Assertion Markup Language (SAML) 2.0 is one of the widely used techniques used for authentication. A general overview of the flow is explained in the link [SAML 2.0](https://github.com/openinfer/PrivateIdentity/wiki/SAML-2.0)

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


## Ping
<br/>