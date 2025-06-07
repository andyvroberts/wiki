
# Windows 11 
For a fresh Android Development environment on a clean windows 11 installation, yu shoudl first reset your PC to a clean OS and perform the setup dialogue without connecting to the internet.   
If you get stuck at the wireless connection menu with no way out, start a command prompt using Shift+F10 and type in 
```
OOBE\BYPASSNRO
```
This will restart the PC, and back at the wireless connection dialogue you will get a new option to bypass the connection. 


# Flutter Installation
You will need to install these tools and then the Flutter SDK:  
- Git. https://git-scm.com/downloads.  
- PowerShell v5 or later.  
- Flutter https://docs.flutter.dev/release/archive  

Once the SDK is downloaded, install using power shell with:  
```
Expand-Archive `
    –Path $env:USERPROFILE\Downloads\flutter_windows_3.29.1-stable.zip `
    -Destination $env:USERPROFILE\Dev\Flutter\SDK-3.29\
```
Then add the flutter bin directory to the windows PATH Environment Variable.  
```
C:\Users\<user>\Dev\Flutter\SDK-3.29\bin
```

Android Studio 2024.3 (Meerkat). https://developer.android.com/studio  
The google docs ask you to install these tools:  
- Android SDK Platform, API 35.0.2  
- Android SDK Command-line Tools  
- Android SDK Build-Tools  
- Android SDK Platform-Tools  
- Android Emulator  

They were all installed by default apart from the command line tools, but these can be added once you open Android Studio and go to "Settings" or "More Actions" on the startup splash screen.    

To use the Android Emulators, you must enable the Windows Hypervisor for VM acceleration.  
Go to the "Turn windows features on or off" dialogue box and make sure the approproate item is checked.  If it needs to be isntalled do it, then restart.  

[Use Windows Hypervisor for VM accelleration](./win-hypervisor-option.png)


## Flutter Commands
Check your installation.  
```
flutter doctor
flutter doctor -v
```
After installing Android Studio and the Emulator, you must accept the android licences.  
```
flutter doctor --android-licenses
```

## Android Studio
To open a Flutter peoject you must first install the Plugin.  
In Android Studio go to File > Settings > Plugins and install Flutter.  

Now you can open a new Flutter Project from the menu.  
Add the Flutter path when prompted (e.g. C:\Users\avrob\Dev\Flutter) then you can continue.  
