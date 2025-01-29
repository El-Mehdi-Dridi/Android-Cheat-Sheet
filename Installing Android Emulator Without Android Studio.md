### Installing Android Emulator Without Android Studio
Normally, Android Studio is required to run code using its Android Emulator (AVD). However, if you only need the AVD Emulator and not Android Studio itself, installing the full IDE can be unnecessary.

In this guide, I’ll show you how to install and run the AVD Emulator on your PC without needing Android Studio.

First we should get tools package from https://developer.android.com/studio

![aaa](https://github.com/user-attachments/assets/2ac1b6cc-5229-4de0-9681-435e540efafa)

After downloading the ZIP file for your OS, you should extract it. Once extracted, you will have the tools package for your OS.

Next, we will download the **platform-tools** and **emulator** packages. The **platform-tools** package contains tools for interacting with Android devices when connected to your computer, while the emulator package includes the Android emulator. To install these, we will use **sdkmanager.bat** located in the **cmdline-tools/bin** directory.

but first you should  move all files inside the directory **cmdline-tools/** to **cmdline-tools/latest/** 

![image](https://github.com/user-attachments/assets/342aa949-db7e-49c6-81d1-507a2e982f5d)


Than try running this command 

```bash
./sdkmanager.bat --list
```
You will get a list of all packages that are available for installation.

![image](https://github.com/user-attachments/assets/8cb9463d-3f95-4fe0-9c6a-3cce0c1e67d6)

After that you should install the **emulator** and **platform-tools** by running this command 
```bash
./sdkmanager.bat platform-tools emulator
```
Now you are able to create your AVD by runnnig these commands

```
./sdkmanager.bat "platforms;android-30"
        
./sdkmanager.bat "build-tools;30.0.0"
        
./sdkmanager.bat "system-images;android-30;google_apis;x86_64"

./avdmanager.bat create avd --name AVD30 --package "system-images;android-30;google_apis;x86_64"
```
Now, you are able to run your emulator with this command

![image](https://github.com/user-attachments/assets/c3bc6b59-c669-4d81-b743-e284580db045)

![image](https://github.com/user-attachments/assets/4783d4bd-edd8-433a-8bd8-53650a47135a)




