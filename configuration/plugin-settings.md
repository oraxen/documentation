---
description: Various options impacting the plugin in its generality
---

# Plugin settings

## Plugin

```yaml
Plugin:
  commands:
    repair:
      oraxen_durability_only: false # will not repair vanilla items if set to true
```

The plugin related options. Here you can configure how some things work. Should the repair only repair Oraxen items with an oraxen durability?

## Pack

### Generation

```yaml
  generation:
    generate: true
    compression: BEST_COMPRESSION # see Deflater.class
    comment: "The content of this texture pack
     \nbelongs to the owner of the Oraxen
     \nplugin and any complete or partial
     \nuse must comply with the terms and
     \nconditions of Oraxen."
```

This section allows you to configure the generation of the pack. The compression is configured to make the smallest zip possible by default. You can change the comment which is basically a watermark inside your zip.

### Upload

```yaml
    enabled: true
    type: polymath #transfer.sh or polymath
    polymath:
      server: atlas.oraxen.com # you can also host your own polymath instance
```

Oraxen integrates with Polymath \(a custom web server written in Python especially to be compatible\). You can download the source code [here](https://github.com/Th0rgal/Polymath/) and host it yourself or use the provided instance \(atlas\). You can also integrate with [your own custom hosting service](../developers/custom-hosting-service.md).

### Dispatch

This section allows you to easily perform actions depending on the resource pack status of your players.

You can send message \(through a KICK, the chat, an actionbar or a title\) and specify a delay and a period \(between the different messages if you are using an actionbar or a title\).

```yaml
receive:
  enabled: true

  loaded:
    actions:
      message:
        enabled: true
        # KICK / CHAT / ACTION_BAR / TITLE
        type: ACTION_BAR
        # Delay before the first message to appear, this is in seconds
        delay: 0
        # You only need a period if you send multiple messages of type ACTION_BAR or TITLE
        period: -1
        # Click and Hover elements are only available by using the CHAT type
        messages:
          - "&a&lResourcePack successfully loaded!"

      # If you need to send commands
      commands:
        console: []
        player: []
        opped_player: []

  accepted:
    actions:
      message:
        enabled: true
        # KICK / CHAT / ACTION_BAR / TITLE
        type: TITLE
        # Delay before the first message to appear, this is in seconds
        delay: 0
        # You only need a period if you send multiple messages of type ACTION_BAR or TITLE
        period: 3
        # Click and Hover elements are only available by using the CHAT type
        messages:
          - "&a&lResourcePack accepted!"
          - "Thank you"
      # If you need to send commands
      commands:
        console: []
        player: []
        opped_player: []

  denied:
    actions:
      message:
        enabled: true
        # KICK / CHAT / ACTION_BAR / TITLE
        type: CHAT
        # Delay before the first message to appear, this is in seconds
        delay: 0
        # You can put any value here because this is a CHAT message
        period: -1
        # Click and Hover elements are only available by using the CHAT type
        messages:
          - "<red>You refused the ResourcePack, but you need it in order to see the new items. Please </red><click:run_command:/oraxen pack><hover:show_text:\"<green>Display more informations\"><green><bold>CLICK HERE</bold></hover></click> <red>or type <bold>/o pack"
      # If you need to send commands
      commands:
        console: []
        player: []
        opped_player: []

  failed_download:
    actions:
      message:
        enabled: true
        # KICK / CHAT / ACTION_BAR / TITLE
        type: CHAT
        # Delay before the first message to appear, this is in seconds
        delay: 0
        # You can put any value here because this is a CHAT message
        period: -1
        # Click and Hover elements are only available by using the CHAT type
        messages:
          - "<red>You failed to download the ResourcePack, but you need it in order to see the new items. Please </red><click:run_command:/oraxen pack getpack><hover:show_text:\"<red>/!\\ loading the resourcepack from the game can cause lags\"><red><bold>CLICK HERE</bold></hover></click> <red>to retry or type <bold>/o pack</bold> and download it from the internet"
      # If you need to send commands
      commands:
        console: []
        player: []
        opped_player: []
```

## ConfigTools

```yaml
  # Nice for production servers, automatically set model ID in settings so
  # that you can other items without destroying the others already created
  automatically_set_model_id: false
  enable_configs_updater: true
  error_item:
    material: PODZOL
    excludeFromInventory: false # set to true if you don't want to display it inside inventory
    injectID: false
```

The `automatically_set_model_id` option is really important. If you set it to true, Oraxen will automatically edit your configurations to add a custom\_model\_data field, that way if you add another item, it won't take the same model\_data than your previous item and this will avoid breaking already existing items. Please enable this option on a production server \(with players\). If you work on a test server and reset items everytime, it is not required.

## Misc

### reset\_recipes

```yaml
reset_recipes: true
```

This option can causes bug with other recipes plugins. If you notice bugs with a recipes plugin when reloading Oraxen, you can disable this option. If you do that, you will have to restart the server to refresh Oraxen recipes.

## GUI Inventory

```yaml
gui_inventory:
  armors: emerald_chestplate
  blocks: orax_ore
  guis: CHEST
  hats: crown
  items: ruby
  mobs: goblin_beetle
  mystical: legendary_hammer
  skins: wood_sword
  tools: iron_serpe
  weapons: energy_crystal_sword
```

This allows you to configure an icon for every section of the Oraxen inventory. You can use Oraxen ids or Minecraft materials.



