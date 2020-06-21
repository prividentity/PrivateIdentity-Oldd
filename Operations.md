### Operations

1. Currently, the apiKey for the software has to be obtained by an administrator via request.

2. In the devel branch, a cron job has been setup that pulls the code automatically if there is any changes in the code

3. We can reset the server by calling the url with **resetServer**. For ex., if the url for the application is `https://sample.privateidentity.com` then we can reset the server by calling 
`https://sample.privateidentity.com/resetServer`

4. Another way to reset the server is by using the backdoor through the cluster pods. Detailed description on how to perform the operation can be seen in [reset Backdoor](https://github.com/openinfer/PrivateIdentity/wiki/Backdoors#reset-the-server)