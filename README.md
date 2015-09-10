[KIDOZ](http://www.kidoz.net) SDK Sample App
=================================

*Updated to KIDOZ SDK version 0.1.0* 

This Android application project provides an example of the [KIDOZ](http://www.kidoz.net) SDK integration.
It is compiled with Android 4.0 (API level 14) and supports any device running this Android version or higher.

The example application contains the following creative tools:
* Interstitial content tool - ```The Feed```
* KIDOZ's default button - ```The Gift Button```

#Integration
When integrating the SDK with your application, please make sure to use the latest SDK version, which can be downloaded from our [developers portal](http://www.kidoz.net).

###Include the library
On android studio you can include the library directly in your Gradle project:

 - 	Add the following to your app's `build.gradle`:
```gradle
dependencies {
	    compile 'com.kidoz.sdk:KidozSDK:0.1.0'
}
``` 

###Initiate the KIDOZ SDK
When initiating the SDK, please make sure to use your given `publisherID` and `securityToken`, which can be retrieve from your account on [developers portal](http://www.kidoz.net).

 - 	Inside your main activity onCreate add the following line:
```java
@Override protected void onCreate(Bundle savedInstanceState)
{
	super.onCreate(savedInstanceState);
	KidozSDK.initialize(getApplicationContext(), "publisherID", "securityToken");
	//the rest of your main activity onCreate
}
```

###Creating an instance of Interstitial View
 - 	Inside your desired activity or fragment create an instance of `InterstitialView` by adding the following lines:

> MainActivity.java

```java
public class MainActivity extends FragmentActivity
{
	InterstitialView mInterstitialView;
	
	private void initInterstitialView()
	{
		mInterstitialView = new InterstitialView.Builder(MainActivity.this, getSupportFragmentManager()).build();
	}
}
```	

You can add a listener if you want to be informed when the `InterstitialView` is dismissed and/or open by adding the following code:

```java
mInterstitialView.setOnInterstitialViewEventListener(new IOnInterstitialViewEventListener()
{
	@Override public void onDismissView()
	{
		// Will be called when the InterstitialView is closed
	}

	@Override public void onReadyToShow()
	{
		// Will be called when the InterstitialView is open
	}
});
```

###Using KIDOZ Button
You can add the ```KIDOZ button``` to your layout xml file or create a new instance programmatically.

 - 	Add ```KIDOZ button``` inside xml:
 ```xml
<com.kidoz.sdk.api.KidozButtonView
	android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/kidozBtn_view"
        android:layout_alignParentRight="true"/>
```


#Launching the Feed Interstitial View
The ```Interstitial View``` can be launched by clicking on a button or any other view with a onClick listener or depends on your own logics like when a game is stopped or anywhere else inside your app as long as your target class have a reference to the InterstitialView instance.
</br>
Simply launch the ```Interstitial View``` by calling the method showView() on the InterstitialView instance.
```java
Button openInterstitialViewButton = findViewById(R.id.OpenInterstitialViewButton);
openInterstitialViewButton.setOnClickListener(new OnClickListener()
{
	mInterstitialView.showView();
}
```







</br>For any question or assistance, please contact us at support@kidoz.net.
