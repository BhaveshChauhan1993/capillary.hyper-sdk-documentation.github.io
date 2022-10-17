## Track Behavioral events

Behavioral events help capture customer activities such as registration, forgot password, and cart abandonment. The events resource lets you create Custom Events to track any other user interactions that are curcial for your business. Each Custom Event can further be defined by Event Attributes like price, quantity, category and so on.
This API can be used to log such events.

```
fun pushEvent(
        event_name: String,
        attributes: Map<String, Any>
    )

```
