
# Permissions

*Conduit's permission system is SEPARATE from the default Minecraft OP system.*

Permission "sections" are split up by the `.` character. For example, consider the following permissions exist:

```
myplugin.commands.admin
myplugin.commands.throw
myplugin.commands.admin.uberban
myplugin.actions.move
myplugin.actions.move.fast
```

Conduit supports granting permission sections, instead of each granular permission. This means you could grant a player the `myplugin.commands` and they would have access to all permission nodes under `commands`.

### Usage

Getting all permissions on a player: `ServerPlayer#getPermissionNodes`

For these examples, we'll assume you want to add or remove permissions on the player join event.

Adding a permission:

```java

@Listener
public void playerJoinEvent(PlayerEvents.PlayerJoinEvent event) {
    event.getPlayer().addPermission("myplugin.commands");
}

```

Removing a permission:

```java
@Listener
public void playerJoinEvent(PlayerEvents.PlayerJoinEvent event) {
    event.getPlayer().removePermission("myplugin.commands");
}
```
