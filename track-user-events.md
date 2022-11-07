# Track User Events

The SDK provides four event tracking APIs to log events for reporting User action events. It allows you to identify visitors, track events, dynamically create events and keep an account of the actions performed by the users, along with any properties that describe the action.

1. [Sign In](README.md#sign-in) 
2. [Sign Up](README.md#sign-up) 
3. [User Update](README.md#user-update) 
4. [Sign Out](README.md#sign-out) 

There should be a unique id associated with each user whenever user signs in or signs up in the app. Sdk designates this identifier as cuid, it is strongly recommend providing this identifier as it will allow you to track your users across devices and platforms, improving the quality of your behavioral and demographic data.


## Sign In

### Android
Reporting a Sign In event requires **cuid** to be provided. Other basic information are optional to provide in this api. You can also add any custom data to log any additional attributes in the form of a Map with this api.
```kotlin
/**
* Track User Sign in event
* @param cuid  customer id can be either of phone/email/externalId
* @param firstName User first Name
* @param lastName User Last Name
* @param email Email address of the User
* @param phone User mobile number
* @param customData The attribute map which needs to be set for the user
*/
fun pushUserSignIn(
        cuid: String,
        firstName: String? = null,
        lastName: String? = null,
        email: String? = null,
        phone: String? = null,
        customData: Map<String, Any>? = null)

```

## Sign Up

### Android
To report a User Sign Up event **cuid** with other basic form info needs to be provided. You can also add any custom data to log any additional attributes in the form of a Map with this api.

```kotlin
/**
* Track User Signup event
* @param cuid  customer id can be either of phone/email/externalId
* @param firstName User first Name
* @param lastName User Last Name
* @param email Email address of the User
* @param phone User mobile number
* @param customData The attribute map which needs to be set for the user
*/
fun pushUserSignup(
        cuid: String,
        firstName: String,
        lastName: String,
        email: String,
        phone: String,
        customData: Map<String, Any>?
    )

```

## User Update
### Android
User update event is similar to the sign in event where **cuid** is required to identify the user. You can add other custom data to update in the form of a Map with this api.

```
/**kotlin
* Track User update event
* @param cuid  customer id can be either of phone/email/externalId
* @param firstName User first Name
* @param lastName User Last Name
* @param email Email address of the User
* @param phone User mobile number
* @param customData The attribute map which needs to be set for the user
*/
 fun pushUserUpdate(
        cuid: String,
        firstName: String? = null,
        lastName: String? = null,
        email: String? = null,
        phone: String? = null,
        customData: Map<String, Any>? = null
    ) 

```


## Sign Out

### Android
Sign out event can be logged by providing just the **cuid**. This will erase all the other basic info like firstName, mobile, etc. provided earlier in the session. 

```kotlin
/**
* Track User Sign out event
* @param cuid  customer id can be either of phone/email/externalId
*/
fun pushUserSignOut(
        cuid: String
    )

```
