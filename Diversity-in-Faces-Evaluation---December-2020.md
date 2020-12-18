Private Identity® Facial Recognition Using DIF-CELEB-1M
December 17, 2020

### `DIF-CELEB-1M Fairness Evaluation Dataset`

* Use the [Encryption Engine](https://github.com/openinfer/PrivateIdentity/wiki/Encryption-Engine-setup) Kubernetes cluster to reproduce results.
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
* **440,832 images used for probes**
  * All remaining original images from each class (73,472) are augmented 5X resulting in 440,832 probe images. 
### `RESULTS`
![Spreadsheet showing detailed results of evaluation](https://github.com/openinfer/PrivateIdentity/blob/master/images/Results%20in%20table.png)
[Link](https://drive.google.com/file/d/1xgbK_eiCjSMR4pNE6yabkjfj_Hzg3iyg/view?usp=sharing) to spreadsheet (Google Sheet)

![Charts showing results ](https://github.com/openinfer/PrivateIdentity/blob/master/images/Report%20Results.png)

### `Discussion`
* The Private Identity Recognition Algorithm performed fairly across all subgroups.  
* The model generated no false positive (Type 1) errors.
* The model generated False Negatives errors on poor quality images. Examples of images that the model is unable to process are shown below.
![Examples of images that generated Type II errors](https://github.com/openinfer/PrivateIdentity/blob/master/images/Examples%20of%20FNIR%20Images.png)



