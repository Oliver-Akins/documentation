
# Custom Level API

Conduit has a very featureful custom level API that allows you to customize every single aspect of your level.

### Creating a new level:

```java
// Create the basic data about how your level should be generated
LevelDataFactory data = LevelDataFactory.builder()
    .levelName("myWorld"); // This is the only required field.
    .largeBiomes(true)
    .generateBonusChest(true)
    .hasRaids(false)
    .build();

// Tell the server to generate the new world.
Conduit.getLevelManager().createLevel(data).ifPresent(newLevel -> {
    // New level was generated without issue!

    // For fun, now we'll teleport all the players on the server to it.
    BlockPos spawn = newLevel.getSharedSpawnPos();
    Conduit.getPlayerManager().getOnlinePlayers().forEach(player -> player.teleport(newLevel, spawn.getX(), spawn.getY(), spawn.getZ(), 0, 0));
});
```

### Getting an existing level

```java
Conduit.getLevelManager().getLevel("myWorldName").ifPresent(level -> {
    // Do something with the level
})
```
