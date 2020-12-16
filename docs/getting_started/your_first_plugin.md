
# Creating your first Conduit Plugin

Conduit plugins have a very simple structure to the main plugin class.

For this guide, we're going to assume your plugin is called `MyPlugin`.

Create a new class called MyPlugin and enter this code:

```java
@PluginMeta(name = "MyPlugin", author = "MyNameHere", description = "What my plugin does", version = "0.0.1")
public class MyPlugin extends Plugin {

    @Override
    public void onEnable() {
        Conduit.getLogger().info("Wow we're doing things!");
    }

    @Override
    public void onDisable() {
        Conduit.getLogger().info("Wow we're not doing things!");
    }
}
```

All plugins *MUST* be annotated with `@PluginMeta`, and extend `Plugin`. This tells Conduit that your plugin should be actually be loaded in.

...And that's it! Move your compiled JAR file into your plugins folder within your server. Once you start your server you'll see the plugin being loaded, and your logger messages on enable and disable.
