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
* The Private Identity Recognition Algorithm performed fairly across all subgroups.  
* The model generated no false positive (Type 1) errors.
* The model generated false negative errors on poor quality images. Examples of images that the model is unable to process are shown below.
![Examples of images that generated Type II errors](https://github.com/openinfer/PrivateIdentity/blob/master/images/Examples%20of%20FNIR%20Images.png)

### `Embedding DNN Evaluation for Private ID Facial Recognition Model 1607349233`
* At Cutoff 1.14: Min = 0.68, Mean = 1.00, Max = 1.14, F1 = 99%
* Cutoff Evaluation Performance: IR=99.8%, FPIR=0.000%, FNIR=0.200%
* Cutoff analysis for each Subclass is shown below.
* Please see [**Embedding DNN Performance Analysis December 2020**](https://github.com/openinfer/PrivateIdentity/wiki/FACE-EMBEDDING-DNN-PERFORMANCE-DECEMBER-2020) for the Cutoff analysis. 

<pre>
Authors:  	  Chung Nguyen PhD
                  Scott Streit, CTO 
Data Run Date:    DEC 17, 2020. 15:30 EST
</pre>