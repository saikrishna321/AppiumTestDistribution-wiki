##Tips:

* In order to test on a real iOS device cahange the simulator capability on the cabalities file to device, both can be used to run in both real devices and simulators.
    "app": {
      "device": "/Users/qh/Documents/AppiumTestDistribution/orgQMApp.app",
      "simulator": "/Users/qh/Documents/AppiumTestDistribution/QMApp.app"
    }
* Capabilities can be added to the driver like this:
	    "chromedriverExecutableDir": "chromedrivers",
        "nativeWebScreenshot": true,
	    "fullReset":false,
	    "noReset":true,
* The chromedriverExecutableDir can be used, from appium 1.8 on, as a collection of chrome driver version and appium itself will choose which one to use.