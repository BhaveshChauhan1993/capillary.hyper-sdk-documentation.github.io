## Track Behavioral events

Behavioral events help capture customer activities such as registration, forgot password, and cart abandonment. There are standard events that are predefined with name, id, and attributes. The events resource lets you create custom events and map event fields.
This API can be used to log such events.

```
fun pushEvent(
        event_name: String,
        attributes: Map<String, Any>
    )

```
