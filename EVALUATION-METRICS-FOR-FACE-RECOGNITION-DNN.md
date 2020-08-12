### EMBEDDING RECOGNITION DNN PERFORMANCE ### 

***
### VALIDATION ACCURACY OF SOFTMAX TRAINING ###

**Face recognition DNN trained with 51M images** with validation accuracy of 97.71% using 8M images for validation. 

[[images/threshold1.png]]

### TRIPLET LOSS TRAINING GAINS 2.288% ACCURACY ###

**Triplet loss training then gains 2.288%** in accuracy resulting in an overall accuracy of 99.998%.

[[images/threshold2.png]]
Data visualization is from TensorFlow’s TensorBoard visualization toolkit

### CUTOFF ANALYSIS USING 10K RANDOM IMAGES ###

The cutoff analysis is then calculated using a random segment of the validation set.

This is used for a starting point on a multi-variable cutoff analysis.  We choose 10,000 random images from the validation set (public dataset) and measured DNN performance by accuracy, precision and recall. 

[[images/threshold3.png]] 

### THRESHOLD ANALYSIS ###

**Threshold** analysis using 9,900 random images from the validation dataset and 100 images from a private dataset. This analysis assists in further optimization considering min, mean and max thresholds in deriving the multi-value cutoff.

[[images/threshold4.png]]

**Line 746 (highlighted) provides 0.811 as the optimal threshold.**  
This results in an accuracy of 99.998%, 0 false positives and 6 (0.0006) false negatives. This is asymptotic to 100% accuracy.

The six images that failed during evaluation show that the model was unable to overcome blur + eyeglasses. Blur is added to the data to help generalize the model.  
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Failed6.png)

### ETHNIC, GENDER AND RACE BREAKDOWN
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Ethnic%20chart%203.png)
![](https://github.com/openinfer/PrivateIdentity/blob/master/images/Graph%20bw%20ethnic%20gender.png)
<pre>
Authors:  	Chung Nguyen PhD 
                Scott Streit, CTO
Data Run Date:  2 June 2020, 12:13AM
</pre>

