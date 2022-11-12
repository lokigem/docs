---
title: "Google Maps / GeoLocator"
date: 2022-11-08
template: main.html
---
## Google Maps
### 설정 - iOS Error 
```swift title="AppDelegate.swift"
import UIKit
import Flutter 
import GoogleMaps // 이거 안해주면 오류남

@UIApplicationMain
@objc class AppDelegate: FlutterAppDelegate {
  override func application(
    _ application: UIApplication,
    didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?
  ) -> Bool {
    GMSServices.provideAPIKey("Google Maps API Key") // add here
    GeneratedPluginRegistrant.register(with: self)
    return super.application(application, didFinishLaunchingWithOptions: launchOptions)
  }
}
```


## GeoLocation
### Setting
#### iOS 
위치 권한, 백그라운드 위치 권한 설정.
```swift title="ios/Runner/info.plist"
<key>NSLocationWhenInUseUsageDescription</key>
<string>This app needs access to location when open.</string>
<key>NSLocationAlwaysUsageDescription</key>
<string>This app needs access to location when in the background.</string>
```