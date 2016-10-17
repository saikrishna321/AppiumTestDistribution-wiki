1. Main Runnerclass should look as below ::

```
**Run lists of tests from package**
    public class Runner {

        @Test
        public void testApp() throws Exception {
            ParallelThread parallelThread = new ParallelThread();
            //parallelThread.runner(package_name_where_test_located);
            parallelThread.runner("com.paralle.tests");
        }
    }

**  Run lists of tests** 
     @Test
        public void testApp() throws Exception {
          ParallelThread parallelThread = new ParallelThread();
          List<String> tests = new ArrayList<>();
          tests.add("HomePageTest2");
          tests.add("HomePageTest3");
          parallelThread.runner("com.test.site",tests);
        }

  **Run lists of tests from mulitple packages**
     @Test
        public void testApp() throws Exception {
          ParallelThread parallelThread = new ParallelThread();
          List<String> tests = new ArrayList<>();
          tests.add("HomePageTest2");
          tests.add("HomePageTest3");
          parallelThread.runner("com.test.site,com.ios.test",tests);
        }
    ```
2. Extend your tests to AppiumParallelTest ::( It is part of the dependencies and will take care of running the Appium server session in parallel threads).

    ```
    public class UserBaseTest extends AppiumParallelTest {

        @BeforeMethod()
        public void startApp(Method name) throws Exception {
            driver = startAppiumServerInParallel(name.getName());
            startLogResults(name.getName());
        }

        @AfterMethod()
        public void killServer(ITestResult result) {
            endLogTestResults(result);
            getDriver().quit();
        }

        public AppiumDriver<MobileElement> getDriver() {
            return driver;
        }

        @BeforeClass()
        public void beforeClass() throws Exception {
             startAppiumServer(getClass().getSimpleName());
        }

        @AfterClass()
        public void afterClass() throws InterruptedException, IOException {
            killAppiumServer();
        }
    }
    ```

3. Create `config.properties` file under your test directory, which should have below properties.

    ```
    APP_PACKAGE=com.android2.calculator3
    APP_ACTIVITY=com.android2.calculator3.Calculator
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
    IOS_APP_PATH=<absolute path to .app/.ipa>
    ANDROID_APP_PATH=<absoulte path to .apk>
    FRAMEWORK=testng/cucumber
    
    ## For remote logging the reports using ExtentX(http://extentreports.relevantcodes.com/extentx/)
    MONGODB_SERVER=ADDRESS_OF_THE_SERVER
    MONGODB_PORT=PORT_NUMBER
    ```

###Run Test from CommandLine

```
mvn clean -Dtest=Runner test
```

###Run Test from CommandLine with ExtentX logging

```
ExtentX="true" mvn clean -Dtest=Runner test
```