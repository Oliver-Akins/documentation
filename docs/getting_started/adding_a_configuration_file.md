
# Adding a configuration file to your plugin

You may want to add some settings to your plugin. The best way to do this is through a configuration file. This guide will show you how to add a basic configuration file to your plugin.

### Creating the configuration file

Create a new class called `MyConfiguration` that extends `Configuration` and add the `@ConfigFile` decorator to it:

```java
@ConfigFile(name = "first", type = "json")
public class MyConfiguration extends Configuration {
}
```

This will now generate an empty configuration file. To add fields to your config, we recommend using Lombok's `@Getter` annotation. Click [here](https://projectlombok.org/) to learn more about Lombok.

For example, if you wanted a configurable join message you could add the following to your configuration file:
```java
@Getter private String joinMesssage;
```

And just like that, Conduit will automatically handle the serialization and deserialization to and from your config file.

### Registering the configuration file

In your main plugin file, add the following to your PluginMeta decorator in you plugin's main class:

```java
@PluginMeta(name = "MyPlugin", author = "MyNameHere", description = "What my plugin does", version = "0.0.1", config = MyConfiguration.class)
public class MyPlugin extends Plugin {
    // ...snip...
}
```

The `name` you provide will be the name of the file in the plugin's config folder.

The type is the extension / file type of the configuration. At this time the support file types are:

 - `json`

The `defaultFile` is the file that is packaged with your plugin (generally in your `resources` folder) to be copied as the default config if the config does not already exist.

### Accessing the configuration

To access the configuration file at a later time, follow the guide below:

```java
// ...snip...

@Override
public void onEnable() {
    Optional<MyConfiguration> config = this.getConfig();
    config.ifPresent(cfg -> Conduit.getLogger().info(cfg.getJoinMessage()));
}

// ...snip...
```
