### **1. Installing Dart on Windows 11**

You have two main paths to install the Dart SDK locally.

_(Note: If you are planning to build mobile or web apps with Flutter, you don't need to install Dart separately! Downloading the Flutter SDK automatically includes the full Dart SDK.)_
#### **Option A: Using Chocolatey (Recommended)**

Chocolatey is a popular command-line package manager for Windows that handles downloading and path configurations for you.

1. Open **PowerShell** as an Administrator (Search for PowerShell in the Windows menu, right-click, and select "Run as administrator").
2. If you don't have Chocolatey installed, install it first by following the official instructions on chocolatey.org.
3. Once Chocolatey is ready, run the following command to install Dart:
    ```
    choco install dart-sdk
    ```
4. Close and reopen your terminal to apply the environment variables. Verify the installation by running:
    ```
    dart --version
    ```
    
#### **Option B: Manual ZIP Installation**

If you prefer not to use a package manager, you can install the SDK manually.

1. Go to the official **Dart SDK Archive** online and download the latest stable `.zip` file for Windows (x64).
2. Extract the `.zip` file to a permanent location on your computer (for example, `C:\tools\dart-sdk`).
3. Add Dart to your System PATH:
    - Press the Windows key, type **Environment Variables**, and hit Enter.
    - Click the **Environment Variables...** button.
    - Under "System variables" (or "User variables"), find the **Path** variable, select it, and click **Edit**.
    - Click **New** and paste the exact path to the Dart `bin` folder (e.g., `C:\tools\dart-sdk\bin`).
    - Click **OK** on all windows to save and apply.
4. Open a new Command Prompt or PowerShell window and verify by running `dart --version`.
### **2. Running Dart Programs Locally**

Once Dart is installed, you can write and execute code right from your terminal.

1. Open your favorite text editor (like Visual Studio Code or Notepad).
2. Write a simple Dart script. For example:
    ```
    void main() {
      print('Hello from Windows 11!');
    }
    ```
3. Save the file as `hello.dart` in a dedicated folder.
4. Open Command Prompt or PowerShell, and navigate to the folder where you saved your file using the `cd` (change directory) command:
    ```
    cd path\to\your\folder
    ```
5. Run the program using the `dart run` command:
    ```
    dart run hello.dart
    ```
    _You should immediately see "Hello from Windows 11!" printed in your console._

### **3. Running Dart Online via DartPad**

If you want to test Dart code quickly without installing anything, DartPad is the official browser-based playground.

1. Open your web browser and go to **dartpad.dev**.
2. You will see a split-screen interface. The left side is your code editor, and the right side is your console output.
3. Write your Dart code in the editor on the left.
4. Click the blue **Run** button at the top of the screen.
5. Your code will compile in the cloud, and the output will appear in the console pane on the right.