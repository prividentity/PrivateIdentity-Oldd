[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

<br/>

In this document, the SaaS architecture is explained in terms of how the workflow should be executed. The elements of this workflow are as follows: 

1. Consuming client.
1. NodeJS middle-tier.
1. Authorizing Python server.

1- The consuming client is any application trying to use any of our services previously explained. The client must have a valid api_key for a request to execute. 

2- NodeJS middle-tier is passing the api_key to the Python server, and making sure it exists in valid format. If the api_key is invalid or absent in the call payload, error message will be sent back without consuming the Python server.

3- The Python server checks to see if the request has a valid api_key. If the api_key format is valid, processing continues. 


The first step in the workflow is to register a new api_key for any given client, so that it can be used. This api_key cannot be used inside a browser JavaScript code. It can be used, for example, on NodeJS, and that would be to prevent exploiting the api_key to the outer world.

Here is an example of using api_key in the previously described workflow:


|Parameter     |         Value| 
|-----|----|
|...           |         This can be any kind of request, like predict or enroll.|
|api_key      |          value of api_key in text format.|

```
{
 ...,
 api_key: "xxxxxxxxxxx"
}
```

This structure denotes that any kind of request, must have a key called api_key at the top level of the request.  The three dots in the previous payload can be replaced with any other type of request, i.e., predict or enroll.

If the api_key is absent or coming in invalid format, in any request payload, the NodeJS will respond back with the following error message:

```
{
 error: 'invalid api_key key'
} 
```