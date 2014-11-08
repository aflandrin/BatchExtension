BatchExtension
===========================

BatchExtension is an Openfl extension for batch https://batch.com/

Installation
------------
Add the link to batch extension to your project.xml
```xml
<include path="extensions/Haxe-Openfl-Batch-extension" if="mobile"/>
```
Android
------------

Add to your AndroidManifest.xml

```xml

	<service android:name="com.batch.android.BatchPushService" />
		<receiver android:name="com.batch.android.BatchPushReceiver" android:permission="com.google.android.c2dm.permission.SEND"> 
		  <intent-filter> 
			<action android:name="com.google.android.c2dm.intent.RECEIVE" /> 
			<category android:name="::APP_PACKAGE::" /> 
		  </intent-filter>  
		</receiver>

	<activity android:name="MainActivity">
		<!-- filter for URI schemes -->
		<intent-filter>
			<action android:name="android.intent.action.VIEW"/>
			<category android:name="android.intent.category.DEFAULT"/>
			<category android:name="android.intent.category.BROWSABLE" />
			<data android:scheme="batchXXXX" />
		</intent-filter>
	</activity>
	```

```xml
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<uses-permission android:name="android.permission.INTERNET" />

<permission android:name="::APP_PACKAGE::.permission.C2D_MESSAGE" android:protectionLevel="signature" />
<uses-permission android:name="::APP_PACKAGE::.permission.C2D_MESSAGE" />
	
<!-- GCM requires a Google account. -->
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
<!-- App receives GCM messages. -->
<uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />

<uses-permission android:name="android.permission.WAKE_LOCK" />
<uses-permission android:name="android.permission.VIBRATE" />  
```

IOS
------------

Add build link to your project.xml
<ios linker-flags="-force_load /path_to_framework/Batch.framework/Batch" />

Add now the batch framework to your xcode project.


Usage
------------


