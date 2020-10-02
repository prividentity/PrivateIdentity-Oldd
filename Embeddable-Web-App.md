In this tutorial, we are going to explore how to download the web app and deploy it. This tutorial assumes you have an HTTPS domain, where you want to have the app running.

## Video Tutorial
<b>[Link](https://youtu.be/1hk2ATzgKzA) to video tutorial.</b>

## Step 1: `Downloading Files`

The first step is to click on [this link](http://private.id/MFA-Microapp.zip) to download the app. Once the download finishes, we can see two folders and one file: dist, src, and `index.htm`. The dist folder contains the necessary JS files and images. The src folder have the machine learning models. And finally, the `index.htm` file is one we should use to run the app.


## Step 2:  `Running the Microapp`

Once we upload the two extracted folders and the HTML file, we should be able to run it, through the `index.htm` file. So, if you uploaded the app to `example.org`, then you should go to example.org/index.htm?apiKey=XXXXXX. It's important to use the `apiKey` parameter with the proper value, or otherwise the app won't work.

## Step 3:  `Using the Microapp` with the redirect URL parameter

Once we have the app running, we can see the homepage like this:

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Screen%20Shot%202020-09-29%20at%206.40.11%20PM.png)

You can now use all the app features and URL parameters. In case of a successful prediction, the URL parameter 'redirect' is considered as redirection path. Example: `example.org/index.htm?apiKey=XXXXXX&redirect=domain.com` will redirect the user to domain.com once he finishes prediction successfully.  



# Running the JS API Tool

After downloading [the .zip file](http://private.id/MFA-Microapp.zip) we mentioned before, we can find another useful tool for utilizing the JavaScript API methods. This tool consists of one folder, and two files. The `models` folder has all the necessary machine learning models. You can also find `module.js` file, which is responsible for exporting the API methods to the browser. Finally, the `index.html` file has an example of using the models and the `module.js` file. 

You can find a live example of this tool in this link: https://private.id/predict-enroll-library/

For more information about the available API methods, please take a look at: https://github.com/openinfer/PrivateIdentity/wiki/JavaScript-API