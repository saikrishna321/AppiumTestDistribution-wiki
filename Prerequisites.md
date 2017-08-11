### Android:
1. If you have installed Appium from [npm](https://www.npmjs.com/package/appium) make sure you have latest version.
    e.g. `npm -g install appium@beta` or [Build Appium from source](https://discuss.appium.io/t/appium-1-5-beta-release/6058/35).
2. Android SDK is installed and ANDROID_HOME is set as the environment variable.
3. JDK 1.8 is installed and JAVA_HOME is set as the environment variable.
4. Developer option is enabled on the attached device and must be authorized.

### IOS (Real device):
1. Mac machine with XCode and command line tools installed. XCode version >= 6.0, 7.1.1 recommended.
2. `libimobiledevice` and `ideviceinstaller` must be installed.

    e.g. `brew install libimobiledevice libplist libtasn1 usbmuxd openssl ideviceinstaller`
3. Developer option must be enabled in attached iOS device (Settings>Developer>Enable UI Automation)
4. You must have a debug build of the application you wish to test.
5. If you want to trigger tests on Multiple Simulators in parallel make sure you have Xcode9-beta and latest appium version 1.6.6.beta.
6. Install ios-webkit-debug-proxy, if running web test on real devices.
   e.g. `brew install ios-webkit-debug-proxy
 `