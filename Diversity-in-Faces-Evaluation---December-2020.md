<pre>
Evaluation of the Private Identity® Facial Recognition Algorithm 
Using DIF-CELEB-1M (Diversity in Faces) Fair Evaluation Dataset
and Private ID Facial Recognition Model 1607349233
December 17, 2020
</pre>
### `Introduction`
Many facial recognition algorithms show bias for one or more subgroups. A customer therefore requested that Private Identity provide a diversity evaluation of the Private Identity facial recognition algorithm. In addition, the customer asked for the ability to run the evaluation themselves. 

First, we built a Diversity in Faces (DIF) evaluation dataset, DIF-CELEB-1M. Then, we enhanced Private Identity's [Encryption Engine](https://github.com/openinfer/PrivateIdentity/wiki/Encryption-Engine-setup) to accommodate high-throughput predictions and enrolls. Finally, we ran the Encryption Engine to enroll all faces in DIF-CELEB-1M and predict each probe. We describe the results below. 

### `DIF-CELEB-1M Fairness Evaluation Dataset`

* Customers with an API Key should use the [Encryption Engine](https://github.com/openinfer/PrivateIdentity/wiki/Encryption-Engine-setup) Kubernetes cluster to reproduce results. Researchers please contact sales@private.id to obtain an API Key. 
* **2,049 diverse classes in DIF-CELEB-1M**
  * DIF-CELEB-1M was created by Private Identity 11/2020
  * Subclass representation: 14% Black, 6% Asian, 53% White, 23% Hispanic, 4% Other
  * **1,300 classes** are from MS-Celeb-1M (deduplicated and cleaned)  
  * **700 diverse celebrity classes** added manually 
![Graph showing subclass diversity](https://github.com/openinfer/PrivateIdentity/blob/master/images/Describe%20Subclasses.png)
* **461,322 total facial images**
  * 93,962 original images (~ 46 images/subject)
  * 367,360 augmented images (rotations, flips, blurs, b/w, grayscale, abrasions)
  * MS-Celeb-1M images vary by color, B/W, grayscale, different background, lighting, pose and include frontal and profile views. 
* **20,490 images used for enrollment**
  * 10 original images from each class are augmented 8X (resulting in 80 images) and used to enroll the class.   
* **440,832 images used as probes**
  * All remaining original images from each class (73,472) are augmented 5X resulting in 440,832 probes. 
### `RESULTS`
![Spreadsheet showing detailed results of evaluation](https://github.com/openinfer/PrivateIdentity/blob/master/images/Results%20in%20table.png)
[Link](https://drive.google.com/file/d/1xgbK_eiCjSMR4pNE6yabkjfj_Hzg3iyg/view?usp=sharing) to spreadsheet (Google Sheets)

![Charts showing results ](https://github.com/openinfer/PrivateIdentity/blob/master/images/Report%20Results.png)

### `Discussion`
* The Private Identity Recognition Algorithm performed fairly across all subgroups.  
* The model generated no false positive (Type 1) errors.
* The model generated false negative errors on poor quality images. Examples of images that the model is unable to process are shown below.
![Examples of images that generated Type II errors](https://github.com/openinfer/PrivateIdentity/blob/master/images/Examples%20of%20FNIR%20Images.png)

### `Embedding DNN Evaluation for Private ID Facial Recognition Model 1607349233`
* At Cutoff 1.14: Min = 0.68, Mean = 1.00, Max = 1.14, F1 = 99%
* Cutoff Evaluation Performance: IR=99.8%, FPIR=0.000%, FNIR=0.200%
* Cutoff analysis for each Subclass is shown below.
* Please see [Embedding DNN Performance Analysis December 2020](https://github.com/openinfer/PrivateIdentity/wiki/FACE-EMBEDDING-DNN-PERFORMANCE-DECEMBER-2020) for the Cutoff analysis. 

<pre>
Authors:  	  Chung Nguyen PhD
                  Scott Streit, CTO 
Data Run Date:    DEC 17, 2020. 15:30 EST
</pre>