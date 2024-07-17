---
description: Various options impacting the plugin in its generality
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966825582216237126/unknown.png
coverY: 0
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

## Item configurations

### How do the Oraxen configurations work?

First, Oraxen has several folders and 3 of these are to configure things, the first one is `Oraxen/ghyphs/` and is to configure the Custom Font or Ghyph, then\
`Oraxen/items/` and is to configure and create your own configuration yaml and lastly `Oraxen/pack/` the target place where all the files like textures and models will be created,

## Pack

### Obfuscation

Obfuscation works by renaming all models, textures and files into random namespaces and paths\
This is to make it very hard to just download and use a ResourcePack.\
It comes with four modes, FILENAME, NAMESPACE, FULL & NONE\
\
There is also an option to cache the obfuscated pack. \
This makes it so unless there are changes, Oraxen will not reobfuscate the ResourcePack.\
This makes it so players do not have to redownload the ResourcePack every time your server starts.\


```yaml
Pack:
  obfuscation:
    type: FULL
    cache: true
```

**NONE** does no obfuscation on the ResourcePack

```makefile
📁ResourcePack
└── 📁assets
    └── 📁custom_namespace
        └── 📁models
             └── 📑custom_model.json
```

**FILENAME** only obfuscates individual filenames, but retains the original pack-structure

```makefile
📁ResourcePack
└── 📁assets
    └── 📁custom_namespace
        └── 📁models
             └── 📑02a61ae4-2457-4dfa-91af-9598cd52fd9e.json
```

**NAMESPACE** only obfuscates namespaces, but retains the original filepath otherwise

```makefile
📁ResourcePack
└── 📁assets
    └── 📁0d003f53-e176-4e74-a895-d392c82f50be
        └── 📁models
             └── 📑custom_model.json
```

**FULL** obfuscates the entire path

```
📁ResourcePack
└── 📁assets
    └── 📁0d003f53-e176-4e74-a895-d392c82f50be
        └── 📁models
             └── 📑02a61ae4-2457-4dfa-91af-9598cd52fd9e.json
```

### PackServer

The ResourcePack oraxen generates needs to be hosted somewhere before it can be sent to players.\
Oraxen has two built-in server-options, POLYMATH & SELFHOST

**POLYMATH** is Oraxens own remote server, same as in Oraxen 1.0.\
It is located in France and can therefore be slower depending on your server's location and players download speed\
\
SELFHOST is a locally hosted server on the machine and can therefore be faster if your players are closer to it. You will need to manually configure the IP-address to your servers.

```yaml
Pack:
  server:
    type: SELFHOST
      selfhost:
        public_address: 0.0.0.0   # Set to your server's IP
        port: 8082                # Set to a port you have opened on your server
      polymath:
        server: atlas.oraxen.com
        secret: oraxen
```

### Dispatch

This section is for handling when the pack should be sent to players.

```yaml
Pack:
  dispatch:
    # Sends the Resourcepack before the players loads into the server
    # Might cause issues with large packs due to long download/load times
    send_pre_join: true
    send_on_join: false
    send_on_reload: true    # Sends the pack to players after using reload-command
    delay: -1               # Delay before pack is sent, does not apply to PreJoin dispatches
    mandatory: true         # If declining the ResourcePack should kick the player
    prompt: "<#fa4943>Accept the pack to enjoy a full <b><gradient:#9055FF:#13E2DA>Oraxen</b><#fa4943>experience"
```

## Misc

### hide\_scoreboard\_numbers

This option lets you hide the red scoreboard numbers.\\

```yaml
  hide_scoreboard_numbers: true
```

**Before:**\
![](https://media.discordapp.net/attachments/758785982005903431/1043486669371887616/image.png)\
**After:**\
![](https://media.discordapp.net/attachments/758785982005903431/1043486615655432193/image.png)

### hide\_scoreboard\_background

This option lets you hide the scoreboard background.\\

```yaml
  hide_scoreboard_background: true
```

### reset\_recipes

```yaml
reset_recipes: true
```

This option can causes bug with other recipes plugins. If you notice bugs with a recipes plugin when reloading Oraxen, you can disable this option. If you do that, you will have to restart the server to refresh Oraxen recipes.

## Oraxen Inventory

```yaml
oraxen_inventory:
  main_menu_title: "<shift:-18><glyph:menu_items><shift:-193>"
  menu_rows: 6
  menu_layout:
    armors:
      slot: 1
      icon: emerald_chestplate
      title: "<main_menu_title><#362753><glyph:menu_items_overlay:colorable>"
    blocks:
      slot: 2
      icon: orax_ore
      title: "<main_menu_title><#EDCDEB><glyph:menu_items_overlay:colorable>"
    furniture:
      slot: 3
      icon: chair
      title: "<main_menu_title><#F2F2F2><glyph:menu_items_overlay:colorable>"
    flowers:
      slot: 4
      icon: dailily
      title: "<main_menu_title><#bf332c><glyph:menu_items_overlay:colorable>"
    hats:
      slot: 5
      icon: crown
      title: "<main_menu_title><#81B125><glyph:menu_items_overlay:colorable>"
    items:
      slot: 6
      icon: ruby
      title: "<main_menu_title><#DA2E45><glyph:menu_items_overlay:colorable>"
    mystical:
      slot: 7
      icon: legendary_hammer
      title: "<main_menu_title><#9AB2E4><glyph:menu_items_overlay:colorable>"
    plants:
      slot: 8
      icon: weed_leaf
      title: "<main_menu_title><#44C886><glyph:menu_items_overlay:colorable>"
    skins:
      slot: 9
      icon: wood_sword
      title: "<main_menu_title><#C48E40><glyph:menu_items_overlay:colorable>"
    tools:
      slot: 10
      icon: iron_serpe
      title: "<main_menu_title><#FFFFFF><glyph:menu_items_overlay:colorable>"
    weapons:
      slot: 11
      icon: energy_crystal_sword
      title: "<main_menu_title><#2FB6FF><glyph:menu_items_overlay:colorable>"
```

This allows you to configure an icon for every section of the Oraxen inventory. You can use Oraxen ids or Minecraft materials.
