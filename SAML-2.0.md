### SAML Overview

Our biometric technologies are compliant with SAML (Security Assertion Markup Language) standards. The latest standardized version of the protocol is 2.0, and it is the one we support. 

In this document, the workflow is explained with examples on Google GSuite and Microsoft Azure Directory. The process should begin at our authentication application, then move to the external parties (Google and Microsoft in this case). Once we connect with such entities, we can redirect back to, for example, your GMail, or your Outlook account.


### Integration with GSuite

In this example, the GSuite is utilized along with our authentication application, so that users can login to any service provided by Google. 

** Request **

The format of this API call is:  

POST “/node/getSamlResponse”

|Parameter     |         Value| 
|-----|----|
|loginEmail           |         GSuite email that was used during enroll.|
|domain      |         User's GSuite domain.|
|api_key      |         Authorization api_key.|

For example, if we are trying to login to GMail using the email user@domain.org, the login email will be "user@domain.org", and the domain will be "domain.org."

```
{
   "loginEmail": "user@example.org",
   "domain": "example.org",
   "api_key": "xxxx"
}
```

**Response**

The response coming from this endpoint should be useful inside an HTML form. The result is a base64 encoded XML response that can be sent to Google for authorization.


### Integration with Microsoft Azure

In addition to being compatible with Google's GSuite, our application is also capable of granting user access to Microsoft services. The workflow is similar to the previously described one, with respect to some parameter changes.


** Request **

The format of this API call is:  

POST “/node/getSamlResponseAzure”

|Parameter     |         Value| 
|-----|----|
|loginEmail           |         GSuite email that was used during enroll.|
|domain      |         User's GSuite domain.|
|api_key      |         Authorization api_key.|

For example, if we are trying to login to Outlook using the email user@domain.org, the login email will be "user@domain.org", and the domain will be "domain.org."


```
{
   "loginEmail": "user@example.org",
   "domain": "example.org",
   "api_key": "xxxx"
}
```


**Response**

The response coming from this endpoint should be useful inside an HTML form. The result is a base64 encoded XML response that can be sent to Microsoft for authorization.