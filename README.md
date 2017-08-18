# Xamarin Examples

```` cli
echo "# xamarin" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/mikerains/xamarin.git
git push -u origin master
````


# Configuration
## Install Xamarin into Visual Studio 2017
* https://developer.xamarin.com/guides/android/getting_started/installation/windows/

## Install Visual Studio Android Emulator
* https://blogs.msdn.microsoft.com/devops/2014/11/12/introducing-visual-studios-emulator-for-android/
* https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/visual-studio-android-emulator/

# Debugging

### Debugging with Local Android Device
* https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-device/
* https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/
  * General USB Drivers https://developer.android.com/studio/run/oem-usb.html#Drivers
  * Kyocera Phone USB Drivers http://www.kyoceramobile.com/support/drivers/


### Debugging with VS Android Emulator
* Troubleshooting the Visual Studio Emulator for Android  https://msdn.microsoft.com/en-us/library/mt228282.aspx
* http://dotnetbyexample.blogspot.hu/2016/02/fix-for-could-not-connect-to-debugger.html
* https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/visual-studio-android-emulator/

* Configure Hyper-V Machine to "Migrate to Different Physical Processor"
* Configure Android Project to not do the "Fast Deployment"
* Make sure Studio Project Proeprties - Build - that Optimize Code is not checked.
* Also in Android Options, I have needed to 
  * checkmark Enable developer instrumentation ( Debugging Tooling, and set ) , 
  * set Debugger to .Net/Xamarin, and Linking to "Sdk and User Assemblies"
  
#### Calling WebAPii on my Local VStudio  
* Android Phone needs to trust the Local Certificate
  * In Android - Settings - Security - Install From SD Card
    * I exported the certificate in Windows Cert Manager, copied over USB to my phone, and then installed in settings
  * https://stackoverflow.com/questions/29279486/how-to-resolve-enter-the-password-for-credential-storage-issue
  * About Certificates: http://info.ssl.com/article.aspx?id=12149
  * More about certs: https://stackoverflow.com/questions/642284/apache-with-ssl-how-to-convert-cer-to-crt-certificates
  

### App Crashes on phone, no Stack or Exception in VStudio Debugger
* Command prompt in android-srd\platf0rm-tools> adb logcat AndroidRuntime:E *:S



First of all, I got into these samples from working through Xamarin.com's "Application Fundamentals", and the first sample app is from https://developer.xamarin.com/guides/android/application_fundamentals/services/creating-a-service/bound-services/

[Bound Service](https://developer.xamarin.com/samples/monodroid/ApplicationFundamentals/ServiceSamples/BoundServiceDemo/)

## Other Selections from https://developer.xamarin.com/samples/android/all/

[Azure ADB2C Auth](https://developer.xamarin.com/samples/xamarin-forms/WebServices/AzureADB2CAuth/)

[Azure Storage](https://developer.xamarin.com/samples/xamarin-forms/WebServices/AzureStorage/)

[Azure Search](https://developer.xamarin.com/samples/xamarin-forms/WebServices/AzureSearch/)

[Grid Layout](https://developer.xamarin.com/samples/xamarin-forms/FormsGridLayout/)

[JNI](https://developer.xamarin.com/samples/monodroid/JNIDemo/)

[Intro to Xamarin Forms](https://developer.xamarin.com/samples/xamarin-forms/GettingStarted/)

[Master Detail Page](https://developer.xamarin.com/samples/xamarin-forms/Navigation/MasterDetailPage/)

[Media Browser](https://developer.xamarin.com/samples/monodroid/android5.0/MediaBrowserService/)

[Multi-Touch Tracking](https://developer.xamarin.com/samples/monodroid/ApplicationFundamentals/FingerPaint/)

