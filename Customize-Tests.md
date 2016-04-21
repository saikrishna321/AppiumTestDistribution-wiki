* Specific test method can be skipped based on platform (AndroidDriver/IOSDriver) when running tests Concurrently on the same OSX Host.
    ```
    @Test
    @SkipIf(platform = "AndroidDriver")
    public void testOnlyForIOS() throws Exception  {
        Your test steps...
        ...
        //This will run only on iOS devices
    }

    @Test
    @SkipIf(platform = "IOSDriver")
    public void testOnlyForAndroid() throws Exception  {
        Your test steps...
        ...
        //This will run only on Android devices

    }
    ```
* Retry Annotation for handling flakiness or failure of the test.

    ```
    @Test(retryAnalyzer=Retry.class)
    @RetryCount(maxRetryCount=2)
    public void testWithRandomFailure() throws Exception  {
        Your test steps...
        ...
        //This test will be re-executed the specified number of time if it fails.
    }
    ```