

# Install facial recognition C# SDK

## IDE Installation

This SDK requires *Microsoft Visual Studio IDE*. Requires following Visual Studio IDE components to be installed:
* Microsoft Visual Studio C# Tools
* Microsoft Visual Studio C++ Tools

The IDE projects in this package is tested with:
- [x] Visual Studio 2019
- [x] Visual Studio 2022 

* The project files uses following packages
* Newtonsoft.Json version=13.0.1 
* RestClient.Net  version=5.0.7
* RestSharp version=107.2.1 
* Magick.NET.Core version=9.1.2

## Dependencies

None.
    
## Install Private ID package

* Extract the package [prividModuleApp - 1.2.6.zip](https://github.com/openinfer/PrivateIdentity/blob/master/prividModuleApp%20-%201.2.6.zip)
* Open the ./prividModuleApp 1.2.6/prividModuleApp.sln in Visual Studio IDE
* Update the NuGet Package as described below.
* License 
[AWS EULA Template (2020.11.20) (Private Identity).pdf](https://github.com/openinfer/PrivateIdentity/files/8132683/AWS.EULA.Template.2020.11.20.Private.Identity.pdf)

## Upgrade Private ID package

Use Visual Studio IDE _Manager NuGet Packages_ Option OR Invoke Package Manager from .NET CLI with following command:

``` shell
Install-Package privid_fhe_cs -Version 1.2.6
```
# Using facial recognition C# SDK

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

## Sample Application 

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

# Test facial recognition C# SDK 
## Typical Machine Configuration 
* Operating System - Microsoft Windows 10 Or Windows 11 64-bit .NET Framework 4.6.1
* CPU - Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz   
* RAM - 3.19 GHz with 16.0 GB
## Perform Health Check
To verify that the system is up. Calls all APIs and prints the status in Console.

``` bat
test_case1.bat
``` 
The sample output is :
``` bat
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
FHE_enroll_predict ok, ret = -1
Contacting server https://priv.id/node/predict ...
    idx   uuid                                                               probability
    -----+------------------------------------------------------------------+-----------
    00000 0c762c12ef64de292482eaef2ddca0ab9a6d372b917032e61b154759e8d3dae074 100.00
    00001 -1 0.00
    00002 -1 0.00
    -----------------------------------------------------------------------------------

C:\Users\SPL\test_face\test_face_ver8>test_case1.bat

C:\Users\SPL\test_face\test_face_ver8>.\\bin\\Debug\\prividModuleApp.exe .\\img\\a1.png 0 predict
Test PrividModule with C# interface, version 2111.1, predict :

INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
FHE_enroll_predict ok, ret = -1
Contacting server https://priv.id/node/predict ...
    idx   uuid                                                               probability
    -----+------------------------------------------------------------------+-----------
    00000 0c36910c39943d15db5c5896af9701e7f8e8500f9c5f8d61e0aa2a73f5db09710d 100.00
    00001 -1 0.00
    00002 -1 0.00
    -----------------------------------------------------------------------------------

C:\Users\SPL\test_face\test_face_ver8>.\\bin\\Debug\\prividModuleApp.exe .\\img\\a1.png 0 enroll
Test PrividModule with C# interface, version 2111.1, enroll :

INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
FHE_enroll_predict ok, ret = -1
Contacting server https://priv.id/node/enroll ...
    uuid = 0c36910c39943d15db5c5896af9701e7f8e8500f9c5f8d61e0aa2a73f5db09710d
    guid = 0c1b7cd13776c14dcf0229afb79a1fb68b8745b9bf44b1ca3edab52f134179a841
    ++++++  Person exists in system skipping enroll.  ++++++
``` 
## API Tests
### Is Valid
``` bat
.\bin\Debug\prividModuleApp.exe  ./img/a1.png 0 is_valid
``` 
``` bat
Test PrividModule with C# interface. C++ DLL version 2111.1, C# Wrapper DLL version 1.2.6.0,
 Testing is_valid with a1.png:

INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
     PRIV_FHE :     [Thresholds] result[24] = 0.983136  conf_score_thr = 0.500000
     PRIV_FHE :     [Thresholds] conf_score_thr = 0.500
is_valid ok, ret = 0
     RESULT  : valid_result for Image a1.png is = 0 - Valid Image
``` 
## Results

| *Return Value*  | *Results/Error Description* |
| ------------- | ------------- |
| 0 | Valid Image |  
| 1 | ~Face is an image of an image (spoof),  ensure that you provide live facial image(s)~ |  
| 2 | ~Face is an image of a video (spoof),  ensure that you provide live facial image(s)~ |  
| 3 | Face in image is too close to the camera,  Please move away from the camera |  
| 4 | Face in image is too far away |  
| 5 | Face in image is too far to the right |  
| 6 | Face in image is too far to the left |  
| 7 | Face in image is too high |  
| 8 | Face in image is too low |  
| 9 | Face in image is too blurry |  
| 10 | Eyeglass Detected. Please remove eyeglasses during registration |  
| 11 | Face Mask Detected. Please remove face mask  during registration |   
| 12 | Head in image turned too far toward the left/right. Please face the camera |  
| 13 | Head in image turned too far toward the up/down. Please face the camera |  
| 14 | Reserved |  
| 15 | Reserved |  
| -1 | No face found in image |  
| -10 | API Error |  
| -11 | Local Storage Error |  
| -20 | Memory Error |

### Enroll

``` bat
.\bin\Debug\\prividModuleApp.exe a1.png 0 enroll
``` 
``` bat
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
FHE_enroll_predict ok, ret = -1
Contacting server https://priv.id/node/enroll ...
    uuid = 0c36910c39943d15db5c5896af9701e7f8e8500f9c5f8d61e0aa2a73f5db09710d
    guid = 0c1b7cd13776c14dcf0229afb79a1fb68b8745b9bf44b1ca3edab52f134179a841
    ++++++  Person exists in system skipping enroll.  ++++++
### Predict
```

``` bat
.\bin\Debug\prividModuleApp.exe a1.png 0 predict
``` 
``` bat
Test PrividModule with C# interface, version 2111.1, predict :

Test PrividModule with C# interface, version 2111.1, predict :

INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
FHE_enroll_predict ok, ret = -1
Contacting server https://priv.id/node/predict ...
    idx   uuid                                                               probability
    -----+------------------------------------------------------------------+-----------
    00000 0c36910c39943d15db5c5896af9701e7f8e8500f9c5f8d61e0aa2a73f5db09710d 100.00
    00001 -1 0.00
    00002 -1 0.00
    -----------------------------------------------------------------------------------
``` 
### Delete
``` bat
.\bin\Debug\prividModuleApp.exe  0c36910c39943d15db5c5896af9701e7f8e8500f9c5f8d61e0aa2a73f5db09710d 1 delete
``` 

``` bat
Test PrividModule with C# interface, version 2111.1, delete :

Contacting server https://priv.id/node/deleteUser ...
    Delete Operation Completed, Status = 0, Message = OK
``` 

### Compare Files
``` bat
.\bin\Debug\prividModuleApp.exe  ./img/a1.png ./img/m1.png compare
``` 

``` bat
Test PrividModule with C# interface, version 2111.1, compare :

INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
compare_result = 1, Images ./img/a1.png and ./img/m1.png are different
``` 

## FAQ
1. Sample App (.\bin\Debug\prividModuleApp.exe) is not working
Ensure that the Machine is x64 with Windows operating system 10 or 11.
Check your access rights for the path where you extracted the package. 

2. Image is not getting enrolled
Ensure that the image is in ARGA and in PNG format. You may verify with images in ./img or ./img_a folder in the package

3. I don't have Visual Studio IDE installed in my machine
You may install Visual Studio Community edition from https://visualstudio.microsoft.com/downloads/ 

4. How do I get thresholds and check values for different comparisons, such as for is-valid ? 
Run the test application with verbose=1. 

