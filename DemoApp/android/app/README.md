## Changes from `develop`
1. Enabled Proguard obfuscation in release mode. This required adding a signing configuration. If you need to use the release mode (to send JavaScript crashes), change the details in `android/app/build.gradle` to your own keystore.
2. Changed order of repositories in `android/build.gradle`. This was a bugfix and the app won't compile without it.
3. Added `devsupport.pro` rules to Proguard obfuscation. This was a bugfix.
4. Added a class `ByZeroDivide` to `DemoAppNativeModule.java`. This adds a fully obfuscated frame to the Java crash stacktrace (the rest of the frames are referenced using reflection and so aren't obfuscated).
5. Set crashes to be sent to `int`. Can be changed in `MainApplication.java (55)`.

## Notes
1. The app must be built in release mode to send JavaScript crashes. Native Java crashes can be sent in debug or release mode. Both types of crashes are obfuscated when Proguard is enabled although it is difficult to see this in the JavaScript crashes. You can tell by looking at the exception type (for me it was obfuscated to `com.facebook.react.common.d`).
2. Set the appsecret in `DemoApp/android/app/src/main/assets/appcenter-config.json`