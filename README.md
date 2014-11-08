BatchExtension
===========================

BatchExtension is an Openfl extension for batch https://batch.com/

Installation
------------
Add the link to batch extension to your project.xml
```xml
<include path="extensions/BatchExtension" if="mobile"/>
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
```xml
<ios linker-flags="-force_load /path_to_framework/Batch.framework/Batch" />
```

Add now the batch framework to your xcode project.


Usage
------------

-- Import
```xml
import BatchExtension;
```

-- Add listener to redeem offer
```xml
BatchExtension.addEventListener("REDEEM_OFFER", onReceiveRedeemOffer);
public static function onReceiveRedeemOffer(e:BatchEvent) {
	trace(e);
	trace(e.arg1);
	trace(e.arg2);
} 
```

-- init batch extension with your API keys (you can pass the gcm sender id if you want to init push but it's not mandatory)
```xml
BatchExtension.initBatch("BATCH_API_KEY", "your_gcm_sender_id");
```

for ios just use
```xml
BatchExtension.initBatch("BATCH_API_KEY", "");
```

Now in batch.com dashboard you can configure a message which will be display when user receive an offer buy adding custom parameters

reward_title --> Congratulations

reward_message --> Thanks to Openfl

Features
===========================
- Register to batch
- listen to onRedeemAutomaticOffer
- Push service

To do
=========================== 
- Redeem an offer using a code
- Using links for automatic items
- Restoring items


