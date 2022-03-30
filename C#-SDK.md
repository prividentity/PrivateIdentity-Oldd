# PrivID C# SDK

## MS Visual Studio IDE Installation

This SDK requires the following *Microsoft Visual Studio IDE* components to be installed:
* Microsoft Visual Studio C# Tools

This package is tested with:
- [x] Visual Studio 2022 
- [x] Visual Studio 2019

* The project files use following packages
* Newtonsoft.Json v. 13.0.1 
* RestSharp v. 107.2.1 

## Dependencies

None.
    
## Install PrivID C# SDK package 

### Through Visual Studio Nuget Package Manager 

#### Private FHE C# DLL 

 1. Use the Visual Studio IDE _Manager NuGet Packages_ Option OR 
 2. Invoke Package Manager from .NET CLI with following command:

``` shell
Install-Package privid_fhe_cs -Version 1.9.2
```
#### Private FHE C# DLL for .NET 2.1 (limited support)
``` csharp
Install-Package privid_fhe_cs_net21 -Version 1.0.1 
```

#### Private FHE C# Test Application 
The API test application is also available through nuget. https://www.nuget.org/packages/privid_fhe_cs_example1/

``` csharp
Install-Package privid_fhe_cs_example2 -Version 1.3.1
```
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

## Response Class
```csharp

    public class PiInfo
    {
      
        public string uuid { get; set; }
        public string guid { get; set; }
        public double probability { get; set; }
    }

    public class Response {
        public int status;
        public string message;
        public int parser_status;
        public string get_json();
        public IList<PiInfo> PI_list { get; set; }
    }
```

## Enroll
Enrolls the image in the Private ID server.
``` csharp
public Response enroll(System.Drawing.Image imageIn)
```
* imageIn - Directory path to the image file
* Return - Response Object. 

## Predict
Predicts the image in the Private ID server.
``` csharp
public Response predict(System.Drawing.Image imageIn, int k)
```
* imageIn - Directory path to the image file
* k - this value shall be 0 < k < 11, default = 1
* Return - Response Object.  
* Prints - UUIDs and respective probabilities for each k. 
## Is Valid
Check if the image is valid
``` csharp
public t_privid_results_is_valid is_valid(System.Drawing.Image imageIn)
```
* imageIn - Directory path to the image file
* Return - Status and message of the operation as t_privid_results_is_valid type. 
## Delete
Deletes the enrollment from the Private ID server. 
``` csharp
public string delete(string uuid)
* uuid - UUID of the entry to be deleted
* Return - result in json format
```
* uuid - UUID of the enrolled image
## Compare Images
Compare two faces for verification.
``` csharp
public t_privid_results_comparecompare_files(System.Drawing.Image imageInA, System.Drawing.Image imageInB, int option)
```    
* imageInA and imageInB  - Path to the image files to be compared 
* option - verbosity option 

* Return - compare result structure as t_privid_results_compare. Compare t_privid_results_compare::result. 0 - imageInA is of same person as that of imageInB; 1 - if different 

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
    string folder_name_local_storage = "privid_local_storage1"; // edit if required
        string server_url = "enter url here";
        string api_key = "enter the api key here";
        int k_factor = 3;

    privid_fhe_face privid_fhe_face1 = new privid_fhe_face(server_url, folder_name_local_storage, api_key, option);
 
    image_in = Image.FromFile(args[0]);
    bool valid_result = privid_fhe_face1.is_valid(image_in);

    image_in = Image.FromFile(args[0]);
    bool enroll_result = privid_fhe_face1.enroll(image_in);

    image_in = Image.FromFile(args[0]);
    Responsepredict_result = privid_fhe_face1.predict(image_in, k_factor);

    privid_fhe_face.t_privid_results_compare compare_result = privid_fhe_face1.delete(args[0]);

    Image a = FixedSize(Image.FromFile(args[0]), imWidth, imHeight);
    Image b = FixedSize(Image.FromFile(args[1]), imWidth, imHeight);
    t_privid_results_compare compare_result = privid_fhe_face1.compare_files(a, b, 0);
    Console.WriteLine("{0}", compare_result .ToString(args[0], args[1]));
