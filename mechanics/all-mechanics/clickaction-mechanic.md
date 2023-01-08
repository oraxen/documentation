---
description: >-
  Run commands, play sounds, or send messages when a player clicks a block or
  furniture.
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966825489098489856/unknown.png
coverY: 0
---

# clickAction Mechanic

### Information

The `clickAction` mechanic allows you to run commands, play sounds, or send messages when a player clicks on a furniture or a block.

### Configuration

To get started, create a basic [Block](../block-mechanic/) or [Furniture](../furniture-mechanic/).

Next, under the mechanics section, you can add the default clickAction mechanic under any\
noteblock-mechanic, furniture-mechanic or stringblock-mechanic item.

```yaml
Mechanics:      
  noteblock/furniture/stringblock:
    clickActions:
      - conditions:
          - '#player.hasPermission("test.permission")'
        actions:
          - '[console] say <player> hello <player>!'
```

With this setup, players will only trigger the console command `say hello <player>` action if they have the permission `test.permission`.

If you are not using conditions, you need to place brackets where they would be:

```yaml
Mechanics:
  noteblock/furniture/stringblock:
    clickActions:
      - conditions: []
        actions:
          - '[console] say <player> hello <player>!'
```

{% hint style="danger" %}
This mechanic does not support furniture with no hitbox.
{% endhint %}

### Conditions

Conditions are VERY configurable. You can use any of the "get" methods for Player or Server. See the Spigot Javadocs for all methods.

{% embed url="https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/Player.html" %}

{% embed url="https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Server.html" %}
TIP! Click "CTRL + F" and search "get" to find valid methods.
{% endembed %}

Additionally, the Spring Documentation is a good resource for understanding how to use condition expressions.

{% embed url="https://docs.spring.io/spring-framework/docs/3.0.x/reference/expressions.html" %}

#### Condition Examples

`#server.getOnlinePlayers().size() > 10`

`#server.getAllowEnd()`

`#server.getDefaultGameMode()`

`#player.world.name == 'world'`

`#player.hasPermission("test.permission")`

`#player.gamemode.name() == 'ADVENTURE'`

### Actions

`[console] <command>`

`[player] <command>`

`[message] <message>`

`[actionbar] <message>`

`{source=SOURCE volume=VOLUME pitch=PITCH} [sound] <sound name>`

#### Action Examples

`[console] say hello`

`[player] say hello`

`[message] <blue>Hello!`

`[actionbar] <gray>Hello from the actionbar!`

`{source=AMBIENT volume=0.1 pitch=1} [sound] minecraft:block.shulker_box.close`



