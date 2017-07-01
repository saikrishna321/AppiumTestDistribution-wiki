1. Main Runnerclass should look as below ::

```
** Run lists of tests from package **    
      public class Runner {

        @Test
        public void testApp() throws Exception {
            ParallelThread parallelThread = new ParallelThread();
            //parallelThread.runner(package_name_where_test_located);
            parallelThread.runner("com.paralle.tests");
        }
    }

** Run lists of tests ** 
     @Test
        public void testApp() throws Exception {
          ParallelThread parallelThread = new ParallelThread();
          List<String> tests = new ArrayList<>();
          tests.add("HomePageTest2");
          tests.add("HomePageTest3");
          parallelThread.runner("com.test.site",tests);
        }

** Run lists of tests from mulitple packages **
     @Test
        public void testApp() throws Exception {
          ParallelThread parallelThread = new ParallelThread();
          List<String> tests = new ArrayList<>();
          tests.add("HomePageTest2");
          tests.add("HomePageTest3");
          parallelThread.runner("com.test.site,com.ios.test",tests);
        }

** Run test against certain devices connected **
command to start runner
mvn clean -Dtest=RunnerCukes test -Dudid=udid1,udid2,udid3

public class RunnerCukes {
    @Test 
    public void testCukesRunner() throws Exception {
        String udidParam = System.getProperty("udid");
        String[] parts = udidParam.split(",");
    	List<String> deviceList = Arrays.asList(parts);
    	ParallelThread cucumberParallelThread = new ParallelThread(deviceList);
        boolean hasFailures = cucumberParallelThread.runner("output");
        Assert.assertFalse(hasFailures, "Testcases have failed in parallel execution");
    }
}

```

2. Create `config.properties` file under your test directory, which should have below properties.

    ```
    RUNNER=distribute

    ## For appium 1.5.X users (If appium installed using npm)
    APPIUM_JS_PATH=/usr/local/lib/node_modules/appium/build/lib/main.js

    ## For appium 1.4.13 users (GUI)
    APPIUM_JS_PATH=/Appium.app/Contents/Resources/node_modules/appium/bin/appium.js

    ## For appium 1.4.16 users (Non-GUI -- Installed using npm)
    APPIUM_JS_PATH=/usr/local/lib/node_modules/appium/bin/appium.js
    BROWSER_TYPE=chrome
    APP_TYPE=NA
    BUNDLE_ID=
    FRAMEWORK=testng/cucumber
    
    ## For remote logging the reports using ExtentX(http://extentreports.relevantcodes.com/extentx/)
    MONGODB_SERVER=ADDRESS_OF_THE_SERVER
    MONGODB_PORT=PORT_NUMBER
    ```
3. If you want to specify android/iOS capabilities 
   (https://github.com/saikrishna321/PageObjectPatternAppium/tree/master/caps)

###Run Test from CommandLine

```
Platform="android/ios/both" mvn clean -Dtest=Runner test
```

###Run Test from CommandLine with ExtentX logging

```
ExtentX="true" mvn clean -Dtest=Runner test
```