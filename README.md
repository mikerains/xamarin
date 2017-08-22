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
  * Uncheck "Optimize code"
  
#### Calling WebApi on my Local VStudio  
* Android Phone needs to trust the Local Certificate
  * In Android - Settings - Security - Install From SD Card
    * I exported the certificate in Windows Cert Manager, copied over USB to my phone, and then installed in settings
  * https://stackoverflow.com/questions/29279486/how-to-resolve-enter-the-password-for-credential-storage-issue
  * About Certificates: http://info.ssl.com/article.aspx?id=12149
  * More about certs: https://stackoverflow.com/questions/642284/apache-with-ssl-how-to-convert-cer-to-crt-certificates
  

### App Crashes on phone, no Stack or Exception in VStudio Debugger
* Command prompt in android-srd\platf0rm-tools> adb logcat AndroidRuntime:E *:S

### App crashes, android doesn't trust the Local Service Fabric machine's Certificate
System.Net.Http.HttpRequestException: An error occurred while sending the request ---> System.Net.WebException: Error: TrustFailure (The authentication or decryption has failed.) ---> System.IO.IOException: The authentication or decryption has failed. ---> System.IO.IOException: Error while sending TLS Alert (Fatal:InternalError): System.IO.IOException: The authentication or decryption has failed. ---> Mono.Security.Protocol.Tls.TlsException: Invalid certificate received from server. Error code: 0xffffffff800b010f
  at Mono.Security.Protocol.Tls.RecordProtocol.EndReceiveRecord (System.IAsyncResult asyncResult) [0x00037] in <d2bf9ddce2b945f79db1e7c4354bafea>:0 
  at Mono.Security.Protocol.Tls.SslClientStream.SafeEndReceiveRecord (System.IAsyncResult ar, System.Boolean ignoreEmpty) [0x00000] in <d2bf9ddce2b945f79db1e7c4354bafea>:0 
  at Mono.Security.Protocol.Tls.SslClientStream.NegotiateAsyncWorker (System.IAsyncResult result) [0x00071] in <d2bf9ddce2b945f79db1e7c4354bafea>:0 
   --- End of inner exception stack trace ---
  at Mono.Security.Protocol.Tls.SslClientStream.EndNegotiateHandshake (System.IAsyncResult result) [0x00032] in <d2bf9ddce2b945f79db1e7c4354bafea>:0 
  at Mono.Security.Protocol.Tls.SslStreamBase.AsyncHandshakeCallback (System.IAsyncResult asyncResult) [0x0000c] in <d2bf9ddce2b945f79db1e7c4354bafea>:0  ---> System.IO.IOException: Unable to write data to the transport connection: Connection reset by peer. ---> System.Net.Sockets.SocketException: Connection reset by peer
  at System.Net.Sockets.Socket.EndSend (System.IAsyncResult asyncResult) [0x00012] in <a547bd0d78184f26ab08d022f013c1e1>:0 
...
   --- End of inner exception stack trace ---
  at Mono.Security.Protocol.Tls.SslStreamBase.EndRead (System.IAsyncResult asyncResult) [0x0004b] in <d2bf9ddce2b945f79db1e7c4354bafea>:0 
  at Mono.Net.Security.Private.LegacySslStream.EndAuthenticateAsClient (System.IAsyncResult asyncResult) [0x0000e] in <a547bd0d78184f26ab08d022f013c1e1>:0 
  at Mono.Net.Security.Private.LegacySslStream.AuthenticateAsClient (System.String targetHost, System.Security.Cryptography.X509Certificates.X509CertificateCollection clientCertificates, System.Security.Authentication.SslProtocols enabledSslProtocols, System.Boolean checkCertificateRevocation) [0x0000e] in <a547bd0d78184f26ab08d022f013c1e1>:0 
...
  at System.Runtime.CompilerServices.TaskAwaiter.ValidateEnd (System.Threading.Tasks.Task task) [0x00008] in <3fd174ff54b146228c505f23cf75ce71>:0 
  at System.Runtime.CompilerServices.ConfiguredTaskAwaitable`1+ConfiguredTaskAwaiter[TResult].GetResult () [0x00000] in <3fd174ff54b146228c505f23cf75ce71>:0 
  at Hatcx.Services.UserManagement.Client.UserManagementOperations
  +<ExecuteRequestWithoutResponseBodyAsync>d__10.MoveNext () [0x001b9] in <dc5bf32d73df4163863fcaccf979d0ad>:0 
--- End of stack trace from previous location where exception was thrown ---
...
  at System.Runtime.CompilerServices.TaskAwaiter.ValidateEnd (System.Threading.Tasks.Task task) [0x00008] in <3fd174ff54b146228c505f23cf75ce71>:0 
  at System.Runtime.CompilerServices.ConfiguredTaskAwaitable`1+ConfiguredTaskAwaiter[TResult].GetResult () [0x00000] in <3fd174ff54b146228c505f23cf75ce71>:0 
  at Hatcx.Services.UserManagement.Client.UserManagementOperationsExtensions+<UpdateUserAsync>d__3.MoveNext () [0x00075] in <dc5bf32d73df4163863fcaccf979d0ad>:0 
 +<ExecuteRequestWithoutResponseBodyAsync>d__10.MoveNext () [0x001b9] in <dc5bf32d73df4163863fcaccf979d0ad>:0 
--- End of stack trace from previous location where exception was thrown ---
...
<3fd174ff54b146228c505f23cf75ce71>:0 
  at System.Runtime.CompilerServices.TaskAwaiter.GetResult () [0x00000] in <3fd174ff54b146228c505f23cf75ce71>:0 
  at Hatcx.Mobile.Cost.Services.DataProvider+<UpdateUserProfileAsync>d__20.MoveNext () [0x00153] in C:\hatcxgit\HATCXCost\src\HatcxCost\Services\DataProvider.cs:263 
  
Diagnosis: When .Net is running on a Windows machine, it has access to the certificate store, and knows about local certificates installed there.  MONO does not have access to the store, so we need to handle untrusted certificates in the ServicePointManager callback.

In HatcxCostDroid's LaunchActivity.OnCreate:
````
//ServicePointManager.ServerCertificateValidationCallback += new RemoteCertificateValidationCallback((sender, certificate, chain, policyErrors) => { return true; });
ServicePointManager.ServerCertificateValidationCallback += (sender, certificate, chain, policyErrors) =>
{
    string[] allowThumbprints = .....; //get from config somewhere
    if (errors == SslPolicyErrors.None) return true;

    // get the thumbprint of the certificate that is being validated
    var currentCertificateThumbprint = (certificate as X509Certificate2)?.Thumbprint;

    // determine if any of the allowed thumbprints matches the current thumbprint
    return !string.IsNullOrWhiteSpace(currentCertificateThumbprint) 
        && allowedThumbprints.Any(thumbprint => thumbprint.Equals(currentCertificateThumbprint, StringComparison.InvariantCultureIgnoreCase));
};
````



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

