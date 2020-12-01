## `PingFederate® Integration Tutorial (Video)`
[![IMAGE ALT TEXT](https://github.com/openinfer/PrivateIdentity/blob/master/images/PingFederate%20Integration%20PLAY%201.png)](https://youtu.be/pN1wLWwmyV0 "PingFederate Integration Tutorial with Cloud Biometric MFA")

## `Step-by-Step PingFederate® Integration`

### `Step 1: Choose the Service Provider`
Log in to the PingFederate server and choose Service Provider. Click Create New to create a new IdP connection.

![Ping Setup 1](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_1.png)

### `Step 2: Choose the Connection Type`
Choose the connection type as Browser SSO profiles SAML 2.0. Click next

![Ping Setup 2](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_2.png)

### `Step 3: Choose the Default Configuration`
Leave the Default configuration of Browser SSO. Click Next.

![Ping Setup 3](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_3.png)

### `Step 4: Choose Metadata as none`
Choose Metadata as None and click next.

![Ping Setup 4](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_4.png)

### `Step 5: Enter the Entity ID`
In the General Info screen, fill the desired name in entity ID e.g., privateid.face with the connection name. Click next.

![Ping Setup 5](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_5.png)

### `Step 6: Configure Browser SSO`
Click on Configure Browser SSO.

![Ping Setup 6](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_6.png)

### `Step 7: Choose SP Initiated SSO`
In the SAML Profiles section, check the SP Initiated SSO and click next.

![Ping Setup 7](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_7.png)

### `Step 8: Click on Configure User-Session Creation`
Click on Configure User-Session Creation for defining the mappings between the SAML XML and the user system.

![Ping Setup 8](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_8.png)

### `Step 9: Choose No Mapping`
In the Identity Mapping section, Choose No Mapping and click next.

![Ping Setup 9](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_9.png)

### `Step 10: Configure Mappings`
Private Identity provides the GUID of the registered user. Configure the mappings in the Attribute Contract section on what values have to be mapped from the SAML. Click done.

![Ping Setup 10](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_10.png)

### `Step 11: Configure Protocol Settings`
Click on Configure Protocol Settings to set up how the SAML Request and Response has to be sent and received.

![Ping Setup 11](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_11.png)

### `Step 12: Choose Redirect as the Binding`
In the SSO Service URLs section, Choose Redirect as the Binding and give the desired modality URL as the Endpoint URL. The following modalities are currently configured.

* [Face modality](https://private.id/a/?idp=ping&apiKey=1962&action=predict&authType=face&SAMLPartnerID=privateid.face)
* [Voice modality](https://private.id/a/?idp=ping&apiKey=1962&action=predict&voice=true&face=false&liveness=true&SAMLPartnerID=privateid.voice)
* [Face & Voice modality](https://private.id/a/?idp=ping&apiKey=1962&action=predict&voice=true&face=true&faceLiveness=false&liveness=true&SAMLPartnerID=privateid.faceandvoice)

Click next.

![Ping Setup 12](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_12.png)

### `Step 13: Choose both POST and Redirect Bindings`
Check both POST and Redirect bindings. Click next.

![Ping Setup 13](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_13.png)

### `Step 14: Choose Default Overrides`
Leave the default configuration in the Overrides section. Click next.

![Ping Setup 14](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_14.png)

### `Step 15: Choose Additional Signature Requirements`
In the Signature Policy section, Choose "Specify Additional Signature Requirements" and check sign Authn request. Click next.

![Ping Setup 15](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_15.png)

### `Step 16: Choose Encryption Policy`
Choose Encryption Policy as None and Click done.

![Ping Setup 16](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_16.png)

### `Step 17: Configure Credentials`
Click on Configure credentials to upload the IdP's certificate to authenticate the requests.

![Ping Setup 17](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_17.png)

### `Step 18: Choose the Certificate`
Choose the certificate to sign the SAML Requests by selecting the certificates from the dropdown. Check both the boxes to include the certificate in the request. Click next.

![Ping Setup 18](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_18.png)

### `Step 19: Choose Manage Signature Verification`
Click on Manage Signature Verification Settings to choose the certificate required for verifying the SAML Response received from the IdP.

![Ping Setup 19](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_19.png)

### `Step 20: Choose the Unanchored Option`
Choose the UNANCHORED option in the Trust Model section and click next.

![Ping Setup 20](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_20.png)

### `Step 21: Choose the Certificate`
Choose the certificate to verify the response from the dropdown. Click done.

![Ping Setup 21](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_21.png)

### `Step 22: Confirm Configuration`
A general summary of all the configuration will be displayed for verification. Confirm the setup configuration before saving.

![Ping Setup 22](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_22.png)

### `Step 23: Save`
After verifying the setup parameters, Click save to process the IdP connection.

![Ping Setup 23](https://github.com/openinfer/PrivateIdentity/blob/master/images/ping_setup_23.png)

Sample SAML Request:
`
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
`
Sample SAML Response:
`
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
`
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

### `Sample Ping Demo`

Currently, a sample workflow of ping demo can be experienced in the following way.

First, the user will register themselves in the system using this [enroll link](https://ping.private.id:9031/sp/startSSO.ping?SpSessionAuthnAdapterId=pingdemo&authType=enroll). The screen will ask for the Active Directory credentials to store the random hex string UUID returned from the system.

Second, the user can log in to the application using different modalities described in the link below:
* [Login with Face](https://ping.private.id:9031/idp/startSSO.ping?PartnerSpId=Dropbox&authType=face)
* [Login with Voice](https://ping.private.id:9031/idp/startSSO.ping?PartnerSpId=Dropbox&authType=voice)
* [Login with Face and Voice](https://ping.private.id:9031/idp/startSSO.ping?PartnerSpId=Dropbox&authType=faceandvoice)

Apart from the above functionalities, user can able to raise their enroll level by verifying with a document. The described functionality can be achieved with this [verified enroll link](https://private.id/a/index.htm?apiKey=1962&passport=true)

In case, the user has forgotten their credentials for your Active Directory, they can recover the password with the [Recover Password](https://ping.private.id:9031/ext/pwdreset/Identify?AdapterId=ActiveDirectory)

If the user wishes to delete their biometric from the system, they can use either [Forget User](https://private.id/a/?apiKey=1962&action=deleteSubject) link which will predict the user first then proceed with deletion or [Delete User](https://private.id/deleteUser/) link by providing the user's UUID.

A sample demo of all the links can be accessed through [Ping Demo](https://ping.private.id/ping.html) page.


