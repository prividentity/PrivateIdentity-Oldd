### OAuth 2.0 API Overview

In this document, the workflow for OAuth 2.0 protocol will be explained in detail. The process of utilizing OAuth 2.0 inside our app starts with the following step:

### Registering a Client

**Request**

Register a client inside our OAuth workflow. The format of this API call is:  

POST “/trueid/v1.1/add_client”

|Parameter     |         Value| 
|-----|----|
|client_name           |         Name of the client in string.|
|api_key           |         Authorized api_key in string.|


**Response**

If the parameters are correct, the client will be added and a message containing the client_id and client_secret is returned.

```
{
    "id": 1,
    "secret": "xxxx",
    "status": 0
}
```

### Checking Client Status

The next step is checking whether our client details are correct or not. This is done in the following way:

**Request**

The format of this API call is: 

POST “/trueid/v1.1/client_exists”

|Parameter      |            Value|
|----------|--------------| 
|client_id       |            client_id returned from previous call.|
|client_secret       |            client_secret returned from previous call.|
|api_key       |            Client api_key in string.|







