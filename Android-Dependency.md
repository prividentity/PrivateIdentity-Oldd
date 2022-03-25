# PrivID Android Dependency

## Android 

This dependency requires following tool to be installed: 
* Android studio 

This dependency tested with:
- [X] Android Studio 4.2.1
- [x] compileSdkVersion 31
- [x] buildToolsVersion "30.0.2"
- [X] targetSdkVersion 31
- [X] minSdkVersion 28


## Dependencies
* Add  dependency in build.gradle(Module)
``` android
    dependencies 
    {
        implementation 'com.github.openinfer:Android-library:1.10'
    }

```

* Add it in your root build.gradle(Project) at the end of repositories:
``` android
    allprojects {
    	repositories {
    	    ...
    	    maven { url 'https://jitpack.io' }
    	}
    }
``` 

# Use the dependency for Facial Recognition 

This section covers how to use the dependency for facial recognition. 

## PrividFheFace.class
* Make instance of PrividFheFace class.
* Pass required parameters in constructor

``` android
     public PrividFheFace prividFheFace = new PrividFheFace(localStoragePath, activity);
```

* localStoragePath: string
	 - Path to the local storage where result will store.

* activity: Activity 
	 - Instance of activity.


The **PrividFheFace** implements the methods for enrolling and predicting.
It exposes 3 methods as part of the interface:

## Response Classes
```android
public class ResponseModel {
    private String message;
    private Integer status;
    private boolean result;
    private PIModel piModel =new PIModel();

    public PIModel getPiModel() {
        return piModel;
    }
    public void setPiModel(PIModel piModel) {
        this.piModel = piModel;
    }
    public String getMessage() {
        return message;
    }
    public void setMessage(String message) {
        this.message = message;
    }
    public Integer getStatus() {
        return status;
    }
    public void setStatus(Integer status) {
        this.status = status;
    }
    public ResponseModel( Integer status,String message, boolean result,PIModel piModel) {
        this.message = message;
        this.status = status;
        this.piModel = piModel;
        this.result = result;
    }
    public ResponseModel( Integer status,String message, boolean result) {
        this.message = message;
        this.status = status;
        this.result = result;
    }
    public boolean isResult() {
        return result;
    }
    public void setResult(boolean result) {
        this.result = result;
    }
}

public class PIModel {
    String enroll_level;
    String modality;
    String uuid;
    String guid;

    public String getEnroll_level() {
        return enroll_level;
    }
    public void setEnroll_level(String enroll_level) {
        this.enroll_level = enroll_level;
    }
    public String getModality() {
        return modality;
    }
    public void setModality(String modality) {
        this.modality = modality;
    }
    public String getUuid() {
        return uuid;
    }
   public void setUuid(String uuid) {
        this.uuid = uuid;
    }
    public String getGuid() {
        return guid;
    }
    public void setGuid(String guid) {
        this.guid = guid;
    }
}

```

## Enroll
Enrolls the image in the Private ID server.
``` android
prividFheFace.enroll(imageIn);
```
* imageIn - Directory path to the image file
* Return - ResponseModel Object. 

## Predict
Predicts the image in the Private ID server.
``` android
prividFheFace.predict(imageIn);
```
* imageIn - Directory path to the image file
* Return - ResponseModel Object.  

## Is Valid
Check if the image is valid
``` android
prividFheFace.isValid(imageIn, activity);
```
* imageIn  - Directory path to the image file
* activity - Instance of activity.
* Return -  ResponseModel Object.

## METHODS
|Method| Desc  |
|--|--|
| `isValid` | Check if the image is valid |
| `enroll`  | Enrolls the image in the Private ID server |
| `predict` | Predicts the image in the Private ID server |


## Sample Code 

``` android
    Activity activity = this;
    String TAG = getClass().getSimpleName();
    String imagePath = "/storage/emulated/0/Android/media/" + activity.getPackageName() + "/" + activity.getString(R.string.app_name) + "/image/test.png";
    String folder_name_local_storage = "/storage/emulated/0/Android/media/" + activity.getPackageName() + "/" + activity.getString(R.string.app_name) + "/privid_local_storage/";

    PrividFheFace prividFheFace = new PrividFheFace(folder_name_local_storage, activity);

    ResponseModel responseModel = prividFheFace.isValid(imagePath, activity);
    Log.e(TAG, "getMessage " + responseModel.getMessage());
    Log.e(TAG, "getStatus " + responseModel.getStatus());

    responseModel = prividFheFace.predict(imagePath);
    Log.e(TAG, "predict getMessage " + responseModel.getMessage());
    Log.e(TAG, "predict getStatus " + responseModel.getStatus());
    Log.e(TAG, "predict getUuid " + responseModel.getPiModel().getUuid());

    responseModel = prividFheFace.enroll(imagePath);
    Log.e(TAG, "enroll getMessage " + responseModel.getMessage());
    Log.e(TAG, "enroll getStatus " + responseModel.getStatus());
    Log.e(TAG, "enroll getUuid " + responseModel.getPiModel().getUuid());   
 
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
| 21 | Image is not valid |
| 22 | Image path is not valid |
| 23 | App don't have Read/Write permission |
| 24 | Image is not valid |
| 25 | Server error. Unable to get UUID |
| 27 | Server error. Unable to get response from server |
| 28 | Server error. Unable to get response from server |
| 29 | Memory error |
| 30 | Unable to write result in local storage |
