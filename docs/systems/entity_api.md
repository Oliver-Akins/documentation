
# Entity Factory

### Creating a new Entity

```java
ServerLevel level = Conduit.getLevelManager().getLevel("world").get();  // Assuming the world exists
Optional<Entity> entity = EntityFactory.builder()
    .name("My zombie")
    .type(EntityType.ZOMBIE)
    .level(level)
    .position(new BlockPos(0, 60, 0))
    .build().spawn();

entity.ifPresent(e -> Conduit.getPlayerManager().broadcastMessage(entity.getName().getString()));
```
