[![logo-name](https://www.private.id/static_home/images/Private-Identity-Logo-1.png)](https://www.private.id/)

<br/>


### Introduction 
 Private Identity® was founded in Washington, D.C. by Mike Pollard and Scott Streit in 2017 to develop fully homomorphic encryption. Private Identity’s small team of top computer scientists and ML engineers converged on the AI/ML/FHE security solution in early 2018. The company applied for cryptography patents in 2018 and collaborated with Google’s TensorFlow® team in 2019 to bring FHE to the edge. USPTO granted patents in 2019 and 2020 to Private Identity for encrypted enrollment, encrypted match, encrypted search and incremental training for all biometric modalities. Additional patents are pending worldwide. 

Fully homomorphic encryption (FHE) benefits society by ensuring full privacy. The Private Identity recognition algorithm uses FHE to enable encrypted match and search operations on an encrypted dataset without any requirement to store, transmit or use plaintext biometrics or biometric templates. The biometric data is irreversibly anonymized using a 1-way cryptographic hash algorithm (embedding, or vector encryption) and then discarded without the data ever leaving the local device. 

FHE also provides significant performance and efficiency benefits in addition to full privacy. FHE increases the Private Identity recognition algorithm’s accuracy, speed and efficient compute. FHE also reduces the recognition algorithm’s false positive rate to nearly zero (0.0001%) and reduces data flows to the cloud by 99.5%. 
The Private Identity solution implementation follows ML best practices. The face, face with mask, voice and fingerprint recognition models are small (3MB, 3MB and 900kB, respectively) and use MobileNetV2 architecture. The face model operates with 0.2% non-overlapping subspaces of the entire embedding space (0.2% overlap). Similarly, the fingerprint model has a 3% overlap and the voice model has an 8% overlap.  The face and fingerprint models accommodate 20-30% occlusion to the original biometric and while maintaining the same accuracy as non-occluded biometrics. 

The Private Identity solution is available as SaaS or PaaS on GCP, AWS and on-premises. Private Identity provides pre-configured SaaS enterprise integrations for Google Identity®, PING Identity®, Okta® Factor Authentication, SAML 2.0, OAuth/OIDC, WebAuthn, Azure® Active Directory and AWS® IAM. 

For PaaS integrations on GCP, the solution leverages TensorFlow.js, Cloud AI Platform, Cloud Compute, K8s Engine, Memory Store (Redis), MySQL clustered & fault tolerant, Cloud Storage buckets & data lakes, Cloud Speech to Text, Cloud Vision API, Cloud DNS and Cloud Identity.  Similarly, for PaaS integrations on AWS, the solution leverages TensorFlow.js, Sagemaker, Compute, EKS, In Memory Store (Redis), MySQL clustered & fault tolerant, S3, AIM, and Cloud Speech to Text, Cloud Vision API and Route 53. 

<br/>

### Background

If a username, token or password is lost or stolen, it can be canceled and replaced with a different one. Biometrics, however, cannot be canceled or replaced. For that reason, it is of utmost importance that biometric systems maintain privacy and confidentiality.  Most such systems do not maintain privacy.  

Researchers have spent decades attempting to build privacy preserving security systems using homomorphic encryption. To date, Private Identity is the only firm to launch a real-time fully homomorphic security system.  In 1978, Rivest, Adleman and Dertouzos at MIT were the first to propose maintaining privacy by performing mathematical operations on encrypted data (FHE). Thirty years later, Dr. Craig Gentry described the first FHE scheme using lattice-based cryptography.  In 2015, the MIT Lincoln Laboratory with US Government funding demonstrated the first use of FHE in the laboratory to control data sharing. In 2017, the US Government launched the homomorphic encryption HECTOR R&D program and reported that law enforcement agencies and private sector companies may, “leverage these new forms of [encrypted] Personal Identifying Information (PII) without encroaching on civil liberties…” 

In October 2019, Dr. Clayton Stewart at University College London tested the performance and privacy of the algorithm. The Stewart paper is here [Link](https://drive.google.com/file/d/15oLgujDI6MG1ICi8phCEubtppiR5fmh8/view)


<br/>


### Technical details

There is a comparison between the methods of [Biometric Matching](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Matching-Methods), such as [Template-Based Biometric Matching](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Matching-Methods#Template-Based-Biometric-Matching) and [Cloud-Based Biometric Matching](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Matching-Methods#Cloud-Based-Biometric-Matching), and the [Private Identity Solution](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Matching-Methods#The-Private-Identity-Solution) to biometric matching and while each have a similar yet different approach, Private Identity's solution is the only one to comply [Biometric Privacy and Data Privacy](https://github.com/openinfer/PrivateIdentity/wiki/Biometric-Privacy-and-Data-Privacy) standards

![](https://github.com/openinfer/PrivateIdentity/blob/master/images/White%20Paper%20(14).png)

For Private Identities software to operate, the client-side device: (1) acquires and pre-processes plaintext biometrics; (2) utilizes a pre-trained CNN to create 4kB, 1-way encrypted, Euclidean measurable biometric feature vectors that can be safely stored and operated locally or in the Cloud; and (3) then discards the plaintext biometric data since it is no longer needed.

The client-side software has a small footprint, requires a 1MP camera (or better) for facial recognition and does not require training on the device. The solution supports most client devices including phones, tablets, iPod Touch, PCs, IoT devices, Apple Watch and TV (using voice) and can be embedded in firmware.

The DNN maintains full accuracy during boundary cases such as poor lighting or less-than-ideal subject positioning.

<br/>

### Basic Architecture

[[images/cluster_image.png]]

The [Client Applications](https://github.com/openinfer/PrivateIdentity/wiki/Client-applications) are responsible for:
* Creation of the biometric feature vector. 	
* Making an API call to [enroll](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#API-Enroll-Overview).	
* Making an API call to [predict](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#predict-overview).  
* Making an API call for [liveness](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#liveness-overview).


The [SPB Server](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#sbp-api-overview) is responsible for:
* Saving Enrollment Data during [enrollment](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#API-Enroll-Overview) process for subsequent [predict](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#predict-overview) API calls. 
* Retrieving Enrollment Data to support the [predict](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#predict-overview) API call.  
* Retrieving the probability that the [liveness](https://github.com/openinfer/PrivateIdentity/wiki/ieee-2410-standard-for-biometric-privacy-(SBP)-server#liveness-overview) data and result match.

### Enrollment Morphing

The morphing process during enrollment is crucial as this is used to compare the images during prediction. The data that has been presented to the system during Enroll has to be processed robust enough to make it work under all conditions. The following content describes in detail the various techniques applied during the enroll phase.

#### Data Augmentation

Data augmentation refers to the process of manipulating the presented images to various conditions to significantly increase the diversity of data. This increase in diversity helps us make the enrollment process more reliable and less error-prone. A list of morphing techniques applied to the enroll images is described below.

#### Geometry

This morphing technique takes advantage of the various transformations that can be achieved by manipulating the geometrical properties of the image. Below you can see the original image used for morphing followed by their augmentation samples.

![Bach Original](https://github.com/openinfer/PrivateIdentity/blob/master/images/bach.jpg)

* Flipping

Flipping can be generated by a mirror-reversal of an original image across a defined axis (usually horizontal).

![Bach Flipped](https://github.com/openinfer/PrivateIdentity/blob/master/images/sample_aug_4910.png)

* Rotation

Rotation of the image can be achieved by applying an affine transformation to the image. The degree of the rotation can be controlled during the transformation by specifying the degree level.

![Bach Rotated](https://github.com/openinfer/PrivateIdentity/blob/master/images/sample_aug_2541.png)

* Brightness

A random value of brightness can be applied to the original image to vary the overall lightness or darkness of the image. This technique makes the enrollment robust to different lighting conditions to some extent.

* Zoom

Zoomness on the image is another affine transformation technique that can be applied to alter the object closeness to the naked eye. One or more techniques can be applied to a single image resulting in a composite morphed image.

![Bach brightness](https://github.com/openinfer/PrivateIdentity/blob/master/images/sample_aug_4844.png)

#### Color & Contrast:

Apart from the geometrical transformations that can be applied to the image, the color & contrast plays a major role in enhancing the properties of the image. The color of the image refers to the values that represent and measure the intensity and chrominance of the light.  A color image has three values(or channels) per pixel. The contrast of the image is the difference in luminance or color that makes an object distinguishable.

#### RGB & HSL:

RGB colors are made up of a set of three values between 0 and 255. These can be represented as either RGB(255, 255, 255) or, it's hexadecimal equivalent, #ffffff (ff being equal to 255 in base 16).

These values can be mapped neatly in 3D, where each axis represents a different color value - usually represented as a cube. The coordinate (0, 0, 0) represents the color black in the bottom corner and the coordinate (255, 255, 255) represents white in the top corner. The other corners are the base colors (where one value is 255 and the other two are 0) pure red, green, and blue and their counterparts cyan, magenta, and yellow (where two values are 255 and the other is 0).

HSL was created as a way to easily compute saturation and lightness from a given hue (or, alternatively, to create a color of a different hue but the same saturation or lightness). It is also made up of three values: hue - given a value between 0 and 360 - saturation, and lightness - both given a value between 0 and 1 (or often as a percentage value)

HSL can also be represented as a 3D geometry. However, it is represented as a cylinder instead of a cube. Lightness is represented by the height of the cylinder, hue by the angle around the cylinder, and saturation by the distance from the center of the cylinder along a line of the radius.

Our morphing technique alleviates the information provided by the luminance channel of the HSL color space to make robust augmentations. These augmentations significantly reduce the errors in different lighting conditions.
Two methods discussed below were applied for morphing during the enrollment as well as the prediction process.

##### Histogram Equalization (HE)

A histogram is a representation of the intensity distribution of an image. In simple terms, it represents the number of pixels for each intensity value.

Histogram Equalization is an image processing technique primarily used to improve contrast in images. It achieves this by effectively spreading out the most frequent intensity values, i.e. stretching out the intensity range of the image. This method usually increases the global contrast of images. This allows for areas of lower local contrast to gain a higher contrast.

Our first morphing technique relies on performing HE on the luminance channel of the HSL color space of the image. The resulting image will then be combined with the unmodified Hue and Saturation channel to get a color image for processing. The sample image below illustrates the resulting image after applying the HE.

![HLS HE](https://github.com/openinfer/PrivateIdentity/blob/master/images/hls.jpg)

##### Contrast Limited Adaptive Histogram Equalization (CLAHE)

Adaptive histogram equalization (AHE) is an image-processing technique used to improve contrast in images. It differs from ordinary HE in the respect that the adaptive method computes several histograms, each corresponding to a distinct section of the image, and uses them to redistribute the lightness values of the image. It is therefore suitable for improving the local contrast and enhancing the definitions of edges in each region of an image.

CLAHE is an advancement on Adaptive Histogram Equalization(AHE). AHE has a drawback of overamplifying noise. CLAHE limits the amplification by clipping the histogram at a predefined value (called clip limit) before computing the Cumulative Distribution function. The sample image below illustrates the resulting image after applying the CLAHE.

![Bach CLAHE](https://github.com/openinfer/PrivateIdentity/blob/master/images/clahe.jpg)