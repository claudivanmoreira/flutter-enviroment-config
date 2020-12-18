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
:rotating_light: The above command reports that the Android SDK installation was not found. Let's install it now.

## 3. Intall Android SDK Manager

1. Clique [here](https://developer.android.com/studio) and scroll to section "Command line tools only" and download the linux version
2. Create folder _/home/your-usernmae/Documents/DevZone/Tools/android-sdk_ 
3. Extract folder in downloaded .zip, and copy your content to directory _/home/your-usernmae/Documents/DevZone/Tools/android-sdk/cmdline-tools/latest
4. Setup enviroment variables to get access to sdkmanager CLI from terminal: 
  
```javascript
sudo gedit /etc/profile
```

and add the following content at end of file:

```javascript
export ANDROID_SDK_ROOT=/home/claudivan-moreira/Documentos/DevZone/Tools/android-sdk
export ANDROID_HOME=/home/claudivan-moreira/Documentos/DevZone/Tools/android-sdk/cmdline-tools/latest
export PATH=$PATH:$ANDROID_SDK_ROOT/cmdline-tools/latest/bin:$ANDROID_SDK_ROOT/cmdline-tools/tools/bin:$ANDROID_SDK_ROOT/build-tools:$ANDROID_SDK_ROOT/emulator:$ANDROID_SDK_ROOT/platform-tools
```

List available packages with sdkmanager to validate your configuration:

```javascript
sdkmanager --list

Available Packages:
  Path                                                                                     | Version      | Description                                           
  -------                                                                                  | -------      | -------                                               
  add-ons;addon-google_apis-google-15                                                      | 3            | Google APIs                                           
  add-ons;addon-google_apis-google-16                                                      | 4            | Google APIs                                          
  add-ons;addon-google_apis-google-17                                                      | 4            | Google APIs                                           
  add-ons;addon-google_apis-google-18                                                      | 4            | Google APIs                                           
  add-ons;addon-google_apis-google-19                                                      | 20           | Google APIs                                           
  add-ons;addon-google_apis-google-21                                                      | 1            | Google APIs                                           
  add-ons;addon-google_apis-google-22                                                      | 1            | Google APIs                                           
  add-ons;addon-google_apis-google-23                                                      | 1            | Google APIs                                           
  add-ons;addon-google_apis-google-24                                                      | 1            | Google APIs 
  .....
```

5. Install the tools to build and run android emulator. Using command "_sdkmanager --list_" you can get packages names to install. In my case, i installed latest version of build-tools and Android API 28/29 (Android 9/10). You can get the API level for android versions [here](https://developer.android.com/studio/releases/platforms)

```javascript
sdkmanager "build-tools;28.0.3" "platforms;android-28" "platforms;android-29"
```


## 4. Set Android SDK home to Flutter and Accept licenses


```javascript
flutter config --android-sdk /home/claudivan-moreira/Documentos/DevZone/Tools/android-sdk

flutter doctor --android-licenses
```
Restart your machine and revalidate your Flutter instalation:

```javascript
flutter doctor

[✓] Flutter (Channel stable, 1.22.5, on Linux, locale pt_BR.UTF-8)
[✓] Android toolchain - develop for Android devices (Android SDK version 28.0.3)
[!] Android Studio (not installed)
[!] Connected device
```

## 5. Creating Emulator

First, download your specific image for Android Virtual Devices. In my case, i will use the Android 10

```javascript
./sdkmanager "system-images;android-29;google_apis;x86"
```

And then, create your Virtual Device with command bellow:

```javascript
avdmanager create avd -n <device name> -k <image name>
```
Example:

```javascript
avdmanager create avd -n android10 -k "system-images;android-29;google_apis;x86"
```
## 6. Setup KVM permissions

```javascript
sudo apt install qemu-kvm
sudo adduser $USER kvm
sudo chown $USER /dev/kvm
```

## 6. Intall VSCode Editor

Clique [here](https://code.visualstudio.com/download), download and install linux version or by Ubuntu Store

## 7. Improve your VSCode Editor with extensions

- Flutter (Install full support for Flutter including Dart sintaxe highligth, autocomplete and execution)
- Flutter Tree (Similar to emmet)
- Awesome Flutter Snippets (Code snippets for Flutter)
- Dracula Official (Theme)
- GitLens (Git integration)

## 8. Create your Flutter Project


```javascript
flutter create hello-world
```

## 9. Configure your phisical phone (Optional)

You can run your flutter project directly on your physical phone as you develop.

To do this, enable developer mode and USB debugging. Then connect your cell phone with USB cable to your computer.

Validate that your device is accessible via the CLI of the flutter by running the command below on the terminal:

```bash
flutter devices

No devices detected.

Run "flutter emulators" to list and start any available device emulators.

If you expected your device to be detected, please run "flutter doctor" to diagnose potential issues. You may also try increasing the time to wait for connected devices with the --device-timeout flag. Visit
https://flutter.dev/setup/ for troubleshooting tips.

• Device 0041072637 is not authorized.
_You might need to check your device for an authorization dialog._
```

:rotating_light: In first time that you execute this command, an popup will be displayed in your phone. Confirm de option and re-execute the command:

```bash
flutter devices

1 connected device:

Moto E 4 (mobile) • 0041072637 • android-arm • Android 7.1.1 (API 25)
```

## 8. Scrspy (Optional)

This application provides display and control of Android devices connected on USB (or over TCP/IP). It does not 
require any root access. It works on GNU/Linux, Windows and macOS.

Clique [here](https://github.com/Genymobile/scrcpy)
