### TEMPLATE-BASED BIOMETRIC MATCHING

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(13).png)

_(From top to bottom, Template-Based Matching, Cloud-Based Biometric Matching, Private Identities Solution)_


Today, biometric recognition systems operate using either template matching (the most common approach, 2003-present) or Cloud-based Deep Neural Networks (2017-present).  Biometric recognition systems based on template matching operate by (1) storing the features extracted from an original biometric as templates in the system's database and then (2) matching the template features with those extracted from the biometric information presented during subsequent authentication attempts. 

Template matching systems pose a significant threat to biometric privacy through loss of the biometric template information by direct information exposure (e.g. employee error, other unintentionally methods, or by hackers, malware and other malicious methods). Most attempts to shield the biometric from adversarial attacks in such systems involve storing the templates in a decentralized fashion or divided in half (e.g. visual cryptography); however, these solutions require a decryption prior to a plaintext match, making these schemes infeasible for both privacy and 1:many identification.
</br>

### CLOUD-BASED BIOMETRIC MATCHING

Cloud-based Deep Neural Networks‎ (DNNs), specifically Convolutional Neural Networks (CNNs), provide significant performance advances over template matching. These systems expand the range of applications which use facial recognition through performance improvements, cost savings and easy implementation.  Improvements include near-perfect 99.9% identification rates for enrolled subjects and one-tenth the enrollment-error rates experienced by less advanced (template-based) facial recognition tools.

With regard to privacy, cloud-based DNNs require plaintext biometric information to operate and pose an equal or greater threat to biometric privacy as compared to template matching systems. Similar to template matching systems described above, the loss of biometric data may occur through direct information exposure (e.g. employee error, hackers, or malware). Further privacy loss of the training data is possible on each training cycle because training involves plaintext images stored in the cloud.

### The Private Identity Solution

FHE techniques pioneered by Private Identity offer significant performance and privacy advances over previous solutions. The Private Identity recognition algorithm improves speed and accuracy, reduces false positive error rates to nearly zero, and fully preserves and offers the highest level of privacy by conducting encrypted match and search operations on an encrypted dataset using 1-way hash (embedding, or vector encryption). This eliminates the everpresent security vs. privacy tradeoff inherent in previous security solutions.  

To accomplish this, Private Identity uses one pre-trained TensorFlow embedding DNN per biometric modality and a set of helper DNNs for biometric acquisition.  These DNNs acquire the biometric using the Biometric Acquisition Workflow and then discard (delete) the plaintext biometric after embedding creation. 

A second set of classifying DNNs match and search subjects in the encrypted space. These DNNs classify an unlimited number of FHEs and return identity in constant time when deployed on load-balanced, elastic, fault-tolerant Kubernetes clusters and Cloud AI services. Testing at 100,000 FHEs/second (simulating 8B authentications/day, or similar to the daily volume of Azure Active Directory) using the above configuration responds in constant time.  


