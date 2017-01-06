Adcash AdMob Mediation Adapter is designed for integrating Adcash with AdMob Mediation on Android to maximize fill rate and revenue.  

It's a simple 2-step integration process.

## Integration Guide

> Assuming integration is already done with AdMob SDK, if not please follow [AdMob Integration guideline](https://firebase.google.com/docs/admob/android/quick-start) 

### 1. Integrate Adcash SDK

**Prerequisite:**

* **ZONE ID(s)**. You create at [Adcash website](https://www.adcash.com/console/scripts.php).
* Android Studio 1.0 or higher. Instructions to [install Android Studio](https://developer.android.com/studio/install.html).
* Android API level 9 or higher
* Integrated AdMob 5.0.89 or higher

#### 1. Add Dependencies

### JCenter repository

```groovy
repositories {
    jcenter()
}

dependencies {
    // Integrate Adcash SDK:
    compile 'com.adcash:adcash-admob-adapter:2.2.2'

    // Required by Adcash SDK:
    compile 'com.android.support:support-v4:24.2.0'
    compile 'com.google.firebase:firebase-ads:9.4.0'
}
```

![alt tag](http://developer.adca.sh/wp-content/uploads/2016/09/AndroidSDK-AdMob-Adapter-Gradle-Script.png)


Click **Sync Now** or request Gradle sync yourself if you have not been promoted automatically. Wait till Gradle finishes.

> If you have **jcenter** repository  in your project level **build.gradle** for all modules, then you don't need to add it again in module level **build.gradle**

### (Optional) Local library file
If you prefer to use local file instead of Jcenter repository, you can also do it.  

Download the Adcash SDK [here](https://github.com/adcash/Adcash-AdMob-Adapter-Android/archive/master.zip).
Add Adcash SDK into project by putting it in **'libs'** module.  If you don't have 'libs' folder in your project module then create one (Example: ... MyApplication/app/libs/)

```groovy
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


Click **Sync Now** or request Gradle sync yourself if you have not been promoted automatically. Wait till Gradle finishes.

### (Optional) Proguard settings

If you want to enable **Proguard** in your project, add following line to your  `proguard.cfg` file:

> -keep class com.adcash.mobileads.** { *; }  

#### 2. Update Manifest

At this point you have added all necessary dependencies to your project and need small modifications to your module `AndroidManifest.xml` file to finish with the integration. 

1. Add the following `<uses-permission>` tags: 
    * `INTERNET` - required to allow the Adcash SDK to make ad requests.
    * `ACCESS_NETWORK_STATE` - used to check the Network connection availability.  

```xml
    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
```


2. Add **AdcashActivity** for full screen ads to work (interstitial and rewarded video)  

```xml
    <activity
        android:name="com.adcash.mobileads.ui.AdcashActivity"
        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|uiMode|screenSize|smallestScreenSize"
        android:hardwareAccelerated="true"
        android:theme="@android:style/Theme.Translucent" />
```

![alt tag](http://developer.adca.sh/wp-content/uploads/2016/09/AndroidSDK-AdMob-Adapter-Manifest-File.png)


### 2 Configure Adcash Custom Event on AdMob Mediation Portal

##### 2.1 Select App & Add New Network
1. On AdMob Mediation Portal, click on **Monetize tab** then select one of your app from left panel that you want to monetize. 

2. On Application page, select one of your **ad unit** (Adcash AdMob Android Adaptor currently supports Banner and Interstitial ad format) and click on **Mediation** for adding new ad network.
![alt tag](http://i2.wp.com/developer.adca.sh/wp-content/uploads/2016/08/ScreenShot2.png)

3. On Mediation page, click on **new ad network** and it open new window for configuring it.
![alt tag](http://i1.wp.com/developer.adca.sh/wp-content/uploads/2016/08/ScreenShot3.png)

##### 2.2 Add Adcash Custom Ad Network
Click on **Custom Event** and it will open window for filling out information.
![alt tag](http://i0.wp.com/developer.adca.sh/wp-content/uploads/2016/08/ScreenShot4.png)

Custom Event Information from:  
>	**Class Name**  
   	_For Banner:_ com.adcash.mobileads.admobadapter.AdcashAdmobBanner  
	_For Interstitial:_ com.adcash.mobileads.admobadapter.AdcashAdmobInterstitial  
	_For Rewarded Video:_ com.adcash.mobileads.admobadapter.AdcashAdmobRewardedVideo
>	**Label:** Adcash  
>	**Parameter:** Enter Zone ID from Adcash Publisher Panel  
![alt tag](http://i0.wp.com/developer.adca.sh/wp-content/uploads/2016/08/ScreenShot5.png)

## Release App
Now Adcash is successfully has integrated with AdMob Mediation platform and you can release out the app in PlayStore. Please note changes made in AdMob Mediation Portal take couple of hours to reflect.

## Support
If you need any help or assistance you can contact us by sending email to **mobile@adcash.com**.