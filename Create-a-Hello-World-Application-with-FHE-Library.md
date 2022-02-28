# Prerequisite
* Visual Studio 2022 IDE installed on a Windows 10 64-bit machine
* The prividModuleApp - xxx.ZIP file from Private Identity for sample application, runtime DLL[^1] and test scripts 
* Access to NuGet Package Manager for installing privid_fhe_cs library. 

# Steps to follow
## 1. Open Visual Studio IDE
## 2. Create a new Application 
2.1 Select Console Application 
![image](https://user-images.githubusercontent.com/11586902/155999310-f140a497-c5d1-4d73-b1d3-21b1d5ca7f62.png)

2.2 Enter project name and path. Here creating a new Solution. _It is possible to be added to an existing Solution also._ 
![image](https://user-images.githubusercontent.com/11586902/155999448-9214f30e-eae1-40eb-a779-8c3a14540348.png)

2.3 Select the .NET framework. _Here, .NET 6.0 is used. _
![image](https://user-images.githubusercontent.com/11586902/155999776-2bcaf114-65a8-48c6-9ef9-05309e68f8cf.png)

2.4 Open the Program.cs from the Project. 
![image](https://user-images.githubusercontent.com/11586902/156000418-795c682e-552b-4c73-8b44-38aec7cd2af3.png)

2.5 Build and Run
Press F5 

![image](https://user-images.githubusercontent.com/11586902/156000565-c3798ca0-5303-4eae-a08b-cd8e376a6131.png)

Verify that _Hello World !_ in top left of the Console. 

## 3. Add **privid_fhe_cs** to the Project

3.1 Add **privid_fhe_cs **through _NuGet Package Manager _

![image](https://user-images.githubusercontent.com/11586902/156000968-7d09bcab-73bb-406a-b403-ba211bbc165b.png)

3.2 type _privid_fhe_cs_ in _Brows_ pane
![image](https://user-images.githubusercontent.com/11586902/156001196-2eeaf3f1-74a4-4b83-af86-45bf3fdb2ecf.png)

3.3 Click on the _privid_fhe_cs_, Verify License
On pressing _Install_
![image](https://user-images.githubusercontent.com/11586902/156001463-99a8cf9d-79bd-407f-adce-307003353d3c.png)

3.4 Press _Ok_ in preview 
![image](https://user-images.githubusercontent.com/11586902/156001678-e0f567ad-b20a-4bfd-baeb-575a9cc1790a.png)

3.5 Check and verify the project details
![image](https://user-images.githubusercontent.com/11586902/156002029-1899e470-b781-47e1-8d92-d6b6df74ba41.png)

## 4 Edit Program.cs - Print Version 

4.1 Add a line to print the library versions - to print both C++ dll and CS wrapper DLL version. 

``` csharp
using privid_fhe_cs;      

Console.WriteLine("Hello, World!");

Console.Write("Test PrividModule with C# interface. C++ DLL version {0}, C# Wrapper DLL version {1},\n Testing ", privid_fhe_face.get_version(), privid_fhe_face.get_cs_dll_version());

```

4.2 Set working folder to $(ProjectDir). 
Right-Click on the Project in Solution Explorer and navigate to _Debug_,  Open Debug Launch Profile UI and type $(ProjectDir) in _Working Folder _ TextBox. 
![image](https://user-images.githubusercontent.com/11586902/156003733-df945e6f-797e-439e-85c0-449c39dc4f36.png)

ProjectDir is the path where .csproj is saved. in this case, it is:
![image](https://user-images.githubusercontent.com/11586902/156004568-9e55a9e4-0cf8-4cae-9a6f-b8c6085fa4db.png)

4.3 Copy the runtime DLL from ZIP file to $(ProjectDir)

Copy _privid_fhe.dll_ from the _prividModuleApp - a.b.c.ZIP_ to the working folder 

4.4 Build and Run the Project.
![image](https://user-images.githubusercontent.com/11586902/156004740-5f8512e7-322d-4741-b8fa-2a5cb80998d4.png)

Verify the version printed in the Console.

![image](https://user-images.githubusercontent.com/11586902/156004883-759d0ce2-fbc6-4912-a1a8-559a9078c7c6.png)


## 5 Edit Program.cs - Create Instance of _privid_fhe_face_ class

5.1 Ensure that you have a Valid API key

Add following lines to the above Program.cs 
``` csharp 
string folder_name_local_storage = "privid_local_storage1";
string server_url = "https://priv.id/node";
**string api_key = "0000000000000000APIKEY" Enter your API key Here;**
int k_factor = 3;

int option = 1;
privid_fhe_face privid_fhe_face1 = new privid_fhe_face(server_url, folder_name_local_storage, api_key, option);

```

## 6 Edit Program.cs - Add is_Valid API calls 
6.1 Add following lines to the above Program.cs. After adding the code will look as follows :

``` csharp

using privid_fhe_cs;
using System.Drawing;

Console.WriteLine("Hello, World!");
Console.Write("Test PrividModule with C# interface. C++ DLL version {0}, C# Wrapper DLL version {1},\n Testing ", privid_fhe_face.get_version(), privid_fhe_face.get_cs_dll_version());

string folder_name_local_storage = "privid_local_storage1";
string server_url = "https://priv.id/node";
**string api_key = "0000000000000000APIKEY" Enter your API key Here;**
int k_factor = 3;

int option = 1;
privid_fhe_face privid_fhe_face1 = new privid_fhe_face(server_url, folder_name_local_storage, api_key, option);
string imgFileMame = "c4.png";
int valid_result = privid_fhe_face1.is_valid(Image.FromFile("c4.png"));
Console.WriteLine("is_valid returned {0}", valid_result);
valid_result = privid_fhe_face1.is_valid(Image.FromFile("c17.png"));
Console.WriteLine("is_valid returned {0}", valid_result);
valid_result = privid_fhe_face1.is_valid(Image.FromFile("a1.png"));
Console.WriteLine("is_valid returned {0}", valid_result);

```
6.2 Makesure that all the above images are in working folder. In this case, it is $(ProjectDir)

6.3 Build and Run

![image](https://user-images.githubusercontent.com/11586902/156007328-500d8d15-f64c-4c09-b9b9-87744eaf5c1d.png)


## 7 Edit Program.cs - Add Calls to enroll and predict API calls too 
7.1 Add following lines to the above Program.cs. After adding the code will look as follows :

``` csharp

using privid_fhe_cs;
using System.Drawing;

Console.WriteLine("Hello, World!");
Console.Write("Test PrividModule with C# interface. C++ DLL version {0}, C# Wrapper DLL version {1},\n Testing ", privid_fhe_face.get_version(), privid_fhe_face.get_cs_dll_version());

string folder_name_local_storage = "privid_local_storage1";
string server_url = "https://priv.id/node";
string api_key = "00000000000000001962";
int k_factor = 3;

int option = 1;
privid_fhe_face privid_fhe_face1 = new privid_fhe_face(server_url, folder_name_local_storage, api_key, option);


/* clear folder_name_local_storage folder */
if (Directory.Exists(folder_name_local_storage))
    Directory.Delete(folder_name_local_storage, true);

string imgFileMame = "a1.png";
int valid_result = privid_fhe_face1.is_valid(Image.FromFile(imgFileMame));
Console.WriteLine("is_valid returned {0}", valid_result);
bool enroll_result = privid_fhe_face1.enroll(Image.FromFile(imgFileMame));
Console.WriteLine("enroll_result returned {0}", enroll_result);

bool predict_result = privid_fhe_face1.predict(Image.FromFile(imgFileMame), k_factor);
Console.WriteLine("predict_result returned {0}", predict_result);

```
Note the enroll and predict results. _Ignore the ERROR on local storage._

![image](https://user-images.githubusercontent.com/11586902/156009400-f652c0d8-367d-4747-a649-ac0248520d11.png)








[^1] : todo 









