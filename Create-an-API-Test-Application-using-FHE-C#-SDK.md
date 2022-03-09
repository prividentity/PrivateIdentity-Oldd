# Prerequisite
* Visual Studio 2022 IDE installed on a Windows 10 64-bit machine
* Access to NuGet Package Manager for installing privid_fhe C# SDK packages. 

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

## 3. Add **privid_fhe_cs_example1** to the project

3.1 Comment of source code line(s) in Program.cs

3.2 Add privid_fhe_cs_example1 using NuGet Application Manager 
Open 

``` csharp
Install-Package privid_fhe_cs_example1 -Version 1.1.3
```
![image](https://user-images.githubusercontent.com/11586902/157435857-bb84bd97-8e2b-4631-9e55-76b9ffcaf363.png)

Screen after successful installation 
![image](https://user-images.githubusercontent.com/11586902/157436107-ea6f83af-f980-4b0f-a2fb-a1c92718053c.png)

3.3 Add Pre-build script to the project
Copy the lines in README and paste in the Pre-build Even text box as follows:
![image](https://user-images.githubusercontent.com/11586902/157436267-771101d6-0c54-42c1-b159-90bdd545e043.png)

Set the Working Directory to be $(ProjectDir)
![image](https://user-images.githubusercontent.com/11586902/157436668-4c4bef5f-7458-4bd1-896e-02b4f380c4a7.png)

3.4 Build the project 
Right Click on the project and select _RebuildA_
![image](https://user-images.githubusercontent.com/11586902/157437341-408374fd-d659-4157-a9d9-8ec055ec9e61.png)

Screen after successful build
![image](https://user-images.githubusercontent.com/11586902/157437269-51db9a77-c86e-41e6-b464-123dcb942711.png)

3.5 Run the project with no arguments 

Press F5
Screen on successful execution. 
![image](https://user-images.githubusercontent.com/11586902/157437585-f190c93b-4376-4996-9cf0-7376e034fad2.png)

3.6 Run the project - to test is_valid API

add the following line as the commandline argument:
``` csharp
a1.png 1 is_valid
```
![image](https://user-images.githubusercontent.com/11586902/157438213-a0bd8e34-bf4e-4f7f-bebb-9e3dabdaee68.png)

Screen after successful execution
![image](https://user-images.githubusercontent.com/11586902/157438293-9edcb92a-46eb-4583-8344-9ab4c133df3e.png)

3.6 Run the project - to test enroll API

add the following line as the commandline argument:
``` csharp
a1.png 1 enroll 
```
Screen after execution

![image](https://user-images.githubusercontent.com/11586902/157438517-c3b5345a-571e-4397-9f45-0179f9bc6750.png)

3.7 Run the project - to test predict API

add the following line as the commandline argument:
``` csharp
a1.png 1 predict 
```

Screen after execution

![image](https://user-images.githubusercontent.com/11586902/157438617-d6502419-fb0c-49bb-9553-92f64d47f24b.png)

3.8 Run the project - to test delete API

add the following line as the commandline argument:
``` csharp
0c550dd1ea1b68e6a6c837d4c84825ab58daaf47532738c3748223e19f74527158 1 delete
```

Screen after execution

![image](https://user-images.githubusercontent.com/11586902/157438800-9896f627-cff2-4ac0-a2c4-a4a816f28bc7.png)

