# Hydra SDK

This documentation covers the steps to integrate your mobile apps with Hydra Sdk. Installing the Hydra SDK will provide you with basic analytics functionality to engage your users. 

# Installation

The easiest way to use Hydra sdk in your Android project is with [Maven](https://maven.apache.org/). Hydra Android SDK is hosted on `jcenter` Maven repository.

Add `maven` in repositories of your project in the `project/build.gradle` file.

```kotlin
 repositories {
     ...
     maven {
         url "https://maven.pkg.github.com/Capillary/hydra-sdk-android-maven"
         credentials {
             username ['username']
             password ['token']
         }
     }
 }
 ```   
 Add dependencies of **Hydra Sdk** along with **AndroidX Libraries** in the `app/build.gradle` file.
 
 ```kotlin
 dependencies {
     // AndroidX libraries
     implementation("androidx.core:core:xxx")
     implementation("androidx.appcompat:appcompat:xxx")
     implementation("androidx.lifecycle:lifecycle-process:xxx")
     
     // Hydra Sdk
     implementation("com.capillary:hydra-android-sdk:xxx")
 }
 ```
 
# Initialization

You need to create an instance of the sdk for each application, this api needs to be called in the onCreate() of the application class with the [Hydra Config](README.md#hydra-config)

```kotlin
 fun instanceWithConfig(
            context: Context, config: HydraConfig
        ): HydraAPI
```
This api will create a unique instance of the HydraApi created by using the above api can then be retrieved in your code 

# Hydra Config
For initializing the sdk we need to provide some configuration represented by HydraConfig in the sdk. Below are the possible parameters which are accepted by the sdk. User need to provide accountId, accountSecret, and orgId for initialization otherwise sdk will throw an exception, apart from these all the other parameter are optional. 

```kotlin
       var accountId: String,
       var accountSecret: String,
       var orgID: String,
       var baseURL: String?,
       var sslPublicKey: String?,
       var country: String?,
       var city: String?,
       var countryCode: String?,
       var captureViewPortDetails: Boolean,
       var isDisableAppLaunchedEvent: Boolean,
       var debugLevel: Int = LogType.INFO.intValue(),
       var fcmSenderId: String? = null,
```

Once you have your accountId, accountSecret, and orgId with you, sdk initialization block can be added in the onCreate callback of your Application class as shown below.
```kotlin

/**
* Hydra Config requires accountId, accountSecret, orgID as a compulsory fields else Exception will be thrown.
* @param accountId [String] Account ID of partner
* @param accountSecret [String] Account Secret of partner
* @param orgID [String] Organization ID of partner

* @param .debugLevel (Optional)[LogType] Logging Config i.e. OFF(-1),INFO(0),DEBUG(1),VERBOSE(2).
* @param .captureViewPortDetails (Optional)[Boolean] Capture ViewPort information.
* @param .country (Optional)[String] Country name
* @param .city (Optional)[String] City name
* @param .countryCode (Optional)[String] Country Code value
* @param .baseURL (Optional)[String] Base URL of region 
* @param .sslPublicKey (Optional)[String] Valid SSL Public Key of URL
*/
  
val hydraConfig = HydraConfig.Builder(
            applicationContext,
            accountId = "YOUR_ACCOUNT_ID",
            accountSecret = "YOUR_ACCOUNT_SECRET",
            orgID = "YOUR_ORG_ID"
        )
            .debugLevel(LogType.VERBOSE) 
            .captureViewPortDetails(true)
            .country("India")
            .city("Punjab")
            .countryCode("91")
            .baseURL("https://hydratest.crm-nightly-new.cc.capillarytech.com/")
            .sslPublicKey("YOUR_SSL_PUBLIC_KEY")   // for ssl pinning
            .build()
        HydraAPI.instanceWithConfig(applicationContext, hydraConfig)
        
  ```

# Tracking Events
You can record events with Hydra to learn more about your app’s usage patterns and segment your users by their actions.
Events track what individual actions users perform in your app or website. Some examples of events include a user signing in, launching an app, viewing a product, etc. With this SDK you can track users in two ways.

1. [Track User Events](track-user-events.md#track-user-events) In these events all the user specific information like username,firstname,lastname,email,mobile, and other custom information along with system information can be passed.These information can be used to run campaign based on user segregation on different levels.
For Example:- Spreading welcome messages on their emails or offering different offers based on user age,gender etc.
2. [Track Behavioral Events](track-behavioral-events.md#track-behavioral-events) These events can be used to track user actions througout application.These events are Valid only if user is SignIn or SignUp to Hydra SDK.Events are Invalid if they are called after SignOut. 
In order to track these events,User has to pass Event name (NotNull or NonEmpty) and Attributes (Optional). 
