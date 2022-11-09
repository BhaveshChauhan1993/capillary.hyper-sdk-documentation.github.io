## Track Behavioral events

Behavioral events helps in capturing customer activities such as registration, forgot password, and cart abandonment etc. The events resource lets you create Custom Events to track any other user interactions that are important for your business. Each Custom Event can further be defined by Event Attributes like price, quantity, category and so on.
This API can be used to log such events.

```kotlin
/**
* Track user behaviour as events with attributes.
* @param event_name [String] Event name
* @param customData (Optional)[String] The attribute map which needs to be set for the event
*/
fun pushEvent(
        event_name: String,
        attributes: Map<String, Any>
    )

```

Example 1: User need the track of Page/Activity open event.

```kotlin
hydraAPI.pushEvent("Page/Activity successfully opened")
```


