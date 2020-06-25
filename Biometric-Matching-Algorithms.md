# BIOMETRIC MATCHING ALGORITHMS

The Private Identity architecture is biometric modality agnostic. Private Identity uses two DNNs per modality and a set of helper DNNs for each biometric acquisition. Each modality has one pre-trained TensorFlow embedding model and one TensorFlow classifying model that work hand-in-hand to match subjects.  The first DNN and its associated helper DNNs acquire the biometric using the Biometric Acquisition Workflow and then discard (delete) the plaintext biometric after embedding creation.  

The second DNN, a custom Fully Connected Neural Network (FCNN), classifies each FHE and subsequently returns identity in polynomial time. It is capable of classifying an unlimited number of FHEs and returning identity in constant time when configured using load-balanced, elastic, fault-tolerant Kubernetes clusters.  Testing on GCP using 100,000 FHEs/second (approx. 8B authentications/day, or similar to the daily volume of Azure Active Directory) through cloud AI responded in constant time.  The second DNN runs in any AI cloud container or on-premise. 

## FACIAL RECOGNITION ALGORITHM
![Face recognition graphic](https://github.com/openinfer/PrivateIdentity/blob/master/images/Face%20Rec%20Algo%20v2.png)
* Provides absolute accuracy (99.99%) with nearly zero false positives (0.0001%)
* Recognizes faces using any general-purpose camera (webcams, phones) ≥256kB
* Enrolls an unlimited number of users (“unlimited gallery size”) using an ethnically balanced dataset 
* Operates in polynomial time irrespective of gallery size and without discrimination (race, age, gender)
* Trained using the VGG Face2 dataset ethnically balanced with the Asian-Celeb dataset 

### Minimum Imaging Requirements
Face ≥224×224 pixels. Camera ≥256kB. 
Face images smaller than 224×224 pixels may reduce performance. 

### Discrimination
An ethnically balanced dataset and a variety of homogenized lighting algorithms prevent discrimination based on age, gender or ethnicity. 

### Predict RESTful API
Accepts FHE input from the web client or the Encryption Engine. The API returns identity in 200ms constant time with unlimited throughput. 

### Enroll RESTful API
Accepts FHE input from the web client or the Encryption Engine. The API enrolls the subject in 800ms constant time with unlimited throughput. 

### Delete_Subject RESTful API
Accepts FHE input from the web client or the Encryption Engine and deletes identity.

## FACE+MASK RECOGNITION ALGORITHM

* Provides high accuracy (98%) with nearly zero false positives (0.0001%)
* Recognizes faces with masks using any general-purpose camera (webcams, phones) ≥256kB
* Enrolls an unlimited number of users (“unlimited gallery size”) using an ethnically balanced dataset 
* Operates in polynomial time irrespective of gallery size and without discrimination (race, age, gender)
* Trained using the VGG Face2 dataset ethnically balanced with the Asian-Celeb dataset 

### Minimum Imaging Requirements
Face ≥224×224 pixels. Camera ≥256kB. 
Face images smaller than 224×224 pixels may reduce performance. 

### Discrimination
An ethnically balanced dataset and a variety of homogenized lighting algorithms prevent discrimination based on age, gender or ethnicity. 

### Predict RESTful API
Accepts FHE input from the web client or the Encryption Engine. The API returns identity in 200ms constant time with unlimited throughput. 

### Enroll RESTful API
Accepts FHE input from the web client or the Encryption Engine. The API enrolls the subject in 800ms constant time with unlimited throughput. 
Delete_Subject RESTful API. Accepts FHE input from the web client or the Encryption Engine and deletes identity.

## FINGERPRINT RECOGNITION ALGORITHM  

* Provides absolute accuracy (99.99%) with nearly zero false positives (0.0001%) 
* Recognizes fingerprints using any general-purpose camera (webcams, phones) ≥4MP
* Matches in polynomial time irrespective of gallery size and without discrimination (race, age, gender)
* Trained using the NIST Special Database 4 and CASIA-FingerprintV5 

The DNN maintains full accuracy through real-world boundary conditions including poor lighting; camera positioning; expression; image rotation to 22.5°; distance; focus; blur and movement; 30% occlusions including scars, abrasions, and B/W and grayscale images. 

### Minimum Imaging Requirements
Fingerprint ≥224x224. Camera ≥4MP
Images smaller than 224x224 pixels may reduce performance.

### Discrimination
Private Identity HSL filters remove light absorption, skin contour and skin color as distractors and, when combined with a balanced training data set, ensure fairness across ethnic, gender and age groups.  

### Predict RESTful API
Accepts FHE input from the Web client or the Encryption Engine. The API returns identity in 200ms constant time with unlimited throughput. 

### Enroll RESTful API
Accepts FHE input from the Web client or the Encryption Engine. The API enrolls the subject in 800ms constant time with unlimited throughput. 
Delete_Subject RESTful API. Accepts FHE input from the Web client or the Encryption Engine and deletes identity.

## VOICE / SPEAKER IDENTIFICATION ALGORITHM

* Text-, language- and accent-independent voice identification with 1 second of audio
* Provides high accuracy (93%) with nearly zero false positives (0.0001%) 
* Matches in polynomial time irrespective of gallery size and without discrimination

### Minimum Audio Requirements
Voice ≥1 second. Audio ≥8.1kHz (telephone quality)
The minimum voice input size is 100ms. 

### Predict RESTful API
Accepts FHE input from the Web client or the Encryption Engine. The API returns identity in 300ms constant time with unlimited throughput. 

### Enroll RESTful API
Accepts FHE input from the Web client or the Encryption Engine. The API enrolls the subject in 800ms constant time with unlimited throughput. 

### Delete_Subject RESTful API
Accepts FHE input from the Web client or the Encryption Engine and deletes identity.
