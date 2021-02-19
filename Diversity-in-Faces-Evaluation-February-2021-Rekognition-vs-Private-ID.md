<pre>
Evaluation of the Cloud Biometric API Facial Recognition Algorithm using Diversity in Faces 
Fair Evaluation Dataset (DIF-CELEB-1M). The [Cloud Biometric API](https://private.id) Face Model 1607349233
ran on 17 Dec 2020. The [Amazon Rekognition®](https://aws.amazon.com/rekognition/) service ran on 16 Feb 2021. 
</pre>

### `Introduction`
Recent academic papers suggest facial recognition algorithms contain bias for (or against) one or more subgroups. A customer therefore requested that Private Identity® provide a diversity evaluation of the Cloud Biometric API facial recognition algorithm. In addition, the customer asked for the ability to run the evaluation themselves. 

To accomplish the requested evaluation, we built the Diversity in Faces evaluation dataset (DIF-CELEB-1M). Then, we built an AWS Lambda and GCP Cloud Function (both run the same code) to accommodate high-throughput, serverless predictions and enrolls. Finally, we ran the Lambda function to enroll all classes in DIF-CELEB-1M in both Cloud Biometric API and Amazon Rekognition® and predict each probe. The results are described below. 

### `Methods`

To build the evaluation dataset, we collected and labeled 2,049 diverse classes and named the set DIF-CELEB-1M in November, 2020. The subclasses are represented as follows: 14% Black, 6% Asian, 53% White, 23% Hispanic, and 4% Other. 

In total, 1,300 classes were deduplicated and cleaned from the MS-Celeb-1M dataset. Then, we manually added 700 additional diverse celebrity classes to allow the subgroups to approximate the US population. Customers with an API Key should use Private Identity’s AWS Lambda function to reproduce results. Researchers please contact sales@private.id to obtain an API Key. 

![Graph showing subclass diversity](https://github.com/openinfer/PrivateIdentity/blob/master/images/Describe%20Subclasses.png)

DIF-CELEB-1M contains 461,322 total facial images.  Of these, 93,962 are original images (~ 46 images/subject) and 367,360 are augmented images (rotations, flips, blurs, b/w, grayscale, abrasions). The original MS-Celeb-1M images vary by color, B/W, grayscale, different background, lighting, pose and include frontal and profile views. 

We used 10 original images from each class, or 20,490 images, for enrollment. We then augmented each original image seven times (resulting in 80 images) and used the resulting set of 80 images to enroll each class. 

All remaining original images from each class (73,472) were augmented five times, resulting in 440,832 total probes. 

There are no user-selected thresholds in Cloud Biometric API. The Enroll and Predict Lambdas used the following three components:  Face Landmark, Blur Detection, and Face Identification.  Enroll and predict requests ran concurrently. 

For Amazon Rekognition, we experimented setting the confidence level between 0.5 and 0.99. We found optimal results at the 0.98 confidence level. We created AWS Lambdas for Enroll and Predict using the following three Rekognition components:  DetectFaces, IndexFaces, and SearchFaces. Enroll and predict requests ran linearly. 

We submitted a support request to AWS to increase allowed throughput (“unthrottle the service”) on February 8, 2021. Support personnel were helpful but unable to unthrottle the service before the study concluded on February 18, 2021.  We will update this posting as soon as the service is unthrottled.    


### `RESULTS`

We ran the DIF-CELEB-1M dataset on both the [Cloud Biometric API](https://private.id) service and the [Amazon Rekognition](https://aws.amazon.com/rekognition/) service.  Performance was recorded in log files.  

![Table 1.  Performance of Cloud Biometric API vs. Amazon Rekognition on the DIF-CELEB-1M evaluation dataset. ](https://github.com/openinfer/PrivateIdentity/blob/master/images/AWS%20Study%20Data%201.png)
Table 1.  Performance of Cloud Biometric API vs. Amazon Rekognition on the DIF-CELEB-1M evaluation dataset. 

To calculate the Identification Rate, 2049 enrolled classes were matched to 367,360 probe images (approx. 180 probe images per enrolled class).  

![Figure 1: Evaluation of Identification Rate (IR) by Subgroup Processing DIF-CELEB-1M](https://github.com/openinfer/PrivateIdentity/blob/master/images/AWS%20Study%20IR%203.png)
Figure 1: Evaluation of Identification Rate (IR) by Subgroup Processing DIF-CELEB-1M

![Figure 2: Evaluation of False Negative Identification Rate (FNIR, or Type II Error) by Subgroup Processing DIF-CELEB-1M](https://github.com/openinfer/PrivateIdentity/blob/master/images/AWS%20Study%20FNIR%201.png)
Figure 2: Evaluation of False Negative Identification Rate (FNIR, or Type II Error) by Subgroup Processing DIF-CELEB-1M

![Figure 3: Evaluation of False Positive Identification Rate (FPIR, or Type I Error) by Subgroup Processing DIF-CELEB-1M](https://github.com/openinfer/PrivateIdentity/blob/master/images/AWS%20Study%20FPIR%202.png)
Figure 3: Evaluation of False Positive Identification Rate (FPIR, or Type I Error) by Subgroup Processing DIF-CELEB-1M

![Figure 4. Evaluation of Time Required to Process DIF-CELEB-1M ](https://github.com/openinfer/PrivateIdentity/blob/master/images/AWS%20Study%20Time%20Minutes%201.png)
Figure 4. Evaluation of Time Required to Process DIF-CELEB-1M 

The Cloud Biometric API service required 12.08 minutes to enroll 2,049 classes using 20,490 images (28.27 images/sec), and 12.20 minutes to predict 440,832 probes (602.23 images/sec). In contrast, the Amazon Rekognition service required 547.7 minutes to enroll 2,049 classes using 20,490 images (0.62 images/sec), and 2777.1 minutes to predict 440,832 probes (2.65 images/sec). 

### `Discussion`
The Cloud Biometric API service performed fairly across all subgroups. The service generated no false positive (Type I) errors and very few false negative (Type II) errors when it encountered blurry images. 

Surprisingly, the Amazon Rekognition service performed fairly for the Black and Other subgroups (IR=99.54% and 99.35%, respectively). The remaining subgroups (Asian, White, and Hispanic) experienced 1.0% to 1.2% identification failures. Our results did not correlate with recent academic reports that reported Rekognition performed poorly on tasks involving members of the Black subgroup.  

Also surprisingly, 64% of the 118 false positive identifications (Type I errors) Rekognition generated were for the Asian subgroup. The other errors were distributed evenly (~10% each) across the Black, White, and Hispanic subgroups.   