``` 

# Test the C# SDK with facial recognition  
## Typical Machine Configuration 
* Operating System - Microsoft Windows 10 Or Windows 11 64-bit .NET Framework 4.6.1
* CPU - Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz   
* RAM - 3.19 GHz with 16.0 GB
## Perform Health Check (to be updated)
To verify that the system is up. Calls all APIs and prints the status in Console.

``` bat
test_case1.bat
``` 
The sample output is :
``` bat
Test PrividModule with C# interface. C++ DLL version 3301.2, C# Wrapper DLL version 1.9.2.0 : predict with .\\img\\a1.png :  server_url = https://devel.private.id/node/  api_key = 00000000000000001962
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
 uuid = 0a0a442ea0e91af565d3

Test PrividModule with C# interface. C++ DLL version 3301.2, C# Wrapper DLL version 1.9.2.0 : enroll with .\\img\\a1.png :  server_url = https://devel.private.id/node/  api_key = 00000000000000001962
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
 uuid = 5ec0bd36c5265b65a4f0

...

Test PrividModule with C# interface. C++ DLL version 3301.2, C# Wrapper DLL version 1.9.2.0 : predict with .\\img\\a1.png :  server_url = https://devel.private.id/node/  api_key = 00000000000000001962
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
 uuid = 0a0a442ea0e91af565d3
``` 
## API Tests
### Is Valid
``` bat
.\\bin\\Debug\\net6.0\\privid_fhe_cs_example1.exe .\\img\\a1.png 0 is_valid
``` 
``` bat
Test PrividModule with C# interface. C++ DLL version 3301.2, C# Wrapper DLL version 1.9.2.0 : is_valid with .\\img\\a1.png :  server_url = https://devel.private.id/node/  api_key = 00000000000000001962
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
    IS_VALID .\\img\\a1.png                   :   0 - ISVALID000-Valid Image.  crop_conf_score = 0.9819433093070984 crop_conf_score_thr = 0.8500000238418579 crop_status= 0
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
.\\bin\\Debug\\net6.0\\privid_fhe_cs_example1.exe .\\img\\a1.png 0 enroll
``` 
``` bat
Test PrividModule with C# interface. C++ DLL version 3301.2, C# Wrapper DLL version 1.9.2.0 : enroll with .\\img\\a1.png :  server_url = https://devel.private.id/node/  api_key = 00000000000000001962
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
 uuid = 55382f7001ad77d471e1

```
### Predict
```

``` bat
.\\bin\\Debug\\net6.0\\privid_fhe_cs_example1.exe .\\img\\a1.png 0 predict
``` 
``` bat
Test PrividModule with C# interface. C++ DLL version 3301.2, C# Wrapper DLL version 1.9.2.0 : predict with .\\img\\a1.png :  server_url = https://devel.private.id/node/  api_key = 00000000000000001962
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
 uuid = 55382f7001ad77d471e1
``` 
### Delete
``` bat
.\\bin\\Debug\\net6.0\\privid_fhe_cs_example1.exe  55382f7001ad77d471e1 0 delete
``` 

``` bat
Test PrividModule with C# interface. C++ DLL version 3301.2, C# Wrapper DLL version 1.9.2.0 :  server_url = https://devel.private.id/node/  api_key = 00000000000000001962
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
55382f7001ad77d471e1
{"message":"OK","status":0} 

``` 

### Compare Files
``` bat
\\bin\\Debug\\net6.0\\privid_fhe_cs_example1.exe  .\\img\\a1.png .\\img\\m1.png compare
``` 

``` bat
Test PrividModule with C# interface. C++ DLL version 3301.2, C# Wrapper DLL version 1.9.2.0 : compare files .\\img\\a1.png & .\\img\\m1.png :  server_url = https://devel.private.id/node/  api_key = 00000000000000001962
INFO: Created TensorFlow Lite XNNPACK delegate for CPU.
Images .\\img\\a1.png & .\\img\\m1.png are Different

``` 

## FAQ
1. Sample App (.\bin\Debug\prividModuleApp.exe) is not working
Ensure that the Machine is x64 with Windows operating system 10 or 11.
Check your access rights for the path where you extracted the package. 

2. Frontal facial image is not successfully enrolled
Ensure that the image is in ARGA and in PNG format. You may verify with images in ./img or ./img_a folder in the package

3. I don't have Visual Studio IDE installed on my machine
You may install Visual Studio Community edition from https://visualstudio.microsoft.com/downloads/ 

4. How do I get thresholds and check values for different comparisons, such as for is-valid ? 
Run the test application with verbose=1. 