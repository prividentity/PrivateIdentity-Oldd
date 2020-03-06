[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

**Q : What is a biometric?**

Biometrics is the technical term for body measurements and calculations. It refers to metrics related to human characteristics.

Biometrics authentication (or realistic authentication) is used in computer science as a form of identification and access control. It is important to note that privacy with biometrics is essential since biometric, in contrast to password, cannot be reset.

**Q : What is facial recognition?**

A facial recognition is face recognition technology measures and matches the unique characteristics for the purposes of identification or authentication.

Facial recognition is a category of biometric software that maps an individual's facial features mathematically and stores the data as a faceprint. The software uses deep learning algorithms to compare a live capture or digital image to the stored faceprint in order to verify an individual's identity.

**Q : What is a a CNN?**

Yann LeCun and Yoshua Bengio introduced the concept of CNNs in 1995. A con-volutional neural network is a feed-forward network with the ability of extracting topological properties from the input image. It extracts features from the raw image and then a classifier classifies extracted features. CNNs are invariance to distortions and simple geometric transformations like translation, scaling, rotation and squeezing.

Convolutional Neural Networks combine three archit ectural ideas to ensure some degree of shift, scale, and distortion invariance: local receptive fields, shared weights, and spatial or temporal sub-sampling. The network is usually trained like a stan-dard neural network by back propagation.

**Q : What is a fully connected neural network?**

In information technology, a neural network is a system of hardware and/or software patterned after the operation of neurons in the human brain. Neural networks -- also called artificial neural networks -- are a variety of deep learning technologies. Commercial applications of these technologies generally focus on solving complex signal processing or pattern recognition problems. Examples of significant commercial applications since 2000 include handwriting recognition for check processing, speech-to-text transcription, oil-exploration data analysis, weather prediction and facial recognition.

**Q : What is unique about Private Indentity Identification and Authentication?**

Biometrics have a long-held hope of replacing passwords by establishing a non-repudiated identity and providing authentication with convenience. Convenience drives consumers toward biometrics-based access management solutions. Unlike passwords, biometrics cannot be script-injected; however, biometric data is considered highly sensitive due to its personal nature and unique association with users. Biometrics differ from passwords in that compromised passwords may be reset. Compromised biometrics offer no such relief. A compromised biometric offers unlimited risk in privacy (anyone can view the biometric) and authentication (anyone may use the biometric). Standards such as the Biometric Open Protocol Standard (BOPS) (IEEE 2410-2016) provide a detailed mechanism to authenticate biometrics based on pre-enrolled devices and a previous identity by storing the biometric in encrypted form. This solution allows authentication and identification to occur in up to polynomial time, allowing for search in encrypted biometric stores with speed, accuracy and privacy.

**Q : What is enrollment?**

The act of signing/registration people up for participation is enrollment.

Since we have little control over devices such as cameras or sensors, the biometric template arrives as plaintext. If we encrypt it immediately and only process it as ciphertext, we have the maximum practical level of privacy. An important part of offering this highest level of privacy is a one-way encryption algorithm, meaning that given ciphertext, there is no mechanism to get to the original plaintext. Many one-way encryption algorithms exist, such as MD5 and SHA-512. However, these algorithms are not homomorphic. This means we cannot do a closeness match between two ciphertext vectors using Euclidean measurements. Private Identity offers a general purpose solution that produces biometric ciphertext that is Euclidean-measurable. We do this using a Neural Network. We then apply a classification algorithm to allow for one-to-many identification. This solution maximizes privacy and runs between O(1) and O(log⁡(n)) time.

Enrollment is the act of introducing a Subject to the indentification or authenication system. Enrollment, for Open Inference, is the process of extracting features and training a neural network for a particular subject. For Enrollment to work reliably, we give as mnay biometric instances as possible. We use in excess of 10 images, which the software morphs into 250 distinct images. The system then trains on 250 images. All of the training and images are encrypted BEFORE any form of training guaranteeing full privacy.

**Q : What is search?**

Search is a prediction across a trained neural network. Artificial neural networks respond to a prediction request by querying a neural network. The network responds with an accurate response as to who is the subject based on an encrypted search.

**Q : What is voting?**

For voting, we take several searches and the correct answer is the response with plurality. For example, we take 3 facial images. The neural network is 99 percent accurate. So we use the three images and simultaneously search. There is a 1 percent chance we are wrong, voting makes our result 100 percent accurate.

**Q : What is tensorflow?**

TensorFlow is an open source software library for numerical computation using data flow graphs. Nodes in the graph represent mathematical operations, while the graph edges represent the multidimensional data arrays (tensors) communicated between them. The flexible architecture allows you to deploy computation to one or more CPUs or GPUs in a desktop, server, or mobile device with a single API. TensorFlow was originally developed by researchers and engineers working on the Google Brain Team within Google's Machine Intelligence research organization for the purposes of conducting machine learning and deep neural networks research, but the system is general enough to be applicable in a wide variety of other domains as well.

**Q : What is a feature vector?**

A feature vector is an n-dimensional vector of numerical features that represent some object. Many algorithms in machine learning require a numerical representation of objects, since such representations facilitate processing and statistical analysis.

**Q : What is alignment?**

For biometrics to train properly the biometric itself must make it easy to train. If all biometrics are similarly reprsented, then the training is more accurate. We do thisby preprocessing the biometric which involes aligning.

In computer vision, alignment: is the process of finding the spatial mapping, i.e. elements in one image into meaningful correspondence with elements in a second image.

**Q : What is cropping?**

Cropping is the removal of the outer parts of an image to improve framing, accentuate subject matter or change aspect ratio.