
# Runnables

Runnables enable you to run a task every x amount of game ticks.

### Registering a new runnable

Registering a runnable is very simple. See the example below:

```java
int id = Conduit.getRunnableManager().schedule(() -> {
    Conduit.getPlayerManager().broadcastMessage(new TextComponent("Hello, world!"), Util.NIL_UUID);
}, 20 /* change me to how ever many ticks you want in between iterations */)
```

Ensure that you store the ID of the task for cancelling later.

A single task will _never_ be running twice. If your runnable is running and the next iteration comes up, it will be skipped until it is no longer running.

### Cancelling a task

To cancel a previously scheduled task, see the example below:

```java
Conduit.getRunnableManager().cancelRunnable(id);
```
