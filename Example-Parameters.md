### This page will demonstrate a few parameters to grant the user a better understanding of their usage and can integrate other parameters in the same usage. Some parameter walk throughs are seen at the web applications page, but this page will walk the user through the URL usage of the parameters.

> Note, images seen may not be completely up to date, and an apikey was necessary, but functionality will still be the same.

> Note, there are two servers, the developer server and the main server, both have slightly different URLs. The main server is to be the most up to date functioning server, and the developer server is where changes are made and tested and user information may be subject to reset. For demonstration sake the developer server will be used.

### Voice Enrollment
The URL used here was 

devel.private.id/demo/?apiKey=#&voice=true&face=false
> insert image of browser demonstrating usage

This utilizes the voice only modality to enroll the user
### Face Enrollment
The URL used here was

devel.private.id/demo/?apiKey=#
> insert image of browser demonstrating usage

This utilizes the face only modality to enroll the user. Note that because is by default enabled, and voice is by default disabled, no parameters are necessary except the apikey

### Voice/Face Enrollment
The URL used here was

devel.private.id/demo/?apiKey=#&voice=true
> insert image of browser demonstrating usage

This utilizes both face and voice modalities, and will combine them under the same subject ID.

### Liveness Usage
This URL is to demonstrate variables during predictions such as blinking during a facial recognition. It works the same as a regular enroll however. 

devel.private.id/demo/?apiKey=#&voice=true&liveness=true
>for vocal liveness testing

devel.private.id/demo?apiKey=#&faceLiveness=true

>for facial liveness testing

### Multiple Parameters Demo

For this URL the idea was to fit as many parameters in while it still working properly. The idea is that as long as the parameters don't overstep each other they will work together

devel.private.id/demo/?apiKey=#&voice=true&liveness=true&faceLiveness=true&debug=true&isEdge=true&glasscheck=true&livenessImages=1

The result is a voice and face enrollment that sees that its also applying liveness to the testing. The debugger is now enabled that'll output your taken pictures after they have been formatted. The URL is also behaving as if it is on Microsoft Edge, and the glasscheck is enabled, and the number of liveness images taken is 1.





