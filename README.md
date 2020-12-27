# disclaimer

This is a fork of the [Flutter wifi plugin](https://github.com/once10301/wifi) that looks unmaintained as of 2020/12/27.

This fork adds the following features:
- `connection` method: added Android 10 compatibility
- `connection` method: fix on Android 8 when the device wasn't already connected to another Wi-Fi network
- `connection` method: added support for open networks, just leave the `password` field null or empty (Android and iOS)
- `list` method: added BSSID information (Android only)
- `wifiEnabled` method: new! Checks whether the Wi-FI adapter is eanbled (Android only)

## Setup
Add this dependency to your `pubspec.yaml`:

```yaml
dependencies:
  wifi:
    git:
      url: https://github.com/thearaks/wifi
      ref: develop
```

Then run `pub upgrade` to fetch the latest commit.


# wifi

This plugin allows Flutter apps to get wifi ssid and list, connect wifi with ssid and password.

This plugin works Android.

iOS later released.

<br/>

Sample usage to check current status:

```dart
import 'package:wifi/wifi.dart';

String ssid = await Wifi.ssid;

//Signal strength， 1-3，The bigger the number, the stronger the signal
int level = await Wifi.level;

String ip = await Wifi.ip;

var result = await Wifi.connection('ssid', 'password');

// only work on Android.
List<WifiResult> list = await Wifi.list('key'); // this key is used to filter
```
When you use connection on iOS (iOS 11 only)

1. 'build Phass' -> 'Link Binay With Libraries' add 'NetworkExtension.framework'
    ![NetworkExtension](https://github.com/once10301/wifi/blob/master/png/NetworkExtension.png)

2. in 'Capabilities' open 'Hotspot Configuration'

    ![NetworkExtension](https://github.com/once10301/wifi/blob/master/png/Hotspot%20Configuration.png)

3. If you device is iOS12, in 'Capabilities' open 'Access WiFi Information'

    ![NetworkExtension](https://github.com/once10301/wifi/blob/master/png/Access%20WiFi%20Information.png)

If you want to use Wifi.list on iOS, 

reference http://baixin.io/2017/01/iOS_Wifilist/

## Getting Started

For help getting started with Flutter, view our online
[documentation](https://flutter.io/).

For help on editing plugin code, view the [documentation](https://flutter.io/developing-packages/#edit-plugin-package).
