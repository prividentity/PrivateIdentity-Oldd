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

# Install facial recognition Python SDK

This section covers how to use facial recognition SDK for generating and verifying identity.

    class privateid.FHE.FaceFactor(server_url,local_storage_path=None)

The **FaceFactor class** implements the methods for enrolling and predicting.
It exposes four methods as part of the interface:

1. enroll: Enrolls the face of the user.

2. predict: Predicts the face of the user.

3. is_valid: Verifies the face of the user.

4. delete: Deletes the enrollment of the user.

5. compare: Compare two faces for verification (To be implemented).
    
## PARAMETERS

 - URL : STR
	 - The URL of the FaceFactor server.

 - LOCAL_STORAGE_PATH : STR (OPTIONAL)
	 - Absolute path to the local storage.

 - RETURNS
	 - OBJECT
		 - Instance of the FaceFactor class.

## METHODS
|Method| Desc  |
|--|--|
| `is_valid`(image_path) | Check if the image is valid |
| `enroll`(image_path) | Enrolls the image in the face recognition server |
| `predict`(image_path) | Predicts the image in the face recognition server |
|`delete`(uuid) | Deletes the enrollment from the face recognition server |
|compare(image_path_1, image_path_2) | To be implemented |

**`delete(_uuid:  str)  →  dict`**

Deletes the enrollment from the face recognition server

 - PARAMETERS
	 - **UUID**
		 - UUID of the enrolled image
 - RETURNS
	 - DICT - Status and message of the operation.
		 - SUCCESSFUL OPERATION: 
	{
    “status”: 0, “message”: “OK”
    }
		 - UNSUCCESSFUL OPERATION:
{
“status”: -1, “message”: “error message”
}

**`enroll(_image_path:  str)  →  dict`**

Enrolls the image in the face recognition server

 - PARAMETERS
	 - **IMAGE_PATH**
		 - Directory path to the image file
 - RETURNS
	 - DICT - Status and message of the operation.
		 - SUCCESSFUL OPERATION: 
	{
    “status”: 0, “message”: “success”, “uuid”: UUID
    }
		 - UNSUCCESSFUL OPERATION:
{
“status”: -1, “message”: “error message”
}

**`is_valid(_image_path:  str_)  →  dict`**
Check if the image is valid for using in the face recognition

 - PARAMETERS
	 - **IMAGE_PATH**
		 - Directory path to the image file
 - RETURNS
	 - DICT - Status and message of the operation
		 - SUCCESSFUL OPERATION:
{
“status”: 0, “message”: “Valid image”
}
		 - UNSUCCESSFUL OPERATION:
{
“status”: -1, “message”: “Invalid image”
}

**`predict(_image_path:  str_)  →  dict`**
Predicts the image in the face recognition server

 - PARAMETERS
	 - **IMAGE_PATH**
		 - Directory path to the image file
	 - RETURNS
		 - DICT - Status and message of the operation.
			 - SUCCESSFUL OPERATION:
{
‘status’: 0, ‘message’: ‘success’, ‘uuid’: UUID
}
			 - UNSUCCESSFUL OPERATION:
{
“status”: -1, “message”: “error message”
}

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