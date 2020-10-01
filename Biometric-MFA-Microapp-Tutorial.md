In this tutorial we explore how to download the Biometric MFA Microapp and deploy it. This requires that you have an HTTPS domain where you will deploy the JavaScript and have the app running.

## Video Tutorial
[![Video Tutorial on Biometric MFA Microapp](https://github.com/openinfer/PrivateIdentity/blob/master/images/cbmfa%20Microapp%20Tutorial%20Video%201.png)](https://youtu.be/3NOQQXazjno "Quick Tutorial on the Cloud Biometric MFA Microapp")

## Step 1: `Download MFA-Microapp.zip`

The first step is to [download](http://private.id/MFA-Microapp.zip) the Biometric MFA Microapp. 

## Step 2:  `Copy the MFA Microapp to your Web server`
Once the download finishes, you will unzip the file and see two folders and one file: dist, src, and `index.htm`. The dist folder contains the necessary JS files and images. The src folder contains the machine learning models. And finally, the `index.htm` file is one we will use to run the app.

Copy all directories to any convenient location on your Web server. 

## Step 3:  `Running the Microapp`

Once the two folders are uploaded to your Web server, exercise the MFA Microapp using the `index.htm` file. 

If you have uploaded the app to `https://domain.com`, for example, then you should go to `domain.com/index.htm?apiKey=XXXXXX` to run the MFA Microapp. It's important to use a valid API key or the app will not work.

## Step 4:  `Exercise the action URL parameter`
Now, as a second exercise, use the URL parameter `action` to control enrollment and prediction. The URL parameter `action` directs the MFA Microapp to start a user enrollment or user prediction task. 

For example, use the following parameter to direct the MFA Microapp to start a user enrollment. 
> domain.com/index.htm?apiKey=XXXXXX&redirect=google.com&action=enroll

Use the following parameter to direct the MFA Microapp to start a user prediction. 
> domain.com/index.htm?apiKey=XXXXXX&redirect=google.com&action=predict

The full list of client URL parameters is located [here.](https://github.com/openinfer/PrivateIdentity/wiki/Client-URL-Parameters) 

The full list of admin URL parameters is located [here.](https://github.com/openinfer/PrivateIdentity/wiki/Admin-URL-Parameters) 

## Step 5:  `Retrieve the UUID` 

After each successful enrollment or prediction, the server responds back with a UUID. Each enrolled user has a unique UUID. You can get this value through the global variable `window.uuid`. So, each time a prediction/enrollment is done successfully, a new UUID value will be available. 

## Step 6:  `Exercise the redirect URL parameter`

Navigate to `domain.com/index.htm?apiKey=XXXXXX` to see the app running. 
It should look like this:

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Screen%20Shot%202020-09-29%20at%206.40.11%20PM.png)

Now, as a first exercise, use the URL parameter `redirect` to control the Microapp. The URL parameter `redirect` provides the redirection path to follow after the Microapp finishes an enrollment or prediction task. 

For example, use the following parameter to redirect the user to the naked domain “google.com” once the user successfully finishes enrolling or predicting. 
> domain.com/index.htm?apiKey=XXXXXX&redirect=google.com 

This redirect parameter also accepts a full domain URL. 
> domain.com/index.htm?apiKey=XXXXXX&redirect=https://google.com

## Step 7:  `Exercise the JavaScript API tool`

The MFA Microapp can also be exercised without any client GUI. This allows any biometrics to be used for enrollment and prediction -- even if the biometrics are captured by a third-party biometric acquisition vendor, native phone app, different device, different sensor, or not captured in real time.   

First, find and unzip the file `predict-enroll-library.zip` inside the `MFA-Microapp.zip`.  Once expanded, upload `predict-enroll-library` to your web server. This tool utilizes the JS API methods. 

Open the file `index.html` to start using this tool. 

The complete **tutorial on the JavaScript API** is available [here](https://github.com/openinfer/PrivateIdentity/wiki/JavaScript-API). 

You can also exercise the same Sandbox on the Private Identity Website using the URL:
> http://private.id/predict-enroll-library/?apiKey=XXXXXXXXXXXXXXXXX
 
