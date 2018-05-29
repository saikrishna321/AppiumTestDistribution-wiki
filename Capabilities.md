##CAPABILITIES:

* In order to test on a real iOS device change the simulator capability on the capabilities file to device, both can be used to run in real devices and simulators.
```
    "app": {
        "device": "/Users/qh/Documents/AppiumTestDistribution/orgQMApp.app",
        "simulator": "/Users/qh/Documents/AppiumTestDistribution/QMApp.app"
    }
```
* Capabilities can also be added to drivers like this:
```
    "chromedriverExecutableDir": "chromedrivers",
    "nativeWebScreenshot": true,
    "fullReset":false,
    "noReset":true,
```
* The chromedriverExecutableDir can be used, from appium 1.8 up, as a collection of chrome driver version and appium itself will choose which one to use.