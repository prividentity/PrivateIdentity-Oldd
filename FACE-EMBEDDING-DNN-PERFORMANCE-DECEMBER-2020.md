### EMBEDDING DNN PERFORMANCE ### 

***
### VALIDATION ACCURACY OF SOFTMAX TRAINING ###

**Face recognition DNN trained with 54M images** and 83425 people with validation accuracy of 91.62% using 4M images for validation. 

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Exp044_backup_Accuracy.png)

### TRIPLET LOSS TRAINING ###

** We haven't started the triplet loss training yet.

Data visualization is from TensorFlow’s TensorBoard visualization toolkit

### CUTOFF ANALYSIS USING 20K RANDOM IMAGES ###

The cutoff analysis is then calculated using a random segment of the evaluation set.

This is used for a starting point on a multi-variable cutoff analysis.  We choose 20,000 random images from the evaluation set and measured DNN performance by accuracy, precision and recall. 

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Exp044_backup_Cutoff_Analysis.png) 

### THRESHOLD ANALYSIS ###

**Threshold** analysis using the same 20,000 random images from the evaluation dataset. This analysis assists in further optimization considering min, mean and max thresholds in deriving the multi-value cutoff.

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Exp044_backup_Threshold_Analysis.png)

**Line 867 (highlighted) provides 1.14 as the optimal threshold.**  
This results in an accuracy of F1=99%, 30 false positives and 11 false negatives. This is asymptotic to 100% accuracy.


### ETHNIC, GENDER AND RACE BREAKDOWN
We conducted the cutoff analysis on each race (african_american, asian, caucasian_white, hispanic_latino, other) and all races. The following table illustrated the statistics and the cutoff analysis result.

| Race | #people | #images | Cutoff Analysis | Error at cutoff = 1.14 |
| ------------- | ------------- | -------------  | ------------- | ------------- |
|  african_american | 298 | 9611  |  Best cut off:  1.11<br>Accuracy:  0.993 | Error: 0.8%<br>Accuracy:  0.992 |
|  asian | 124 | 4744  |  Best cut off:  1.13<br>Accuracy:  0.992| Error: 0.9%<br>Accuracy:  0.991 |
|  caucasian_white | 1091 | 48344  |  Best cut off:  1.13<br>Accuracy:  0.997| Error: 0.3%<br>Accuracy:  0.997 |
|  hispanic_latino | 483 | 15218  |  Best cut off:  1.13<br>Accuracy:  0.997| Error: 0.3%<br>Accuracy:  0.997 |
|  other | 75 | 3504  |  Best cut off:  1.10<br>Accuracy:   0.992| Error: 1%<br>Accuracy:  0.99 |
|  ALL | 2071 | 81421  |  Best cut off:  1.14<br>Accuracy:  0.998| Error: 0.2%<br>Accuracy:  0.998 |

### DATASET BALANCE AND AUGMENTATION ### 


Visual examples of two HSL algorithms (HSL-1 and HSL-2) are displayed below.  

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/HSL%20Images.png)
<pre>
Authors:  	Chung Nguyen PhD 
                Scott Streit, CTO
Data Run Date:  2 June 2020, 12:13AM
</pre>
