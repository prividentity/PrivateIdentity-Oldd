# Installation

## Python Version

Private ID® supports Python 3.6 or greater. 

## Dependencies

Private ID has dependencies on numpy, scipy and Pillow for image processing. These distributions will be installed automatically. Private ID detects and uses numpy, scipy and Pillow if they are already installed.

-   [Numpy](https://pypi.org/project/numpy/)  provides functions for array wise image manipulation.
    
-   [Pillow](https://pypi.org/project/Pillow/)  provides functionalities for reading the Image and converting to required formats.
    
-   [Scipy](https://pypi.org/project/scipy/)  provides a faster, more efficient method for comparison of distances and supports shared library functionalities.
    
## Install Private ID PIP package

Within the Python3 environment, use the following command to install the Private ID Python SDK:

    pip3 install https://privid-sdk.s3.us-east-2.amazonaws.com/privateid/privateid-1.1.0-py3-none-any.whl

## Upgrade Private ID PIP package

To upgrade the PrivateID version, use the following command:

    pip3 install --force-reinstall --no-cache https://privid-sdk.s3.us-east-2.amazonaws.com/privateid/privateid-1.1.0-py3-none-any.whl

# Install facial recognition Python SDK

This section covers how to use a factor SDK for generating and verifying identity.

The following section explains how the face factor can be used.

	from privateid.FHE impotr Factor

	face_factor = Factor(modality=["face"], server_url=SERVER_URL, api_key=API_KEY, local_storage_path=None)
    
	Optional - local_storage_path

The **Factor class** implements the methods for enrolling and predicting.
It exposes five methods as part of the interface:

1. enroll: Enrolls the user.

2. predict: Predicts the user.

3. is_valid: Verifies the file is valid.

4. delete: Deletes the enrollment of the user.

5. compare: Compare two factors for verification.
    
## PARAMETERS
 - modality : list
	 - List of factors that can be used. "face", "voice", "fingerprint"

 - server_url : str
	 - The URL of the server.

 - local_storage_path : str (OPTIONAL)
	 - Absolute path to the local storage.

 - api_key: str
         - The API key for using the services.

 - RETURNS
	 - OBJECT
		 - Instance of the Factor class.

## METHODS
| Method                                | Desc                                                    |
| ------------------------------------- | ------------------------------------------------------- |
| `is_valid`(image_path)                | Check if the image is valid                             |
| `enroll`(image_path)                  | Enrolls the image in the face recognition server        |
| `predict`(image_path)                 | Predicts the image in the face recognition server       |
| `delete`(uuid)                        | Deletes the enrollment from the face recognition server |
| `compare`(image_path_1, image_path_2) | Check if the images are of same person or not           |

**`delete(uuid:  str)  →  object`**

Deletes the enrollment from the face recognition server

 - PARAMETERS
	 - **UUID**
		 - UUID of the enrolled image
 - RETURNS
	 - Response Object
	 	- status : str - status of the operation
		- message: str - response message from the operation


**`enroll([...image_path]:  list)  →  object`**

Enrolls the image(s) in the face recognition server

 - PARAMETERS
	 - **IMAGE_PATH**: List
		 - List of firectory path to the image file(s)

 - RETURNS
	 - Response Object
	 	- status : int - status of the operation
		- uuid : str - Enrolled UUID
		- guid : str - Enrolled GUID
		- message: str - response message from the operation
		- enroll_level : int - Enroll Level
		- factor: list - "face"/"voice"/"fingerprint"

**`is_valid(image_path:  str)  →  object`**
Check if the image is valid for using in the face recognition

 - PARAMETERS
	 - **IMAGE_PATH**
		 - Directory path to the image file
 - RETURNS
	 - Response Object
	 	- status : int - return code of the operation
	 	- conf_score: float - Confidence score of the file
	 	- conf_score_threshold: float - Threshold used for confidence score
		- result: str - response message from the operation

**`predict(image_path:  str, k: int)  →  object`**
Predicts the image in the face recognition server

 - PARAMETERS
	 - **IMAGE_PATH**
		 - Directory path to the image file
     - **K (OPTIONAL)**
		 - Number of closest search to be retrieved (Default - 1)
 - RETURNS
	 - Response Object
	 	- status : int - return code of the operation
		- message: str - response message from the operation
		- enroll_levels: list - List of enroll levels
		- uuids : list - List of UUIDs
		- guids : list - List of GUIDs
		- probability_score : list - Confidence level of the prediction

**`compare(self, image_path_1: str_, image_path_2: str_) → object`**
Compare two faces for verification 

- PARAMETERS
	 - **IMAGE_PATH_1**
	 	 - Directory path to the image file 1
	 - **IMAGE_PATH_2**
	 	 - Directory path to the image file 2
- RETURNS
	 - Response Object
	 	- status : int - return code of the operation
	 	- result: str - response message from the operation
	 	- conf_score : float - Confidence score of the result
	 	- conf_score_threshold: float - Threshold used for confidence score
		- distances : list - [min , mean, max] of the comparison
		- distance_threholds : list - [thres_min , thres_mean, thres_max] of the comparison

## Virtual environments (optional)

Use a native Python environment from your OS or a virtual environment to manage the dependencies for your project, both in development and in production. This section addresses use of a virtual environment.

What problem does a virtual environment solve? The more Python projects you have, the more likely it is that you need to work with different versions of Python libraries, or even Python itself. Newer versions of libraries for one project can break compatibility in another project.

Virtual environments are independent groups of Python libraries, one for each project. Packages installed for one project will not affect other projects or the operating system’s packages.

Python comes bundled with the  `venv`  module to create virtual environments.

### Create an environment

Create a project folder and a  `venv`  folder within:

    mkdir myproject
    cd myproject
    python3 -m venv venv

On Windows:

    py -3 -m venv venv

### Activate the environment

Before you work on your project, activate the corresponding environment:

    . venv/bin/activate

On Windows:

    venv\Scripts\activate

Your shell prompt will change to show the name of the activated environment.

### Return Codes and Message Desciprtions

| Return Code | Return Message / Error Description                                                                     |
| ----------- | ------------------------------------------------------------------------------------------------------ |
| 0           | Valid Image                                                                                            |
| 1           | Face is an image of an image (spoof). Please only provide live facial image(s). (Under implementation) |
| 2           | Face is an image of a video (spoof). Please only provide live facial image(s). (Under implementation)  |
| 3           | Face in image is too close to the camera. Please move away from the camera.                            |
| 4           | Face in image is too far away.                                                                         |
| 5           | Face in image is too far to the right.                                                                 |
| 6           | Face in image is too far to the left.                                                                  |
| 7           | Face in image is too high.                                                                             |
| 8           | Face in image is too low.                                                                              |
| 9           | Face in image is too blurry.                                                                           |
| 10          | Please remove eyeglasses during registration.                                                          |
| 11          | Please remove face mask during registration.                                                           |
| 12          | Head in image turned too far toward the left/right. Please face the camera.                            |
| 13          | Head in image turned too far up/down. Please face the camera.                                          |
| 14          | Reserved for future use.                                                                               |
| 15          | Reserved for future use.                                                                               |
| 16          | No face found in image.                                                                                |
| 17          | API Error                                                                                              |
| 18          | Local Storage Error                                                                                    |
| 19          | Memory Error                                                                                           |