### How to find your Subject ID on /a/
**There are two methods of determining your subject ID**

> Note, the usage of console is required, so if you are on a handheld device you will have to link to a computer to view the console. Such as an iPhone linking to a macbook to portray the console. Console is accessible on Safari, Firefox, and Google Chrome, and Microsoft Edge.

**Method 1** (during enrollment):
* Enroll your face and/or voice

* Inspect Element, and then select the Console Tab

> ![](https://github.com/openinfer/PrivateIdentity/blob/master/images/chrome-right-click-inspect.png)
> ![](https://github.com/openinfer/PrivateIdentity/blob/master/images/inspect_console.png)
* Your subject ID will show up as either `subject_id:#` or `guid:#`
> ![](https://github.com/openinfer/PrivateIdentity/blob/master/images/SubjectID_Console_During_Enrollment.png)

**Method 2** (after enrollment):
* In the URL use the parameter &action=predict and run the prediction.

* Inspect Element, and the select the Console Tab
> ![](https://github.com/openinfer/PrivateIdentity/blob/master/images/chrome-right-click-inspect.png)
> ![](https://github.com/openinfer/PrivateIdentity/blob/master/images/inspect_console.png)
* Your subject ID will show up as either `subject_id:#` or `guid:#`
> ![](https://github.com/openinfer/PrivateIdentity/blob/master/images/SubjectID_Console_During_Enrollment.png)