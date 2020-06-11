## Setup Predict Enroll library ##

### To run this you need a web server like apache2 or nginx ###

**Note**: If you already have web server you can skip below steps to install apache2 and simply unzip the downloaded code and move it to /var/www/html/ directory.

#### If you want to install an apache2 follow below steps #### 

1. Downlaod Zip file form URL https://private.id/predict-enroll-library.zip

2. Install apache2  `sudo apt-get install apache2`

3. unzip predict library `unzip predict-enroll-library.zip` 

4. move code to html location `mv predict-enroll-library /var/www/html/`

5. start apache2 service `sudo service apache2 start`



#### If you want to install nginx follow below steps #### 

1. Downlaod Zip file form URL an https://private.id/predict-enroll-library.zip

2. Install nginx 'sudo apt-get install nginx'

3. unzip predict library `unzip predict-enroll-library.zip` 

4. move code to html location `mv predict-enroll-library /var/www/html/` 

5. sudo service nginx start


After this you will able to access predict library from url http://localhost/predict-enroll-library/?apiKey=XXXX

[[ images/Title.png ]]

**Note:** You will get the API key from Private Identity.


