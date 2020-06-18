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

Steps to setup Private Identity as IDP in Okta:

1. Log in to Okta as Admin
2. Go to Security -> Identity Providers

![Okta Setup 1](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_1.png)

3. Click on "Add Identity Provider" and Choose "Add SAML 2.0 IdP"

![Okta Setup 2](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_2.png)

4. Fill in the parameters required. The Desired IDP name can be chosen for readability. Choose IdP Usage as Factory only. Fill in the IdP Issuer URI. Currently, the setup is configured with [Private ID](https://devel.private.id). IdP Single Sign-On URL will have the URL for the desired modality authentication. 

Please find the setup parameters:

**IdP Issuer URI:**   
`private.id`

**IdP Single Sign-On URL:**   
`https://private.id/a/?idp=okta&apiKey=<insert_api_here>&action=unknown`

**IdP Signature Certificate:**   
Download the certificate using the below link.   
Right click and save link as [Certificate](https://github.com/openinfer/PrivateIdentity/blob/master/certificate/certificate.pem)   
Upload the downloaded signature to the Okta configuration.

![Okta Setup 3](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_3.png)

5. Click on Advanced Settings. Change the Request Binding to HTTP Redirect. The destination has to be replaced with the same URL as that of IdP Single Sign-On URL. The signature algorithm has to be SHA-256. The remaining parameters can be modified according to the user's needs. Save the configuration

![Okta Setup 4](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_4.png)

6. Go to Security -> Multifactor -> Factor Types.

![Okta Setup 5](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_5.png)

7. Choose the IdP Factor for selecting the configured IdP.

![Okta Setup 6](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_6.png)

8. Click edit and select the desired IdP and save the configuration.

![Okta Setup 7](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_7.png)

9. Go to Security -> Multifactor -> Factor Enrollment.

![Okta Setup 8](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_8.png)

10. Click on Add Multifactor Policy and fill in the required details. Give a policy name, description, assign the groups to everyone, and choose the effective factor as required. Save the policy.

![Okta Setup 9](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_9.png)

11. Go to Security -> Authentication -> Sign On.

![Okta Setup 10](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_10.png)

12. Click on Add Rule to configure a Multifactor rule so that the user will be prompted for multi-factor authentication.

![Okta Setup 11](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_11.png)

13. Keep the default values or change as needed. Check the Prompt for Factor option to enable the rule. Save the configuration.

![Okta Setup 12](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_12.png)

Once the setup is complete and when the user attempts to log in next time into the SP, the factor prompt will be asked for the user for completing the authentication.

Sample SAML Request:

    <saml2p:AuthnRequest xmlns:saml2p="urn:oasis:names:tc:SAML:2.0:protocol"
                         AssertionConsumerServiceURL="https://private.okta.com/sso/saml2/0oa94pj0sb1x1SPAz4x6"
                         Destination="https://devel.private.id/demo/?idp=okta&apiKey=1962&oktaDomain=private.okta.com"
                         ForceAuthn="false"
                         ID="id216400685678752324916391"
                         IssueInstant="2020-05-20T10:17:46.623Z"
                         Version="2.0"
                         >
        <saml2:Issuer xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">https://www.okta.com/saml2/service-provider/spaalgnibujvpmqvrkav</saml2:Issuer>
        <saml2:Subject xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">
            <saml2:NameID>srie@private.id</saml2:NameID>
        </saml2:Subject>
        <saml2p:NameIDPolicy Format="urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified" />
    </saml2p:AuthnRequest>

Sample SAML Response:

    <saml2p:Response xmlns:saml2p="urn:oasis:names:tc:SAML:2.0:protocol"
                     xmlns:xs="http://www.w3.org/2001/XMLSchema"
                     Destination="https://private.okta.com/sso/saml2/0oa94pj0sb1x1SPAz4x6"
                     ID="hiOK90fGDyytFSeznaoZZPTbnOrGBL6n"
                     InResponseTo="id216400685678752324916391"
                     IssueInstant="2020-05-20T10:17:56Z"
                     Version="2.0"
                     >
        <saml2:Issuer xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion"
                      Format="urn:oasis:names:tc:SAML:2.0:nameid-format:entity"
                      >https://devel.private.id/</saml2:Issuer>
        <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
            <ds:SignedInfo>
                <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />
                <ds:SignatureMethod Algorithm="http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" />
                <ds:Reference URI="#hiOK90fGDyytFSeznaoZZPTbnOrGBL6n">
                    <ds:Transforms>
                        <ds:Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
                        <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />
                    </ds:Transforms>
                    <ds:DigestMethod Algorithm="http://www.w3.org/2001/04/xmlenc#sha256" />
                    <ds:DigestValue>H88oDJ9ullvDAWklOaK/6VRgwtK/0cPhg6wY8CVSV0Y=</ds:DigestValue>
                </ds:Reference>
            </ds:SignedInfo>
            <ds:SignatureValue>O9VEu38CuZdgo20iGRZrvll/Bmuo41nINULgLmWkGsWHqHnXbojwCENBtF4rhhxDZ+Mf6vmVymGy9XLBQM/i07Id0HIajKr90Do3sDDI1FKaCIZ8KpeNd2tM3q2jT1zKLCotEy/KNby5t2+QEdGA5/pe1UuLVAQ1YZcA//GkqRNUrjROtsVjXu57EA9wPqD8LJppW2zL8+zzaRhJxlIOtpHXE26PP4AZ4ol5fpn1VSdiU92+X9yJL5g6jZ2dnWHzUBK1mXMD8emj7k/GD+oJYHWHC4KSS9L2HzL3hHKixuPtYR82DyzqF/MVaign4aP/5vDvOH/o1udMwedX/fmA6w==</ds:SignatureValue>
            <ds:KeyInfo>
                <ds:X509Data>
                    <ds:X509Certificate>MIIEGzCCAwOgAwIBAgIUa7n6jLeipmjyhazU9qzZoMZ8bkAwDQYJKoZIhvcNAQELBQAwgZwxCzAJBgNVBAYTAlVTMQswCQYDVQQIDAJNRDERMA8GA1UEBwwIV29vZGJpbmUxHjAcBgNVBAoMFVByaXZhdGUgSWRlbnRpdHksIExMQzERMA8GA1UECwwISWRlbnRpdHkxGTAXBgNVBAMMEFByaXZhdGUgSWRlbnRpdHkxHzAdBgkqhkiG9w0BCQEWEHNjb3R0QHByaXZhdGUuaWQwHhcNMTkxMjExMjEwOTIyWhcNNDcwNDI4MjEwOTIyWjCBnDELMAkGA1UEBhMCVVMxCzAJBgNVBAgMAk1EMREwDwYDVQQHDAhXb29kYmluZTEeMBwGA1UECgwVUHJpdmF0ZSBJZGVudGl0eSwgTExDMREwDwYDVQQLDAhJZGVudGl0eTEZMBcGA1UEAwwQUHJpdmF0ZSBJZGVudGl0eTEfMB0GCSqGSIb3DQEJARYQc2NvdHRAcHJpdmF0ZS5pZDCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALJ1/2ij1PxRi7ZzaeWmUM1WZpsSHUSXGjUyvMWoffZaa4F+9HZvqIlIXP5Te/LMLMnwEQ2dHOMlBAKaMpLFgaQxK630/bx6rPWyBEtfpHGl0GcHkotAXyj46Bz/OHfaQjpGFirZIUM2idR7B7BatUYqLbOzC3JCKvgoD0rnqJX10+qLlKAFSmXn8V5nbpo5a/4mjzHtLYhjJ3cAgbkOSQLYUKcF7i7zQForXRJZCD4mtNs466ptl7uoBy90uolJraMRYxucUoNiLk8rCqRUxOU4bv/SocYjDM/Y/p2EArm1wCcBJH/vJEjCRNlx2ZJBC/UA3P0oQBUuD0OdL41ey58CAwEAAaNTMFEwHQYDVR0OBBYEFABwapu2N0QxKZcf5Cp6G6z24bccMB8GA1UdIwQYMBaAFABwapu2N0QxKZcf5Cp6G6z24bccMA8GA1UdEwEB/wQFMAMBAf8wDQYJKoZIhvcNAQELBQADggEBAHD5YMTBCdVqdVZFCwjX716OUAtm3iJkPBXlYELJcbNWKr4dOisBeJtwNI0+NsSwIPKX885wW2NB/5POcWRDruQbyYDMI8FWp1ia+n05a/lpynJ1tw1UbcuFrbnMrgCsA0mxUfewW2pc8i/VF94rxl3VXOPMAhZTU4pWLUfof5oG+szzRqB80QPsSotfViavrULwQVvOo+OfAgQeaTeIUiuDwSzG5DDqrrWs3mi3j6DsNh76bZ/1TKTjB8U8z2H/vAbskzhWTpDQk+uRy+v4ZiTYOCDvBNEDZ9DQbuhziF2XiSwkctW61zuXC5I2+8kty0nmEWh/Kv/rQMT6MTVpMGA=</ds:X509Certificate>
                </ds:X509Data>
            </ds:KeyInfo>
        </ds:Signature>
        <saml2p:Status xmlns:saml2p="urn:oasis:names:tc:SAML:2.0:protocol">
            <saml2p:StatusCode Value="urn:oasis:names:tc:SAML:2.0:status:Success" />
        </saml2p:Status>
        <saml2:Assertion xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion"
                         xmlns:xs="http://www.w3.org/2001/XMLSchema"
                         ID="3RJXI6T14UGUOYiSw2BbraTWK38UqwcA"
                         IssueInstant="2020-05-20T10:17:56Z"
                         Version="2.0"
                         >
            <saml2:Issuer xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion"
                          Format="urn:oasis:names:tc:SAML:2.0:nameid-format:entity"
                          >https://devel.private.id/</saml2:Issuer>
            <saml2:Subject xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">
                <saml2:NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified">srie@private.id</saml2:NameID>
                <saml2:SubjectConfirmation Method="urn:oasis:names:tc:SAML:2.0:cm:bearer">
                    <saml2:SubjectConfirmationData InResponseTo="id216400685678752324916391"
                                                   NotOnOrAfter="2020-05-20T10:22:56Z"
                                                   Recipient="https://private.okta.com/sso/saml2/0oa94pj0sb1x1SPAz4x6"
                                                   />
                </saml2:SubjectConfirmation>
            </saml2:Subject>
            <saml2:Conditions xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion"
                              NotBefore="2020-05-20T10:15:56Z"
                              NotOnOrAfter="2020-05-20T10:22:56Z"
                              >
                <saml2:AudienceRestriction>
                    <saml2:Audience>https://www.okta.com/saml2/service-provider/spaalgnibujvpmqvrkav</saml2:Audience>
                </saml2:AudienceRestriction>
            </saml2:Conditions>
            <saml2:AuthnStatement xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion"
                                  AuthnInstant="2020-05-20T10:17:56Z"
                                  SessionIndex="3RJXI6T14UGUOYiSw2BbraTWK38UqwcA"
                                  >
                <saml2:AuthnContext>
                    <saml2:AuthnContextClassRef>urn:oasis:names:tc:SAML:2.0:ac:classes:PasswordProtectedTransport</saml2:AuthnContextClassRef>
                </saml2:AuthnContext>
            </saml2:AuthnStatement>
            <saml2:AttributeStatement xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">
                <saml2:Attribute Name="Email"
                                 NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:unspecified"
                                 >
                    <saml2:AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
                                          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                                          xsi:type="xs:string"
                                          >srie@private.id</saml2:AttributeValue>
                </saml2:Attribute>
                <saml2:Attribute Name="GUID"
                                 NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:unspecified"
                                 >
                    <saml2:AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
                                          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                                          xsi:type="xs:string"
                                          >9f371fa2ce0a9b593b6f</saml2:AttributeValue>
                </saml2:Attribute>
            </saml2:AttributeStatement>
        </saml2:Assertion>
    </saml2p:Response>

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

Steps to setup Private Identity as IDP in Ping Identity:

1. Log in to the Ping Federate server and choose Service Provider. Click Create New to create a new IdP connection.

![Ping Setup 1](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_1.png)

2. Choose the connection type as Browser SSO profiles SAML 2.0. Click next

![Ping Setup 2](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_2.png)

3. Leave the Default configuration of Browser SSO. Click Next.

![Ping Setup 3](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_3.png)

4. Choose Metadata as None and click next.

![Ping Setup 4](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_4.png)

5. In the General Info screen, fill the desired name in entity ID e.g., privateid.face with the connection name. Click next.

![Ping Setup 5](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_5.png)

6. Click on Configure Browser SSO.

![Ping Setup 6](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_6.png)

7. In the SAML Profiles section, check the SP Initiated SSO and click next.

![Ping Setup 7](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_7.png)

8. Click on Configure User-Session Creation for defining the mappings between the SAML XML and the user system.

![Ping Setup 8](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_8.png)

9. In the Identity Mapping section, Choose No Mapping and click next.

![Ping Setup 9](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_9.png)

10. Private Identity provides the GUID of the registered user. Configure the mappings in the Attribute Contract section on what values have to be mapped from the SAML. Click done.

![Ping Setup 10](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_10.png)

11. Click on Configure Protocol Settings to set up how the SAML Request and Response has to be sent and received.

![Ping Setup 11](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_11.png)

12. In the SSO Service URLs section, Choose Redirect as the Binding and give the desired modality URL as the Endpoint URL. The following modalities are currently configured.

* [Face modality](https://private.id/a/?idp=ping&apiKey=1962&action=predict&authType=face&SAMLPartnerID=privateid.face)
* [Voice modality](https://private.id/a/?idp=ping&apiKey=1962&action=predict&voice=true&face=false&liveness=true&SAMLPartnerID=privateid.voice)
* [Face & Voice modality](https://private.id/a/?idp=ping&apiKey=1962&action=predict&voice=true&face=true&faceLiveness=false&liveness=true&SAMLPartnerID=privateid.faceandvoice)

Click next.

![Ping Setup 12](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_12.png)

13. Check both POST and Redirect bindings. Click next.

![Ping Setup 13](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_13.png)

14. Leave the default configuration in the Overrides section. Click next.

![Ping Setup 14](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_14.png)

15. In the Signature Policy section, Choose "Specify Additional Signature Requirements" and check sign Authn request. Click next.

![Ping Setup 15](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_15.png)

16. Choose Encryption Policy as None and Click done.

![Ping Setup 16](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_16.png)

17. Click on Configure credentials to upload the IdP's certificate to authenticate the requests.

![Ping Setup 17](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_17.png)

18. Choose the certificate to sign the SAML Requests by selecting the certificates from the dropdown. Check both the boxes to include the certificate in the request. Click next.

![Ping Setup 18](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_18.png)

19. Click on Manage Signature Verification Settings to choose the certificate required for verifying the SAML Response received from the IdP.

![Ping Setup 19](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_19.png)

20. Choose the UNANCHORED option in the Trust Model section and click next.

![Ping Setup 20](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_20.png)

21. Choose the certificate to verify the response from the dropdown. Click done.

![Ping Setup 21](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_21.png)

22. A general summary of all the configuration will be displayed for verification. Confirm the setup configuration before saving.

![Ping Setup 22](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_22.png)

23. After verifying the setup parameters, Click save to process the IdP connection.

![Ping Setup 23](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_23.png)

Sample SAML Request:

    <samlp:AuthnRequest xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol"
                        Version="2.0"
                        ID="i.lFUTKZdLO0XH7XkLIjQK8CKKw"
                        IssueInstant="2020-05-20T11:21:53.922Z"
                        >
        <saml:Issuer xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion">private.id</saml:Issuer>
        <saml:Subject xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion">
            <saml:NameID>srie</saml:NameID>
        </saml:Subject>
        <samlp:NameIDPolicy AllowCreate="true" />
    </samlp:AuthnRequest>

Sample SAML Response:

    <saml2p:Response xmlns:saml2p="urn:oasis:names:tc:SAML:2.0:protocol"
                     xmlns:xs="http://www.w3.org/2001/XMLSchema"
                     Destination="https://18.188.167.103:9031/sp/ACS.saml2"
                     ID="id9GuNOlbQbiE8MXGc19ne6RoWyCEs2k"
                     InResponseTo="i.lFUTKZdLO0XH7XkLIjQK8CKKw"
                     IssueInstant="2020-05-20T11:22:37Z"
                     Version="2.0"
                     >
        <saml2:Issuer xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion"
                      Format="urn:oasis:names:tc:SAML:2.0:nameid-format:entity"
                      >privateid.enroll</saml2:Issuer>
        <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
            <ds:SignedInfo>
                <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />
                <ds:SignatureMethod Algorithm="http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" />
                <ds:Reference URI="#id9GuNOlbQbiE8MXGc19ne6RoWyCEs2k">
                    <ds:Transforms>
                        <ds:Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
                        <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />
                    </ds:Transforms>
                    <ds:DigestMethod Algorithm="http://www.w3.org/2001/04/xmlenc#sha256" />
                    <ds:DigestValue>zhncbf+0nSTTLK7cdoQsBqzHDyvHguay6F59RtuG8VU=</ds:DigestValue>
                </ds:Reference>
            </ds:SignedInfo>
            <ds:SignatureValue>iXYBJYD8hzPy55MAz74QplaJ1P0mTsOXI2u4wS6rauhLBDE+1EAYoZZBfLm0vaNNX9Q+Zsaf81px0mSTgymeqD3Gn9rOnkDSONRVI3foOOpUD0ByObpYVm949c28LYmry+ehKUvs2aQUdCVn8LeqC7ZEbNNwEhi3xR5jgxE62usxUEeAgrE2YB3dNqdLeGpqomqWzxE53xf5Q3o1N7prVflQe8rZKplyZuePzzUbNtHiMRuJ8mNwRkSxSdM6qTSreM1Q9klGIUwMrxbKQswFAEfCnW9LMGaZfF6uUWq1Pduu6YorGKPWvjkbVn+abIP1RDsgm/bXbQh1avM7aGV+DQ==</ds:SignatureValue>
            <ds:KeyInfo>
                <ds:X509Data>
                    <ds:X509Certificate>MIIEGzCCAwOgAwIBAgIUa7n6jLeipmjyhazU9qzZoMZ8bkAwDQYJKoZIhvcNAQELBQAwgZwxCzAJBgNVBAYTAlVTMQswCQYDVQQIDAJNRDERMA8GA1UEBwwIV29vZGJpbmUxHjAcBgNVBAoMFVByaXZhdGUgSWRlbnRpdHksIExMQzERMA8GA1UECwwISWRlbnRpdHkxGTAXBgNVBAMMEFByaXZhdGUgSWRlbnRpdHkxHzAdBgkqhkiG9w0BCQEWEHNjb3R0QHByaXZhdGUuaWQwHhcNMTkxMjExMjEwOTIyWhcNNDcwNDI4MjEwOTIyWjCBnDELMAkGA1UEBhMCVVMxCzAJBgNVBAgMAk1EMREwDwYDVQQHDAhXb29kYmluZTEeMBwGA1UECgwVUHJpdmF0ZSBJZGVudGl0eSwgTExDMREwDwYDVQQLDAhJZGVudGl0eTEZMBcGA1UEAwwQUHJpdmF0ZSBJZGVudGl0eTEfMB0GCSqGSIb3DQEJARYQc2NvdHRAcHJpdmF0ZS5pZDCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBALJ1/2ij1PxRi7ZzaeWmUM1WZpsSHUSXGjUyvMWoffZaa4F+9HZvqIlIXP5Te/LMLMnwEQ2dHOMlBAKaMpLFgaQxK630/bx6rPWyBEtfpHGl0GcHkotAXyj46Bz/OHfaQjpGFirZIUM2idR7B7BatUYqLbOzC3JCKvgoD0rnqJX10+qLlKAFSmXn8V5nbpo5a/4mjzHtLYhjJ3cAgbkOSQLYUKcF7i7zQForXRJZCD4mtNs466ptl7uoBy90uolJraMRYxucUoNiLk8rCqRUxOU4bv/SocYjDM/Y/p2EArm1wCcBJH/vJEjCRNlx2ZJBC/UA3P0oQBUuD0OdL41ey58CAwEAAaNTMFEwHQYDVR0OBBYEFABwapu2N0QxKZcf5Cp6G6z24bccMB8GA1UdIwQYMBaAFABwapu2N0QxKZcf5Cp6G6z24bccMA8GA1UdEwEB/wQFMAMBAf8wDQYJKoZIhvcNAQELBQADggEBAHD5YMTBCdVqdVZFCwjX716OUAtm3iJkPBXlYELJcbNWKr4dOisBeJtwNI0+NsSwIPKX885wW2NB/5POcWRDruQbyYDMI8FWp1ia+n05a/lpynJ1tw1UbcuFrbnMrgCsA0mxUfewW2pc8i/VF94rxl3VXOPMAhZTU4pWLUfof5oG+szzRqB80QPsSotfViavrULwQVvOo+OfAgQeaTeIUiuDwSzG5DDqrrWs3mi3j6DsNh76bZ/1TKTjB8U8z2H/vAbskzhWTpDQk+uRy+v4ZiTYOCDvBNEDZ9DQbuhziF2XiSwkctW61zuXC5I2+8kty0nmEWh/Kv/rQMT6MTVpMGA=</ds:X509Certificate>
                </ds:X509Data>
            </ds:KeyInfo>
        </ds:Signature>
        <saml2p:Status xmlns:saml2p="urn:oasis:names:tc:SAML:2.0:protocol">
            <saml2p:StatusCode Value="urn:oasis:names:tc:SAML:2.0:status:Success" />
        </saml2p:Status>
        <saml2:Assertion xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion"
                         xmlns:xs="http://www.w3.org/2001/XMLSchema"
                         ID="idEZ98c4VU8zFIJGMkwaskkz6KTmpZZS"
                         IssueInstant="2020-05-20T11:22:37Z"
                         Version="2.0"
                         >
            <saml2:Issuer xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion"
                          Format="urn:oasis:names:tc:SAML:2.0:nameid-format:entity"
                          >privateid.enroll</saml2:Issuer>
            <saml2:Subject xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">
                <saml2:NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified">srie</saml2:NameID>
                <saml2:SubjectConfirmation Method="urn:oasis:names:tc:SAML:2.0:cm:bearer">
                    <saml2:SubjectConfirmationData InResponseTo="i.lFUTKZdLO0XH7XkLIjQK8CKKw"
                                                   NotOnOrAfter="2020-05-20T11:27:37Z"
                                                   Recipient="https://18.188.167.103:9031/sp/ACS.saml2"
                                                   />
                </saml2:SubjectConfirmation>
            </saml2:Subject>
            <saml2:Conditions xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion"
                              NotBefore="2020-05-20T11:20:37Z"
                              NotOnOrAfter="2020-05-20T11:27:37Z"
                              >
                <saml2:AudienceRestriction>
                    <saml2:Audience>private.id</saml2:Audience>
                </saml2:AudienceRestriction>
            </saml2:Conditions>
            <saml2:AuthnStatement xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion"
                                  AuthnInstant="2020-05-20T11:22:37Z"
                                  SessionIndex="idEZ98c4VU8zFIJGMkwaskkz6KTmpZZS"
                                  >
                <saml2:AuthnContext>
                    <saml2:AuthnContextClassRef>urn:oasis:names:tc:SAML:2.0:ac:classes:PasswordProtectedTransport</saml2:AuthnContextClassRef>
                </saml2:AuthnContext>
            </saml2:AuthnStatement>
            <saml2:AttributeStatement xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">
                <saml2:Attribute Name="GUID"
                                 NameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:unspecified"
                                 >
                    <saml2:AttributeValue xmlns:xs="http://www.w3.org/2001/XMLSchema"
                                          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                                          xsi:type="xs:string"
                                          >a17405cacaf9863e4a40</saml2:AttributeValue>
                </saml2:Attribute>
            </saml2:AttributeStatement>
        </saml2:Assertion>
    </saml2p:Response>

Once the setup is complete and when the user attempts to log in next time via SP, the user will be redirected to the IdP URL for the configured modality.

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

### Sample Ping Demo

Currently, a sample workflow of ping demo can be experienced in the following way.

1. First, the user will register themselves in the system using this [link](https://ping.private.id:9031/sp/startSSO.ping?SpSessionAuthnAdapterId=pingdemo&authType=enroll). The screen will ask for the Active Directory credentials to store the random hex string UUID returned from the system.
2. Second, the user can log in to the application using different modalities described in the link below:
* [Login with Face](https://ping.private.id:9031/idp/startSSO.ping?PartnerSpId=Dropbox&authType=face)
* [Login with Voice](https://ping.private.id:9031/idp/startSSO.ping?PartnerSpId=Dropbox&authType=voice)
* [Login with Face and Voice](https://ping.private.id:9031/idp/startSSO.ping?PartnerSpId=Dropbox&authType=faceandvoice)

Apart from the above functionalities, user can able to raise their enroll level by verifying with a document. Verified Enroll can be achieved with this [link](https://private.id/a/index.htm?apiKey=1962&passport=true)

In case, the user has forgotten their credentials for your Active Directory, they can recover the password with the [Recover Password](https://ping.private.id:9031/ext/pwdreset/Identify?AdapterId=ActiveDirectory)

If the user wishes to delete their biometric from the system, they can use either [Forget User](https://private.id/a/?apiKey=1962&action=deleteSubject) link which will predict the user first then proceed with deletion or [Delete User](https://private.id/deleteUser/) link by providing the user's UUID.

A sample demo of all the links can be accessed through [Ping Demo](https://ping.private.id/ping.html) page.