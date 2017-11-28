# Implementation of OneSignal in ReactNative supporting iOS & Android

A simple vanilla setup supporting iOS rich media notification. Personal use, not intended for production in any way.

## Getting Started

A plain installation following One Signal Documentation with some personal notes to avoid installation obstacles once again.

* [OneSignal Push Notifications](https://onesignal.com)
* [react-native-onesignal on github](https://github.com/OneSignal/react-native-onesignal)


### Installing

#### Initial React Native Setup
```
react-native init OneSignalReactC
cd OneSignalReactC
yarn add react-native-onesignal
react-native link react-native-onesignal
```
Following official instructions:
* [iOS installation](https://github.com/OneSignal/react-native-onesignal#ios-installation)
* [Android installation](https://github.com/OneSignal/react-native-onesignal#android-installation)

#### Add Keys & ids

* In `android/app/build.gradle`
* In `AppDelegate.m`


## Rich Media notification - iOS only
In order to have rich media notification working on iOS, the native SDK is needed. Read [oscarjg's comment](https://github.com/geektimecoil/react-native-onesignal/issues/345#issuecomment-347000552) carefully.

* https://documentation.onesignal.com/v3.0/docs/rich-media

#### Issues solved, but not documented yet.
* [Step by Step Advice on Github (by oscarjg) ](https://github.com/geektimecoil/react-native-onesignal/issues/345#issuecomment-347000552)

* Podfile needs to be properly structured. Remove all xxxx-tvOSTests stuff in Podfile. They are automatically generated bei pod init because of react-native link and are not needed.

```
target 'OneSignalReactC' do
    target 'OneSignalNotificationServiceExtension' do
       pod 'OneSignal', '>= 2.5.2', '< 3.0'
    end
end
```

## Installation Errors iOS

```
CFBundleIdentifier", Does Not Exist
```

Make sure Paths Build Location is properly set in Xcode.
* `File > Workspace Settings > Advanced`
  * Custom = `Relative to Workspace`
  * Products = `build/Build/Products`
  * Intermediates = `build/Build/Intermediates`
* `Product > Clean`

```
The target `OneSignalReactC-tvOSTests` is declared twice
```

* Structure your Podfile properly. See above.
