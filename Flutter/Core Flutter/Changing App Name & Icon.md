### **Part 1: How to Change the App Name**

This is the name that actually shows up under the icon on the user's phone. You have to change it in two separate native files.

**For Android:**

1. Open your project and go to: `android/app/src/main/AndroidManifest.xml`
2. Look for the `<application>` tag.
3. Find the `android:label` property and change its value to your new app name.
    
    ```
    <application
        android:label="My Awesome App" 
        android:icon="@mipmap/ic_launcher">
    ```

**For iOS:**

1. Go to: `ios/Runner/Info.plist`
2. Look for the `CFBundleDisplayName` key.
3. Change the `<string>` value directly below it.
    
    ```
    <key>CFBundleDisplayName</key>
    <string>My Awesome App</string>
    ```

_(Note: Stop your app completely and run `flutter run` again for these name changes to take effect)._

### **Part 2: How to Change the App Logo (The Smart Way)**

To avoid resizing images manually, we will use the `flutter_launcher_icons` package. It takes one high-resolution image and auto-generates all the correct sizes for both iOS and Android.

**Step 1: Get your image ready** Take your high-res logo (a `1024x1024` PNG with a transparent background works best) and put it in your `assets/` folder. For example: `assets/icon.png`.

**Step 2: Add the package** Open your terminal and run this command to add it to your development dependencies:

```
flutter pub add --dev flutter_launcher_icons
```

**Step 3: Configure it in `pubspec.yaml`** Open your `pubspec.yaml` file. Scroll all the way to the bottom and paste this configuration block. This tells the package where your image is and which platforms to generate icons for.

```
flutter_launcher_icons:
  android: "launcher_icon"
  ios: true
  image_path: "assets/icon.png"
  min_sdk_android: 21 # Required for newer Android versions
```

**Step 4: Run the generator** Open your terminal one last time and tell the package to do its magic by running:

```
flutter pub run flutter_launcher_icons
```