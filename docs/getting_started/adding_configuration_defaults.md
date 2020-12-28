
# Adding a default configuration for your plugin

Sometimes you will want your plugin to assume a value for your configuration, this allows the people using your plugin to not always worry about the config setup, and allows you to know that those values will always be set.


## Defaults in the configuration class

One method to set a configuration default is by assigning a value to the property in the configuration class. Below is the class from the "(Adding a Configuration File)[adding_a_configuration_file.md]" guide without the default value.

```java
@ConfigFile(name = "first", type = "json")
public class MyConfiguration extends Configuration {
	@Getter private String joinMesssage;
}
```

Adding the default value is as simple as chaning:
```java
@Getter private String joinMesssage;
```
to be:
```java
@Getter private String joinMesssage = "Hello, World!";
```
From there Conduit will assume the value assigned as the default.


## Defaults in a configuration file

You can create a default configuration file in the `resources` folder of your plugin's JAR file with the same structure as your configuration class. The default config file for the above example class above would look like:

```json
{
	"joinMessage": "Hello, World!"
}
```

Conduit will copy this file from the JAR to the `plugins/<pluginName>` of the server. From there Conduit will read the file as normal and if the user changes the value it will adjust it as desired.