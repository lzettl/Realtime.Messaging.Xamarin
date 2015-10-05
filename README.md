# Realtime.Messaging.Xamarin

Realtime messaging SDK for Xamarin. The Messaging Service is a highly-scalable pub/sub message broker. Using your favorite programming language you'll be able to broadcast messages to millions of users, reliably and securely. It's all in the cloud so you don't need to manage servers. 

## Platforms

Supports Android, iOS, and Windows Phone 8 Silverlight.

## Implementation

This repository includes both the SDK and a sample application using Xamarin Forms iOS, Android, and Windows Phone 8 Silverlight. The SDK includes a platform agnosted Realtime.Messaging project as well as a platform specific 'plugin'. The Android version uses OKHTTP.ws Binding Libraries. iOS uses SocketRocket Binding Libraries. The Windows Phone version uses Websockets Portable and rda.Sockets.

https://github.com/mattleibow/square-bindings

https://github.com/NVentimiglia/WebSocket.Portable


## Installation

#### NUGET
The SDK is avaliable via Nuget. Please include the NugetPackage to all projects. This includes the common PCL as well as your Xamarin platform project.

#### IOS

For IOS 9, you will need to include a key to your **PList.info**. This may be done in notepad or any text editor.

> App Transport Security has blocked a cleartext HTTP (http://) resource load since it is insecure. Temporary exceptions can be configured via your app's Info.plist file." (See also Apple's corresponding tech note.). 
One way to workaround: Add an NSAppTransportSecurity key to the Info.plist. Under that key, add a dictionary that contains a single NSAppTransportSecurity key set to true: 


`````
<key>NSAppTransportSecurity</key>
<dict>
   <key>NSAllowsArbitraryLoads</key> <true/>
</dict>.
`````

#### Android

I had an issue where OKHttp was referenced twice in my android project (From modernhttpclient and OKHttp.ws). This causes an error when building as it tried to include the java dependencies twice. The solution was to manually remove the reference (not the package, just the reference) from the Android project.


#### Dependency Service
I had issues with the dependency service and the linker. Simply put, the [Perserve] annotation *sometimes* works. If it fails, you will get a "Dependency Service Failed" exception. To fix this, we include a static Link() method within each platform implementation that may be called. This will guarantee that the linker will not strip the solution.

````
// Inside AppDelegate.cs
Realtime.Messaging.IOS.WebsocketConnection.Link();

````

## Sample

Sample of the http://realtime.co messaging framework using Xamarin Forms. Source code included under /Sample/

![Xamarin.Droid Client](xamarin.gif)

#### Usage

- Add your application keys to MainView.cs
- Run the application

#### Questions

Post onto the Github issue system or contact me via my [blog](http://nicholasventimiglia.com)
