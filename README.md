This SDK is designed for integrating Adcash with AdMob Mediation on Android to maximize fill rate and revenue.  

It's a simple 2-step integration process.

## Integration Guide

> Assuming integration is already done with AdMob SDK, if not please follow AdMob Integration guideline 

**Prerequisite:** Android Studio 1.0 or higher 

### 1. Download the Adcash SDK

The Adcash SDK is available via:

#### 1. Integration with JCenter repository (Recommended)

The Adcash SDK is uploaded to **JCenter** for your convenience. So you should setup your project to sync to the JCenter repository to allow it to download the Adcash SDK from there.  
Then simply include the **Adcash SDK** to your project dependencies. Make sure to also include the two library dependencies used and needed by the Adcash SDK - **Google Play Services** and **Android Support Library v4**.  
Add the following lines to your module level `build.gradle` file:

```xml
repositories {
    jcenter()
}

dependencies {
    // Integrate Adcash SDK:
    compile 'com.adcash:adcash-admob-adapter:2.2.1'

    // Required by Adcash SDK:
    compile 'com.android.support:support-v4:24.2.0'
    compile 'com.google.android.gms:play-services:9.4.0'
}
```

![alt tag](http://developer.adca.sh/wp-content/uploads/2016/09/AndroidSDK-AdMob-Adapter-Gradle-Script.png)
> If you have **jcenter** repository  in your project level **build.gradle** for all modules, then you don't need to add it again in module level **build.gradle**

You may see a warning message across the top of the Android Studio window indicating that Gradle needs to perform a Gradle sync.    
If that is the case, click **Sync Now** and Gradle will refresh your project libraries to include the dependencies you just added. You should now have successfully integrated the Adcash SDK into your project.  
At last, go to **Finalize Integration** to make your newly integrated Adcash SDK ready to work with.

#### 2. Integration with local file
Download the Adcash SDK [here](http://developer.adca.sh/wp-content/uploads/2016/09/admob-adapter.zip).
Add Adcash SDK into project by putting it in **'libs'** module.  If you don't have 'libs' folder in your project module then create one (Example: ... MyApplication/app/libs/)

Open the build.gradle of your app and add the following code lines:

```xml
repositories {
    flatDir {
       dirs 'libs'
    }
}

dependencies {
    // Integrate Adcash SDK:
    compile(name: 'adcash-admob-adapter', ext: 'aar')

    // Required by Adcash SDK:
    compile 'com.android.support:support-v4:24.2.0'
    compile 'com.google.android.gms:play-services-ads:9.2.0'
}
```
![alt tag](http://developer.adca.sh/wp-content/uploads/2016/09/AndroidSDK-AdMob-Adapter-Gradle-Script-local.png)

### 2. Update AndroidManifest.xml
Add **INTERNET** and **ACCESS_NETWORK_STATE** permissions in your **&lt;manifest&gt;**:
```xml
<uses-permission android:name="android.permission.INTERNET"/>
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
```

Add Adcash activity in your **&lt;application&gt;**:
```xml
<activity android:name="com.adcash.mobileads.ui.AdcashActivity"
    android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize" 
    android:theme="@android:style/Theme.Translucent"
    android:hardwareAccelerated="true" />
```
![alt tag](http://developer.adca.sh/wp-content/uploads/2016/09/AndroidSDK-AdMob-Adapter-Manifest-File.png)

### 2 Configure Adcash Custom Event on AdMob Mediation Portal

##### 2.1 Select App & Add New Network
On AdMob Mediation Portal, click on **Monetize tab** then select one of your app from left panel that you want to monetize. 

On Application page, select one of your **ad unit** (Adcash AdMob Android Adaptor currently supports Banner and Interstitial ad format) and click on **Mediation** for adding new ad network.
<![alt tag](http://i2.wp.com/developer.adca.sh/wp-content/uploads/2016/08/ScreenShot2.png)

On Mediation page, click on **new ad network** and it open new window for configuring it.
![alt tag](http://i1.wp.com/developer.adca.sh/wp-content/uploads/2016/08/ScreenShot3.png)

##### 2.2 Add Adcash Custom Ad Network
Click on **Custom Event** and it will open window for filling out information. 
![alt tag](http://i0.wp.com/developer.adca.sh/wp-content/uploads/2016/08/ScreenShot4.png)

Custom Event Information from:  
>	**Class Name**  
   	_For Banner:_ com.adcash.mobileads.admobadapter.AdcashAdmobBanner  
	_For Interstitial:_ com.adcash.mobileads.admobadapter.AdcashAdmobInterstitial  
>	**Label:** Adcash  
>	**Parameter:** Enter Zone ID from Adcash Publisher Panel  
![alt tag](http://i0.wp.com/developer.adca.sh/wp-content/uploads/2016/08/ScreenShot5.png)

## Release App
Now Adcash is successfully has integrated with AdMob Mediation platform and you can release out the app in PlayStore. Please note changes made in AdMob Portal take couple of hours to reflect.

## Support
If you need any help or assistance you can contact us by sending email to mobile@adcash.com.