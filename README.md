# Hydra SDK

This documentation covers the steps to integrate your mobile apps with Hydra Sdk. Installing the Hydra SDK will provide you with basic analytics functionality to engage your users. 

# SDK Initialization

You need to create an instance of the sdk for each application, this api needs to be called in the onCreate() of the application class with the [Hydra Config](README.md#hydra-config)

```
 fun instanceWithConfig(
            context: Context, config: HydraConfig
        ): HydraAPI
```
This api will create a unique instance of the HydraApi created by using the above api can then be retrieved in your code 

# Hydra Config
For initializing the sdk we need to provide some configuration represented by HydraConfig in the sdk. Below are the possible parameters which are accepted by the sdk. User need to provide accountId, accountSecret, and orgId for initialization otherwise sdk will throw an exception, apart from these all the other parameter are optional. 

```
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
```
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

1. [Track User Events](track-user-events.md#track-user-events) These are the specific traits of a user such as an email, username, mobile, gender and so on. User Attributes helps target users based on these attributes across devices or installs or to personalize the messages.
2. [Track Behavioral Events](track-behavioral-events.md#track-behavioral-events) This will help you record various actions performed by the users. You can track an event using this api with the event name and its characteristics (attributes/properties).
