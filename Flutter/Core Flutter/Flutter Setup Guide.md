## 1. System Requirements

Before starting, ensure your system meets the following:

- Windows 10/11 (64-bit)
- At least 8 GB RAM (16 GB recommended)
- SSD storage recommended
- Administrator access
- Virtualization enabled (for emulator performance)
# 2. Install Flutter SDK

## Step 1: Download Flutter

Download the latest stable SDK from the official source:  
Flutter SDK
## Step 2: Extract SDK

- Extract the downloaded ZIP file
- Move it to a clean directory:

```
C:\flutter
```

Avoid placing it inside `Program Files` to prevent permission issues.
## Step 3: Configure Environment Variables

1. Open Start Menu → search **Environment Variables**
2. Click **Edit the system environment variables**
3. Click **Environment Variables**
4. Under **System Variables**, find and edit `Path`
5. Add the following:

```
C:\flutter\bin
```

6. Click OK and restart your terminal
## Step 4: Verify Installation

Open Command Prompt or PowerShell and run:

```
flutter doctor
```

This command checks missing dependencies.
# 3. Install Android Studio

## Step 1: Download

Download from:  
[Android Studio](https://developer.android.com/studio)
## Step 2: Install Android Studio

During installation:

- Choose **Standard Installation**
- Ensure the following components are selected:
    - Android SDK
    - Android SDK Platform
    - Android Virtual Device (AVD)

Complete installation.
## Step 3: Initial Setup

When launching Android Studio for the first time:

- Select **Do not import settings**
- Choose **Standard setup**
- Allow all required components to download
# 4. Configure Android SDK Properly

Open Android Studio and navigate to:

```
File → Settings → Android SDK
```
## Under SDK Platforms:

- Install the latest stable Android version (API 33 or higher)
## Under SDK Tools:

Ensure the following are installed:

- Android SDK Build-Tools
- Android Emulator
- Android SDK Platform-Tools
- Android SDK Command-line Tools (important)

Click Apply to install missing components.
# 5. Set ANDROID_HOME (If Required)

If Flutter does not detect the SDK automatically:
## Step 1: Locate SDK Path

Typical path:

```
C:\Users\<your-username>\AppData\Local\Android\Sdk
```

## Step 2: Add Environment Variable

Add:

```
ANDROID_HOME = above path
```
## Step 3: Update PATH

Add these entries:

```
%ANDROID_HOME%\platform-tools  
%ANDROID_HOME%\cmdline-tools\latest\bin
```

Restart terminal after changes.
# 6. Accept Android Licenses

Run the following command:

```
flutter doctor --android-licenses
```

Type `y` to accept all licenses.
# 7. Create and Run Android Emulator

Open Android Studio:

```
Tools → Device Manager
```

Steps:

1. Click **Create Device**
2. Select a Pixel device
3. Choose system image (API 33 or latest)
4. Finish setup
5. Start emulator
# 8. Final Verification

Run again:

```
flutter doctor
```

Expected output:

- Flutter: Installed
- Android toolchain: Installed
- Android Studio: Installed
- Connected device: Available
# 9. Run Your First Flutter App

Create a new project:

```
flutter create my_app  
cd my_app
```

Run the application:

```
flutter run
```

Ensure emulator or physical device is running.
# 10. Optional: Install Code Editor

You may install:  
[Visual Studio Code](https://code.visualstudio.com/Download)

**Recommended extensions:**
- Flutter
- Dart
# 11. Troubleshooting

## Issue: flutter not recognized

- Ensure PATH includes `C:\flutter\bin`
- Restart terminal
## Issue: Android toolchain not detected

- Verify SDK installation in Android Studio
- Ensure command-line tools are installed
## Issue: No devices available

- Start emulator or connect a physical device
- Run:

```
flutter devices
```
## Issue: Emulator is slow

- Enable virtualization in BIOS
- Ensure hardware acceleration is enabled
# 12. Notes for Professional Setup

- Prefer using a physical device for faster testing
- Keep Flutter updated:

```
flutter upgrade
```

- Avoid placing SDKs in restricted directories
- Maintain a clean project structure from the beginning