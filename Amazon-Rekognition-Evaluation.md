<pre>
Evaluation of the Rekognition Facial Recognition Algorithm 
Using DIF-CELEB-1M (Diversity in Faces) Fair Evaluation Dataset
and AWS Face 5.0 version model
February 11, 2021
</pre>
### `Introduction`
We built a Diversity in Faces (DIF) evaluation dataset, DIF-CELEB-1M for evaluating our Face embedding model. We evaluated the dataset with the Amazon Rekognition to compare the performance of our model

* **2,049 diverse classes in DIF-CELEB-1M**
  * DIF-CELEB-1M was created by Private Identity 11/2020
  * Subclass representation: 14% Black, 6% Asian, 53% White, 23% Hispanic, 4% Other
  * **1,300 classes** are from MS-Celeb-1M (deduplicated and cleaned)  
  * **700 diverse celebrity classes** added manually 


### `DIF-CELEB-1M Fairness Evaluation Dataset`

![Graph showing subclass diversity](https://github.com/openinfer/PrivateIdentity/blob/master/images/Describe%20Subclasses.png)
* **93,962 original images (~ 46 images/subject)**
  * MS-Celeb-1M images vary by color, B/W, grayscale, different background, lighting, pose and include frontal and profile views. 
* **2049 images used for enrollment**
* **91913 images used as probes**

### `RESULTS`
![Spreadsheet showing detailed results of evaluation](https://github.com/openinfer/PrivateIdentity/blob/master/images/rek_vs_pri_table_results.png)
[Link](https://docs.google.com/spreadsheets/d/1ZiVZRTzzJl72vL1opwUCRPPm_MzDDk-t5cj9BTeoImg/edit?usp=sharing) to the spreadsheet (Google Sheets)

![Rekognition vs  results ](https://github.com/openinfer/PrivateIdentity/blob/master/images/rek_vs_pri_chart_results.png)

### `Discussion`
* The Private Identity Recognition Algorithm has a better performance than the AWS Rekognition API.  
* The AWS model generated 0.47% False positives when compared with a confidence score of 0.98.
* The AWS model generated 0.002% False positives when compared with a confidence score of 0.6.
* The AWS Face model was not able to identify 2.01% of persons when compared with the indexed faces. 
* The AWS Face model could not detect faces on 0.3% of images used for evaluation. 

### `Embedding DNN Evaluation for Private ID Facial Recognition Model 1607349233`
* Please check [**Diversity in Faces Evaluation December 2020**](https://github.com/openinfer/PrivateIdentity/wiki/Diversity-in-Faces-Evaluation---December-2020) for a more detailed comparison for the Face model results by Private Identity
* Please see [**Embedding DNN Performance Analysis December 2020**](https://github.com/openinfer/PrivateIdentity/wiki/FACE-EMBEDDING-DNN-PERFORMANCE-DECEMBER-2020) for the Cutoff analysis. 

<pre>
Authors:  	  Srie Raam MS
                  Scott Streit, CTO 
Data Run Date:    DEC 17, 2020. 15:30 EST
</pre>