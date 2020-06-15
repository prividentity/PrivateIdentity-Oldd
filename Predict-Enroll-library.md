## Predict Enroll library ##

### Setup ###

Predict Enroll Library is a javascript library that will help you to Enroll and Predict by selecting the images from your browser. This library will send images to a Private Identity server or your own hosted Private Identity server for enrollment and prediction.

### To run this you need a web server like apache2 or nginx ###

**Note**: If you already have a web server you can skip below steps to install apache2 and simply unzip the downloaded code and move it to /var/www/html/ directory.

#### If you want to install an apache2 follow below steps #### 

1. Download Zip file form URL https://private.id/predict-enroll-library.zip

**Note:** ZIP file contains the Javascript library code that you need to run on your own server or your local system. 

2. Install apache2  `sudo apt-get install apache2`

3. Unzip predict library `unzip predict-enroll-library.zip` 

4. Move code to the following location `mv predict-enroll-library /var/www/html/`

5. Start apache2 service `sudo service apache2 start`



#### If you want to install an nginx follow below steps #### 

1. Download Zip file form URL an https://private.id/predict-enroll-library.zip

2. Install nginx `sudo apt-get install nginx`

3. Unzip predict library `unzip predict-enroll-library.zip` 

4. Move code to the following location `mv predict-enroll-library /var/www/html/` 

5. sudo service nginx start


After this, you will able to access predict and enroll from the demo page app. 

Launch the below-mentioned URL in your browser:

http://localhost/predict-enroll-library/?apiKey=XXXX

By default, the NodeJS endpoints are located at `https://private.id/node/`. If you want to change this setting, you can use the URL parameter `nodeServer` to your own private hosted server.

To host your own private server, please have a look at this [link](https://github.com/openinfer/PrivateIdentity/wiki/cluster-setup) which will give detailed step-by-step instructions on how to configure the endpoint.

For ex., if your own server is https://company.privateidentity.com then the URL will be

`http://localhost/predict-enroll-library/?apiKey=XXXX&nodeServer=https://example