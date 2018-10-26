1. The app must be built in release mode to send JavaScript crashes. Native Java crashes can be sent in debug or release mode.
2. Set the appsecret in DemoApp/android/app/src/main/assets/appcenter-config.json
3. The app is currently configured to send crashes to apps in `int`. Change this in `MainApplication.java (55)`.