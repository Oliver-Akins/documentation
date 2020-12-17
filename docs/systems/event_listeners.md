
# Event Listeners

Conduit has a very large amount of event listeners that are available to you as a plugin developer.

If you would like to see a complete list see the following classes:

 - `PlayerEvents`
 - `WorldEvents`
 - `EntityEvents`
 - `ServerEvents`

### Adding an event listener

To listen to an event, an event listener must exist and be registered to your plugin. Your event listener function can have any name, and the first and only parameter must be the event you are listening for.

Then, add an `@Listener` annotation to the method, as shown below:

```java
@Listener
public void onPlayerJoin(PlayerEvents.PlayerJoinEvent event) {
    event.getPlayer().sendMessage(new TextComponent("Welcome to the server!"));
}
```

The event system does also support increasing the priority of your event handler, which will make it run earlier in the queue. The higher the priority, the sooner your handler will run.

Example:

```java
@Listener(priority = 999)  // I want to be first!
public void onPlayerJoin(PlayerEvents.PlayerJoinEvent event) {
    event.getPlayer().sendMessage(new TextComponent("Welcome to the server!"));
}
```

### Registering an event listener

In your plugin's `onEnable` function, simply add:

```java
@Override
public void onEnable() {
    registerListeners(new MyListener());
}
```

### Creating custom events

To create a custom event, simply create a new class that extends one of the following event types:

 - `EventType`
 - `Cancellable`

Once again, we recommend the use of Lombok here. See the getting started guide to learn more.

Sample event class:

```java

public class MyCustomEventType extends EventType {
    private ServerPlayer player;
    // other various fields relating to the event
}
```

This event can then be dispatched with the following snippet:

```java
Conduit.getEventManager().dispatchEvent(new MyCustomEventType(thePlayer));
```
