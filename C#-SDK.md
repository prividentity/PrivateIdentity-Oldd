

# C# SDK

## Installation

This SDK requires *Microsoft Visual Studio IDE*. Requires following Visual Studio IDE components to be installed:
* Microsoft Visual Studio C# Tools
* Microsoft Visual Studio C++ Tools

The IDE projects in this package is tested with:
- [x] Visual Studio 2019
- [x] Visual Studio 2022. 

## Dependencies

* The project files uses following packages
* Newtonsoft.Json version=13.0.1 
* RestClient.Net  version=5.0.7
* RestSharp version=107.2.1 
* Magick.NET.Core version=9.1.2
    
## Install Private ID package

Extract the package <link here...todo>

## Upgrade Private ID package

Extract the package <link here...todo>

# Install facial recognition C# SDK

This section covers how to use facial recognition SDK for generating and verifying identity.

## Constructor 
``` csharp
    public privid_fhe_face(string _server_url, string local_storage_path, string _api_key, int verbosity)
```

* _server_url: string
	 - The URL of the FaceFactor server.

* local_storage_path: string 
	 - Path to the local storage.

* _api_key : string
	 - API key obtained from AWS Marketplace 

* verbosity
	 - Verbose level or Debug message level. 0 - minimum messages and 3 - the maximum level

* Return - Instance of the privid_fhe_face class

The **privid_fhe_face** implements the methods for enrolling and predicting.
It exposes five methods as part of the interface:

## Enroll
Enrolls the image in the face recognition server.
``` csharp
public bool enroll(System.Drawing.Image imageIn)
```
* imageIn - Directory path to the image file
* Return - Status and message of the operation. 0 - Successful operation. -1 or -2 - Enroll operation failed. 

## Predict
Predicts the image in the face recognition server.
``` csharp
public bool predict(System.Drawing.Image imageIn, int k)
```
* imageIn - Directory path to the image file
* k - this value shall be 0 < k < 11, default = 1
* Return - Status and message of the operation. 0 - Successful operation. -1 or -2 - Predict operation failed. 
* Prints - UUIDs and respective probabilities for each k. 
## Is Valid
Check if the image is valid
``` csharp
public bool is_valid(System.Drawing.Image imageIn)
```
* imageIn - Directory path to the image file
* Return - Status and message of the operation.
## Delete
Deletes the enrollment from the face recognition server. 
``` csharp
public int delete(string uuid)
```
* uuid - UUID of the enrolled image
## Compare Images
Compare two faces for verification.
``` csharp
public int compare_files(System.Drawing.Image imageInA, System.Drawing.Image imageInB, int option)
```    
* imageInA and imageInB  - Path to the image files to be compared 
* option - verbosity option 

* Return - Compare result. 0 - imageInA is of same person as that of imageInB; 1 - if different 

## METHODS
|Method| Desc  |
|--|--|
| `is_valid` | Check if the image is valid |
| `enroll`  | Enrolls the image in the face recognition server |
| `predict` | Predicts the image in the face recognition server |
| `delete`  | Deletes the enrollment from the face recognition server |
| `compare_files`  |  Compare two faces for verification |

# Sample Application 

``` csharp
    string folder_name_local_storage = "privid_local_storage1";
        string server_url = "https://priv.id/node";
        string api_key = "16310cf0bf46168129f2";
        int k_factor = 3;

    privid_fhe_face privid_fhe_face1 = new privid_fhe_face(server_url, folder_name_local_storage, api_key, option);
 
    image_in = Image.FromFile(args[0]);
    bool valid_result = privid_fhe_face1.is_valid(image_in);

    image_in = Image.FromFile(args[0]);
    bool enroll_result = privid_fhe_face1.enroll(image_in);

    image_in = Image.FromFile(args[0]);
    bool predict_result = privid_fhe_face1.predict(image_in, k_factor);

    int delete_result = privid_fhe_face1.delete(args[0]);

    Image a = FixedSize(Image.FromFile(args[0]), imWidth, imHeight);
    Image b = FixedSize(Image.FromFile(args[1]), imWidth, imHeight);
    int compare_result = privid_fhe_face1.compare_files(a, b, 0);
    Console.WriteLine("compare_result = {2}, Images {0} and {1} are {3}", args[0], args[1], compare_result, compare_result == 0 ? "the same" : "different");
``` 

# Test Procedure 
