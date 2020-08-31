
### Enrollment Morphing

The morphing process during enrollment is crucial as this is used to compare the images during prediction. The data that has been presented to the system during Enroll has to be processed robust enough to make it work under all conditions. The following content describes in detail the various techniques applied during the enroll phase. The following workflow diagram gives a general overview of how the model categorizes and process the captured image.

#### Data Augmentation

Data augmentation refers to the process of manipulating the presented images to various conditions to significantly increase the diversity of data. This increase in diversity helps us make the enrollment process more reliable and less error-prone. A list of morphing techniques applied to the enroll images is described below.

![Face Detection Workflow](https://github.com/openinfer/PrivateIdentity/blob/master/images/face_detection_workflow.png)

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