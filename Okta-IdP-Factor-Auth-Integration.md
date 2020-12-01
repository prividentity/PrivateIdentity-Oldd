## `Okta® IdP Factor Auth Integration Tutorial (Video)`
(Coming soon)

## `Okta® IdP Factor Authentication Integration`

### `Step 1: Login to Okta`
Log in to Okta as Admin

### `Step 2: Choose Identity Providers`
Go to Security -> Identity Providers

![Okta Setup 1](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_1.png)

### `Step 3: Add an Identity Provider`
Click on "Add Identity Provider" and Choose "Add SAML 2.0 IdP"

![Okta Setup 2](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_2.png)

### `Step 4: Login to Okta`
Fill in the parameters required. The Desired IDP name can be chosen for readability. Choose IdP Usage as Factory only. Fill in the IdP Issuer URI. Currently, the setup is configured with [Private ID](https://devel.private.id). IdP Single Sign-On URL will have the URL for the desired modality authentication. 

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

### `Step 5: Click on Advanced Settings`
Click on Advanced Settings. Change the Request Binding to HTTP Redirect. The destination has to be replaced with the same URL as that of IdP Single Sign-On URL. The signature algorithm has to be SHA-256. The remaining parameters can be modified according to the user's needs. Save the configuration

![Okta Setup 4](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_4.png)

### `Step 6: Choose Factor Types`
Go to Security -> Multifactor -> Factor Types.

![Okta Setup 5](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_5.png)

### `Step 7: Choose IdP Factor`
Choose the IdP Factor for selecting the configured IdP.

![Okta Setup 6](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_6.png)

### `Step 8: Choose the IdP and Save the Config`
Click edit and select the desired IdP and save the configuration.

![Okta Setup 7](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_7.png)

### `Step 9: Navigate to Factor Enrollment`
Go to Security -> Multifactor -> Factor Enrollment.

![Okta Setup 8](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_8.png)

### `Step 10: Choose Add Multifactor Policy`
Click on Add Multifactor Policy and fill in the required details. Give a policy name, description, assign the groups to everyone, and choose the effective factor as required. Save the policy.

![Okta Setup 9](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_9.png)

### `Step 11: Navigate to Sign On`
Go to Security -> Authentication -> Sign On.

![Okta Setup 10](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_10.png)

### `Step 12: Choose Add Rule`
Click on Add Rule to configure a Multifactor rule so that the user will be prompted for multi-factor authentication.

![Okta Setup 11](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_11.png)

### `Step 13: Enable the Rule and Save`
Keep the default values or change as needed. Check the Prompt for Factor option to enable the rule. Save the configuration.

![Okta Setup 12](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_setup_12.png)

Once the setup is complete and when the user attempts to log in next time into the SP, the factor prompt will be asked for the user for completing the authentication.

Sample SAML Request:
`
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
`
Sample SAML Response:
`
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
`
The following screenshots show a sample demonstration of authentication done with face modality.

1. Logging into okta as a service provider [Sample URL](https://private.okta.com).

![Okta Login](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_login.png)

2. Okta uses a multi-factor authentication followed by a password prompt, redirecting the user to IP authentication.

![Okta Multi Factor](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_multi_factor.png)

3. The user gets authenticated by the requested modality e.g., face and if the user is authenticated successfully a success response will be sent to SP.

![IP Face Modality](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_IP_predict.png)

4. If the user gets authenticated successfully, the user will be redirected to the successful login page.

![Okta Success](https://github.com/openinfer/PrivateIdentity/blob/master/images/okta_success.png)
