# Cài đặt với React Native thấp hơn 0.60

> **Lưu ý** : **APP_SECRET_VALUE** là đoạn mã được tạo ra ở bước [cài đặt app center](../Appcenter.md)

## Link thư viện :

```python
react-native link appcenter
react-native link appcenter-analytics
react-native link appcenter-crashes
```

<details>
    <summary>
        IOS
    </summary>

- Nếu gặp lỗi :

  ```
  Added code to initialize iOS App Center SDK in ios/reactnativesample/AppDelegate.m
  Analyzing dependencies [!] Unable to find a specification for AppCenterReactNativeShared (~> {version})

  ```

- Tại thư mục ios:
  ```
  pod repo update
  ```
- Link lại :
  ```
  react-native link
  ```
- Tạo file `AppCenter-Config.plist` trong thư mục ios với nội dung :

  ```
  <?xml version="1.0" encoding="UTF-8"?>
  <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "https://www.apple.com/DTDs/PropertyList-1.0.dtd">
  <dict version="1.0">
      <dict>
      <key>AppSecret</key>
      <string>{APP_SECRET_VALUE}</string>
      </dict>
  </dict>
  ```

- Thêm file `AppCenter-Config.plist` vừa tạo vào project
  - Mở file .xcworkspace bằng xcode
  - Chuột phải vào tên project chọn **Add Files to {tênproject}**
    ![img](../../readmeasset/addToXcode.png)
  - Tìm đến file `AppCenter-Config.plist` vừa tạo
    ![img](../../readmeasset/pickFileConfig.png)
- Cấu hình file `AppDelegate.m` để có thể sử dụng

  - import :
    ```
        #import <AppCenterReactNative/AppCenterReactNative.h>
        #import <AppCenterReactNativeAnalytics/AppCenterReactNativeAnalytics.h>
        #import <AppCenterReactNativeCrashes/AppCenterReactNativeCrashes.h>
        #import <AppCenterReactNativePush/AppCenterReactNativePush.h>
    ```
  - sử dụng :

    ```
        [AppCenterReactNative register];
        [AppCenterReactNativeAnalytics registerWithInitiallyEnabled:true];
        [AppCenterReactNativeCrashes registerWithAutomaticProcessing];
        [AppCenterReactNativePush register];
    ```

  - Kết quả :
    ![img](../../readmeasset/codeInAppDelegate.png)

</details>

<details>
    <summary>
        Android
    </summary>

- Tạo file `appcenter-config.json` trong đường dẫn `android/app/src/main/assets/` với nội dung :

  ```
  {
    "app_secret": "{APP_SECRET_VALUE}"
  }
  ```

- Thêm vào file `strings.xml` trong đường dẫn `res/values/strings.xml` :
  ```
  <string name="appCenterCrashes_whenToSendCrashes" moduleConfig="true" translatable="false">ASK_JAVASCRIPT</string>
  <string name="appCenterAnalytics_whenToEnableAnalytics" moduleConfig="true" translatable="false">ALWAYS_SEND</string>
  ```
  </details>
