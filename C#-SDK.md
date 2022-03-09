# PrivID C# SDK

## MS Visual Studio IDE Installation

This SDK requires the following *Microsoft Visual Studio IDE* components to be installed:
* Microsoft Visual Studio C# Tools

This package is tested with:
- [x] Visual Studio 2022 
- [x] Visual Studio 2019

* The project files use following packages
* Newtonsoft.Json v. 13.0.1 
* RestClient.Net  v. 5.0.7
* RestSharp v. 107.2.1 
* Magick.NET.Core v. 9.1.2

## Dependencies

None.
    
## Install PrivID C# SDK package 

### Through Visual Studio Nuget Package Manager 

#### Private FHE C# DLL 

 1. Use the Visual Studio IDE _Manager NuGet Packages_ Option OR 
 2. Invoke Package Manager from .NET CLI with following command:

``` shell
Install-Package privid_fhe_cs -Version 1.2.6
```
#### Private FHE C# Test Application 
The API test application is also available through nuget. https://www.nuget.org/packages/privid_fhe_cs_example1/

``` csharp
Install-Package privid_fhe_cs_example1 -Version 1.1.3
```

### From ZIP file 

:warning: _this support will be discontinued_

* Download and extract the package [prividModuleApp - 1.2.6.zip](https://github.com/openinfer/PrivateIdentity/blob/master/prividModuleApp%20-%201.2.6.zip)
* Open ./prividModuleApp 1.2.6/prividModuleApp.sln in Visual Studio IDE
* Update the NuGet Package as described [here](https://github.com/openinfer/PrivateIdentity/wiki/C#-SDK#upgrade-private-id-package).
* Standard License [AWS EULA Template (2020.11.20) (Private Identity).pdf](https://github.com/openinfer/PrivateIdentity/files/8132683/AWS.EULA.Template.2020.11.20.Private.Identity.pdf)

# Use the SDK for Facial Recognition 

This section covers how to use the SDK for facial recognition. 

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
Enrolls the image in the Private ID server.
``` csharp
public bool enroll(System.Drawing.Image imageIn)
```
* imageIn - Directory path to the image file
* Return - Status and message of the operation. 0 - Successful operation. -1 or -2 - Enroll operation failed. 

## Predict
Predicts the image in the Private ID server.
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
Deletes the enrollment from the Private ID server. 
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
| `enroll`  | Enrolls the image in the Private ID server |
| `predict` | Predicts the image in the Private ID server |
| `delete`  | Deletes the enrollment from the Private ID server |
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

# Test the C# SDK with facial recognition  
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
Test PrividModule with C# interface. C++ DLL version 2111.1, C# Wrapper DLL version 1.2.6.0,
 Testing predict with .\\img\\a1.png:

INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
     PRIV_FHE :     [Thresholds] result[24] = 0.981943  conf_score_thr = 0.500000
     PRIV_FHE :     [Thresholds] conf_score_thr = 0.500
     PRIV_FHE :     [Thresholds] result[24] = 0.981943  conf_score_thr = 0.500000
     PRIV_FHE :     [Thresholds] conf_score_thr = 0.500
Contacting server https://priv.id/node/predict ...
     idx   uuid                                                               probability
     -----+------------------------------------------------------------------+-----------
     00000 0cafbfcce257bcf5ab3afb6ce6d1ff2452ef7c797bc1fde36f3ae2466d4c7fe721 100.00
     00001 -1 0.00
     00002 -1 0.00
     -----------------------------------------------------------------------------------
     RESULT  : predict_result for Image .\\img\\a1.png is = True
...

``` 
## API Tests
### Is Valid
``` bat
.\bin\Debug\prividModuleApp.exe  ./img/a1.png 0 is_valid
``` 
``` bat
C:\prividModuleApp - 1.2.6>.\\bin\\Debug\\net6.0\\prividModuleApp.exe .\img\0.png 1 is_valid
Test PrividModule with C# interface. C++ DLL version 2111.1, C# Wrapper DLL version 1.2.6.0,
 Testing is_valid with .\img\0.png:

INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
     PRIV_FHE :     [Thresholds] result[24] = 0.859852  conf_score_thr = 0.500000
     PRIV_FHE :     [Thresholds] conf_score_thr = 0.500
is_valid ok, ret = 0
     RESULT  : valid_result for Image .\img\0.png is = 0 - Valid Image
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
.\\bin\\Release\\net6.0\\prividModuleApp.exe .\\img\\a1.png 1 enroll
``` 
``` bat
Test PrividModule with C# interface. C++ DLL version 2111.1, C# Wrapper DLL version 1.2.6.0,
 Testing enroll with .\\img\\a1.png:

INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
     PRIV_FHE :     [Thresholds] result[24] = 0.981943  conf_score_thr = 0.850000
     PRIV_FHE :     [Thresholds] conf_score_thr = 0.850
     PRIV_FHE :     [Thresholds] result[24] = 0.981943  conf_score_thr = 0.850000
     PRIV_FHE :     [Thresholds] conf_score_thr = 0.850
Contacting server https://priv.id/node/enroll ...
     uuid = 0cafbfcce257bcf5ab3afb6ce6d1ff2452ef7c797bc1fde36f3ae2466d4c7fe721
     guid = 0c06956fb32628850da498ca33be00ec88e158d84d74c774d3c2c8bf61b72e7898
     ++++++  Person exists in system skipping enroll.  ++++++
     RESULT  : enroll_result for Image .\\img\\a1.png is = True

### Predict
```

``` bat
.\\bin\\Release\\net6.0\\prividModuleApp.exe .\\img\\a1.png 1 predict
``` 
``` bat
Test PrividModule with C# interface. C++ DLL version 2111.1, C# Wrapper DLL version 1.2.6.0,
 Testing predict with .\\img\\a1.png:

INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
     PRIV_FHE :     [Thresholds] result[24] = 0.981943  conf_score_thr = 0.500000
     PRIV_FHE :     [Thresholds] conf_score_thr = 0.500
     PRIV_FHE :     [Thresholds] result[24] = 0.981943  conf_score_thr = 0.500000
     PRIV_FHE :     [Thresholds] conf_score_thr = 0.500
Contacting server https://priv.id/node/predict ...
     idx   uuid                                                               probability
     -----+------------------------------------------------------------------+-----------
     00000 0cafbfcce257bcf5ab3afb6ce6d1ff2452ef7c797bc1fde36f3ae2466d4c7fe721 100.00
     00001 -1 0.00
     00002 -1 0.00
     -----------------------------------------------------------------------------------
     RESULT  : predict_result for Image .\\img\\a1.png is = True

``` 
### Delete
``` bat
.\\bin\\Debug\\net6.0\\prividModuleApp.exe 0cafbfcce257bcf5ab3afb6ce6d1ff2452ef7c797bc1fde36f3ae2466d4c7fe721 1 delete
``` 

``` bat
Test PrividModule with C# interface. C++ DLL version 2111.1, C# Wrapper DLL version 1.2.6.0,
 Testing
Contacting server https://priv.id/node/deleteUser ...
    Delete Operation Completed, Status = 0, Message = OK
     RESULT  : delete_result for UUID 0cafbfcce257bcf5ab3afb6ce6d1ff2452ef7c797bc1fde36f3ae2466d4c7fe721 is = 0

``` 

### Compare Files
``` bat
.\\bin\\Debug\\net6.0\\prividModuleApp.exe ./img/a1.png ./img/m1.png compare
``` 

``` bat
Test PrividModule with C# interface. C++ DLL version 2111.1, C# Wrapper DLL version 1.2.6.0,
 Testing compare files ./img/a1.png & ./img/m1.png:

In Size.Width = 480 Size.Height = 480 size = 921600
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
FHE_init ok
     PRIV_FHE :     [Thresholds] result[24] = 0.981943  conf_score_thr = 0.500000
     PRIV_FHE :     [Thresholds] conf_score_thr = 0.500
     PRIV_FHE :     [Thresholds] result[24] = 0.981943  conf_score_thr = 0.500000
     PRIV_FHE :     [Thresholds] conf_score_thr = 0.500
     PRIV_FHE :     [Thresholds] result[24] = 0.981943  conf_score_thr = 0.500000
     PRIV_FHE :     [Thresholds] conf_score_thr = 0.500
     PRIV_FHE :     [Thresholds] result[24] = 0.981943  conf_score_thr = 0.500000
     PRIV_FHE :     [Thresholds] conf_score_thr = 0.500
     PRIV_FHE :     [Thresholds] distance_max = 0.20  distance_mean = 0.20  distance_min = 0.20
     PRIV_FHE :     [Thresholds] face_thresholds[0] = 0.96  face_thresholds[1] = 1.01  face_thresholds[1] = 1.06
compare_result = 0, Images ./img/a1.png and ./img/m1.png are the same

``` 

## FAQ
1. Sample App (.\bin\Debug\prividModuleApp.exe) is not working
Ensure that the Machine is x64 with Windows operating system 10 or 11.
Check your access rights for the path where you extracted the package. 

2. Frontal facial image is not successfully enrolled
Ensure that the image is in ARGA and in PNG format. You may verify with images in ./img or ./img_a folder in the package

3. I don't have Visual Studio IDE installed in my machine
You may install Visual Studio Community edition from https://visualstudio.microsoft.com/downloads/ 

4. How do I get thresholds and check values for different comparisons, such as for is-valid ? 
Run the test application with verbose=1. 