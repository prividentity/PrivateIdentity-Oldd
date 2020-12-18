### `VALIDATE SOFTMAX TRAINING`

The Private ID Facial Recognition Model 1607349233 is trained with 83,425 classes and 54M images. 
Validation accuracy is 91.62% using 4M images. 

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Exp044_backup_Accuracy.png)
Source: TensorBoard Visualization Toolkit

### `TRIPLET LOSS TRAINING` 
Triplet loss training is pending. 
We will update this page as soon as training finishes.

### `CUTOFF ANALYSIS USING 20K RANDOM IMAGES`

The multi-variable cutoff analysis is calculated using 20,000 random images from the DIF-CELEB-1M evaluation set. DNN performance is assessed by accuracy, precision and recall. 

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Exp044_backup_Cutoff_Analysis.png) 
Source: TensorBoard Visualization Toolkit

### `THRESHOLD ANALYSIS`

We next derive the multi-value cutoff threshold analysis using the same 20,000 random images. This threshold analysis allows further optimization by considering min, mean and max thresholds.

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Exp044_backup_Threshold_Analysis.png)
Source: TensorBoard Visualization Toolkit

**Line 867 (highlighted) provides 1.14 as the optimal threshold.**  
At Cutoff = 1.14, accuracy F1=99%, and we observe 30 false positives and 11 false negatives. 
In production, the algorithm adjudicates each prediction to eliminate false positives.

### `DIVERSITY ANALYSIS` 

We next conduct the cutoff analysis on subgroups (Black, Asian, White, Hispanic, other). 
The following table illustrated the statistics and the cutoff analysis result.

| Race | #people | #images | Cutoff Analysis | Error at cutoff = 1.14 |
| ------------- | ------------- | -------------  | ------------- | ------------- |
|  Black | 298 | 9611  |  Best cut off:  1.11<br>Accuracy:  0.993 | Error: 0.8%<br>Accuracy:  0.992 |
|  Asian | 124 | 4744  |  Best cut off:  1.13<br>Accuracy:  0.992| Error: 0.9%<br>Accuracy:  0.991 |
|  White | 1091 | 48344  |  Best cut off:  1.13<br>Accuracy:  0.997| Error: 0.3%<br>Accuracy:  0.997 |
|  Hispanic | 483 | 15218  |  Best cut off:  1.13<br>Accuracy:  0.997| Error: 0.3%<br>Accuracy:  0.997 |
|  Other | 75 | 3504  |  Best cut off:  1.10<br>Accuracy:   0.992| Error: 1%<br>Accuracy:  0.99 |
|  ALL | 2071 | 81421  |  Best cut off:  1.14<br>Accuracy:  0.998| Error: 0.2%<br>Accuracy:  0.998 |

### `DATASET BALANCE AND AUGMENTATION`

Visual examples of two HSL algorithms (HSL-1 and HSL-2) are displayed below.  

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/HSL%20Images.png)
<pre>
Authors:  	Chung Nguyen PhD 
                Scott Streit, CTO
Data Run Date:  DEC 18 2020, 13:42PM EST
</pre>

