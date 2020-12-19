<p align="center">
  <img width="500" src="https://flutter.dev/assets/flutter-lockup-1caf6476beed76adec3c477586da54de6b552b2f42108ec5bc68dc63bae2df75.png" alt="Sublime's custom image"/>
</p>
<br>
<br>
<h1 align="center">Enviroment configuration for <br>Flutter Development (Linux Edition)</h1>
<br>
<br>


#### 1. Intall Java Development Kit and Java Runtime Enviroment

1.1. Validate that you have Java installed in your machine. 

```ruby

claudivan-moreira@claudivan:~$ javac --version

claudivan-moreira@claudivan:~$ java --version

```

1.2. If the above commands return error, then install Java


```ruby

claudivan-moreira@claudivan:~$ sudo apt-get install openjdk-11-jre

claudivan-moreira@claudivan:~$ sudo apt-get install openjdk-11-jdk

```

1.3. Validate your instalations:

```ruby

claudivan-moreira@claudivan:~$ javac --version
javac 11.0.9.1

```

```ruby

claudivan-moreira@claudivan:~$ java --version
openjdk 11.0.9.1 2020-11-04
OpenJDK Runtime Environment (build 11.0.9.1+1-Ubuntu-0ubuntu1.18.04)
OpenJDK 64-Bit Server VM (build 11.0.9.1+1-Ubuntu-0ubuntu1.18.04, mixed mode, sharing)
```

#### 2. Install KVM and Setup permissions

```ruby

claudivan-moreira@claudivan:~$ sudo apt install qemu-kvm
claudivan-moreira@claudivan:~$ sudo adduser $USER kvm
claudivan-moreira@claudivan:~$ sudo setfacl -m u:$USER:rwx /dev/kvm

```

#### 3. Intall Flutter SDK

```ruby

claudivan-moreira@claudivan:~$ sudo snap install flutter --classic

```
- Validate instalation

```ruby

claudivan-moreira@claudivan:~$ flutter doctor
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


#### 4. Intall and Setup Android SDK

4.1. Clique [here](https://developer.android.com/studio) and scroll to section _"Command line tools only"_ and download the linux version

4.2. Create folder to extract files 

```ruby

claudivan-moreira@claudivan:~$ mkdir -p ~/Documentos/DevZone/Tools/android/sdk/cmdline-tools/latest

```

4.3. Extract files inside folder _commandlinetools-linux-6858069_latest.zip**/cmdline-tools**_ to new directory created on step 4.2

4.4. Setup enviroment variables to get access to sdkmanager CLI from terminal:

```ruby

claudivan-moreira@claudivan:~$ sudo gedit /etc/profile

```

and add the following content at end of file:

```ruby

export ANDROID_SDK_ROOT=~/Documentos/DevZone/Tools/android/sdk/
export ANDROID_HOME=~/Documentos/DevZone/Tools/android/sdk
export PATH=$PATH:$ANDROID_SDK_ROOT/cmdline-tools/latest/bin:$ANDROID_SDK_ROOT/tools/bin:$ANDROID_SDK_ROOT/build-tools:$ANDROID_SDK_ROOT/emulator:$ANDROID_SDK_ROOT/platform-tools

```

4.5. Restart your machine or logout

4.6. Open terminal and download SDK packages (image and build tools) for Android Nogaut (7.1.1) using command below:

```ruby

claudivan-moreira@claudivan:~$ sdkmanager "platforms;android-25" "system-images;android-25;google_apis;x86_64" "build-tools;25.0.3"

```

4.7. Create your Android Virtual Device

```ruby

claudivan-moreira@claudivan:~$ avdmanager create avd -n <device name> -k <image name>

```

Example:


```ruby

claudivan-moreira@claudivan:~$ avdmanager create avd -n MOTOE_NOUGAT -k "system-images;android-25;google_apis;x86_64"

```

4.8. Now, execute your virtual device:

```ruby

claudivan-moreira@claudivan:~$ emulator @MOTOE_NOUGAT

```

- To list all available images you can run the command _sdkmanager --list_ and download using step 6
- To list all available virtual devices you can run the command _avdmanager list avd_ and executing using step 8
- To delete a virtual device you can run the command _avdmanager delete avd -n <avd name> (Ex: MOTOE_NOUGAT)_ and executing using step 8
  

#### 5. Intall VSCode Editor

Clique [here](https://code.visualstudio.com/download), download and install linux version or by Ubuntu Store


#### 6. Improve your VSCode Editor with extensions

- Flutter (Required)
- Flutter Tree (Optional)
- Awesome Flutter Snippets (Optional)
- Dracula Official (Optional)
- GitLens (Optional)

#### 9. Create your Flutter Project


```ruby

claudivan-moreira@claudivan:~$ flutter create hello-world

```

#### 10. Run project on Emulator

10.1. Open project created on step 9 in VSCode

10.2. Start emulator using step 4.8

10.3. In VSCode, select device to run your project

<p>
  <img width="800" src="https://github.com/claudivanmoreira/flutter-enviroment-config/blob/main/selecao_avd.png?raw=true" />
<p>

If your VSCode not recognize the device, restart VSCode


#### 11. Configure your phisical phone (Optional)

You can run your flutter project directly on your physical phone as you develop.

To do this, enable developer mode and USB debugging. Then connect your cell phone with USB cable to your computer.

11.1. Validate that your device is accessible via the CLI of the flutter by running the command below on the terminal:

```ruby

claudivan-moreira@claudivan:~$ flutter devices
No devices detected.

Run "flutter emulators" to list and start any available device emulators.

If you expected your device to be detected, please run "flutter doctor" to diagnose potential issues. You may also try increasing the time to wait for connected devices with the --device-timeout flag. Visit
https://flutter.dev/setup/ for troubleshooting tips.

• Device 0041072637 is not authorized.
_You might need to check your device for an authorization dialog._
```

11.2. In first time, when above command executed, an popup will be displayed in your phone. Confirm de option and re-execute the command:

```ruby

claudivan-moreira@claudivan:~$ flutter devices
1 connected device:

Moto E 4 (mobile) • 0041072637 • android-arm • Android 7.1.1 (API 25)

```

11.3. In VSCode, select device to run your project 


#### 12. Scrspy (Optional)

This application provides display and control of Android devices connected on USB (or over TCP/IP). It does not 
require any root access. It works on GNU/Linux, Windows and macOS.

Install:

```ruby

claudivan-moreira@claudivan:~$ apt install scrcpy

```

Connect your phone with USB cable and execute

```ruby

claudivan-moreira@claudivan:~$ scrcpy

```

### 13. Tips and Solutions

**Problem 1**: Your VS Code not runing your code in Android Emulator

**Solution**:
1) Disable the Flutter extension in VS Code
2) Restart the VS Code
3) Activate the Flutter extension again

And be happy!


