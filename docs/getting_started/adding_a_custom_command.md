
# Adding your first custom command

Conduit leverages Minecraft's Brigadier system for command management making it very simple to create commands and parse arguments.


### Creating your command

Create a new class called `MyFirstCommand` and enter the following into it:

```java
public class MyFirstCommand extends BaseCommand {

    @Override
    public LiteralArgumentBuilder<CommandSourceStack> getCommand() {
        return Commands.literal("myfirstcommand").executes(ctx -> ctx.getSource().sendSuccess("Hello, world!", false));
    }
}
```

The command context that is provided in the arguments of `executes` contains all the information about both the command arguments, and the command sender.

### Using the command context

TODO

### Accepting arguments on the command

TODO

### Registering the command

To register the command, simply add this to your plugin's `onEnable` function:

```java
registerCommand(new MyFirstCommand())
```
