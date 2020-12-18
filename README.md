# flutter-enviroment-config (Ubuntu Edition)

## 1. Intall Java Development Kit and Java Runtime Enviroment

```javascript
sudo apt-get install openjdk-11-jre
```

```javascript
sudo apt-get install openjdk-11-jdk
```

- Validate your instalation:

```javascript
javac --version

javac 11.0.9.1
```

```javascript
java --version

openjdk 11.0.9.1 2020-11-04
OpenJDK Runtime Environment (build 11.0.9.1+1-Ubuntu-0ubuntu1.18.04)
OpenJDK 64-Bit Server VM (build 11.0.9.1+1-Ubuntu-0ubuntu1.18.04, mixed mode, sharing)
```

## 2. Intall Flutter SDK

```javascript
sudo snap install flutter --classic
```
- Validate instalation

```javascript
flutter doctor

[✓] Flutter (Channel stable, 1.22.5, on Linux, locale pt_BR.UTF-8)
[✗] Android toolchain - develop for Android devices
    ✗ Unable to locate Android SDK.
      Install Android Studio from: https://developer.android.com/studio/index.html
      On first launch it will assist you in installing the Android SDK components.
      (or visit https://flutter.dev/docs/get-started/install/linux#android-setup for detailed instructions).
      If the Android SDK has been installed to a custom location, set ANDROID_SDK_ROOT to that location.
      You may also want to add it to your PATH environment variable.

[!] Android Studio (not installed)
[!] Connected device
    ! No devices available
```

## 3. Intall Android SDK Manager

1. Clique [here](https://developer.android.com/studio) and scroll to section "Command line tools only" and download the linux version
2. Create folder _/home/your-usernmae/Documents/DevZone/Tools/android-sdk_ 
3. Extract folder in downloaded .zip, rename folder cmdline-tools to _adnroid-sdk_ and copy to _/home/your-usernmae/Documents/DevZone/Tools_
4. Setup enviroment variables to get access to sdkmanager CLI from terminal: 
  
```javascript
sudo gedit /etc/profile
```

and add the following content at end of file:

export ANDROID_SDK_ROOT=/home/claudivan-moreira/Documentos/DevZone/Tools/android-sdk/
export ANDROID_HOME=/home/claudivan-moreira/Documentos/DevZone/Tools/android-sdk/
export PATH=$PATH:$HOME/bin:$ANDROID_SDK_ROOT:$ANDROID_SDK_ROOT/emulator:$ANDROID_SDK_ROOT/platform-tools:$ANDROID_SDK_ROOT/bin:$ANDROID_HOME

validate your configuration:

```javascript
sdkmanager --list
```

## 4. Intall VSCode Editor

Clique [here](https://code.visualstudio.com/download), download and install linux version or by Ubuntu Store

## 5. Improve your VSCode Editor with extensions

- Flutter (Install full support for Flutter including Dart sintaxe highligth, autocomplete and execution)
- Flutter Tree (Similar to emmet)
- Awesome Flutter Snippets (Code snippets for Flutter)
- Dracula Official (Theme)
- GitLens (Git integration)

## 6. Configure your phisical phone (Optional)

You can run your flutter project directly on your physical phone as you develop.

To do this, enable developer mode and USB debugging. Then connect your cell phone with USB cable to your computer.

Validate that your device is accessible via the CLI of the flutter by running the command below on the terminal:

```bash
flutter devices
```

You can get more details [here](https://developer.android.com/studio/debug/dev-options)

## 7. Scrspy (Optional)

This application provides display and control of Android devices connected on USB (or over TCP/IP). It does not 
require any root access. It works on GNU/Linux, Windows and macOS.

Clique [here](https://github.com/Genymobile/scrcpy)

## 5. Scrspy (Optional)
