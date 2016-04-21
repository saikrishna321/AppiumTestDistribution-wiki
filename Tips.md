##Tips:

* Provide the absolute path of the .apk and .ipa file.
* APPIUM_JS_PATH should be the location of the appium.js in your local machine.If you're using the latest Appium v1.5.0 please make sure
  you have the source build locally. Refer the Bug(https://github.com/appium/appium/issues/6202), ignore this if you have version 1.5.1 
* RUNNER option can be parallel/distribute(Parallel will run all the tests across device- which helps you to get the device coverage/ Distribute will distribute all the tests across devices which help you faster execution)
* APP_TYPE should be set to "web" to run web tests on chrome in android, if running native/hybrid test, set APP_TYPE="NA".
* Make sure you have chrome browser installed on android real devices, if not download it from Playstore.
* Make sure you don't use ```getDriver().resetApp()``` when you are running your web tests.
* On Test Failures device frame will be added to the screenshot captured during execution, provided you have the frames  inside the resources folder and have installed ImageMagick and set in path. Please download the frames(https://github.com/saikrishna321/DeviceFrames) and place them under resources folder. (e.g. /src/test/resources/frames/)

<h3>Sample ImagesFramed</h3>
https://github.com/saikrishna321/AppiumTestDistribution/tree/master/image/device_frame_example)

##Device Art for Android
* Nexus 4
* Nexus 5
* Nexus 6
* Nexus 6P
* Nexus 5x
* Yet to add S3,S4,S5 and S6

##Device Art for iPhone

* iPhone 5c
* iPhone 5s
* iPhone 6
* iPhone 6 Plus
* iPhone 6s
* iPhone 6s Plus
* iPod touch 5G