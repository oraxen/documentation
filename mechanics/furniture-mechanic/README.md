---
description: How to add non cubic blocs to the game
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966828778028417125/unknown.png
coverY: 0
---

# Furniture Mechanic

## How does it work?

Oraxen uses invisible item frames to add non cubic blocks to the game. This avoids some lags causes by armorstands You can then activate a transparent block (barrier) on top to act as a hitbox.

![Example furniture](<../../.gitbook/assets/image (3).png>)

## Global configuration

This global configuration has to be used in order to define the hierarchy of between your multiple tool\_types. You can put the normal types + new types you just invented.

```yaml
furniture:
  tool_types:
    - WOODEN
    - STONE
    - IRON
    - GOLDEN
    - DIAMOND
    - NETHERITE
  enabled: true
```

## Example configuration per item

```yaml
table:
  displayname: "<gray>Table"
  material: DIAMOND
  Pack:
    generate_model: false
    model: default/table
  Mechanics:
    furniture:
      block_sounds:
        place_sound: block.stone.place
        break_sound: block.stone.break
        hit_sound: my.custom.hitsound     # Custom sound as defined in Oraxen/sound.yml
        step_sound: my.custom.stepsound   # Requires a sound-file in the Oraxen/pack-folder aswell
        fall_sound: my.custom.fallsound
        volume: 0.8                      # Default: 0.8
        pitch: 0.8                       # Default: 0.8
      rotation: NONE
      facing: UP
      barrier: true
      drop: # useless if you are not using a barrier
        silktouch: false
        loots:
          - { oraxen_item: table, probability: 1.0 }
```
## Custom Sounds
Furniture, like custom blocks, can have custom sounds.  
Currently the options are place/break/hit/step/fall.
```yaml
Mechanics:
  furniture:
    block_sounds:
      place_sound: block.stone.place
      break_sound: block.stone.break
      hit_sound: my.custom.hitsound     # Custom sound as defined in Oraxen/sound.yml
      step_sound: my.custom.stepsound   # Requires a sound-file in the Oraxen/pack-folder aswell
      fall_sound: my.custom.fallsound
```
All the volume and pitch values are set to be what Minecraft uses for blocks normally.\
If you want to change the volume or pitch, you can do so by using the format below.\
Keep in mind these two formats are compatible with eachother.\
We recommend just use the default one, but the option is there if you want to change it.
```yaml
Mechanics:
  furniture:
    block_sounds:
      place:
        sound: block.stone.place
        volume: 1.0
        pitch: 0.2
      break_sound: block.stone.break
      hit_sound: my.custom.hitsound     # Custom sound as defined in Oraxen/sound.yml
      step_sound: my.custom.stepsound   # Requires a sound-file in the Oraxen/pack-folder aswell
      fall_sound: my.custom.fallsound
```

## Jukebox
Lets this furniture accept music discs and custom music discs which will be played.\
You can tweak the `volume` and `pitch` of the music from the jukebox.\
There is also a `permission` field, which can be used if you only want certain players to be able to play music from the jukebox.\
By default permission is blank, which means anyone can play music from the jukebox.
```yaml
Mechanics:
  furniture:
    jukebox:
      volume: 1.0
      pitch: 1.0
      permission: "oraxen.jukebox.play"
```

## Barriers

Barriers are invisible blocks placed with your furniture so that it has a realistic hitbox. You can place a single one or a list relative to the position of the player who places them.

### Single barrier:

```yaml
barrier: true
```

### Multiple barriers:

```yaml
barriers:
    - { x: 0, y: 0, z: 0 }
    - { x: 0, y: 0, z: 1 }
    - { x: 0, y: 0, z: 2 }
    - { x: 1, y: 0, z: 0 }
    - { x: 1, y: 0, z: 1 }
    - { x: 1, y: 0, z: 2 }
```

# Seats
<b>Seats are only available when barriers are enabled.</b>  
Currently it will also spawn a seat for every barrier, if there is multiple ones.  
You can alter the height-offset of seats with the following configuration:  

```yaml
seat: { height: 0.5 }
```
You can also adjust the rotation if desired by adding a yaw section.  
Keep in mind it is recommended to leave this off
```yaml
seat: { height: -0.5, yaw: 90 }
```

# Limited placing
You can customize what blocks a custom block/furniture can be placed on with `limited_placing` subsection.
You can use the `roof`, `floor` and `wall` options to dictate where a block can be placed. By default, all are set to `true`.\
The `type` specifies if it should only be allowed on or denied on specific blocks.  
If type is `ALLOW` the block can only be placed on the given blocks.  
If the type is `DENY` can be placed on all blocks not matching the given blocks.
```yaml
chair:
  Mechanics:
    furniture:
      limited_placing:
        roof: false
        floor: true
        wall: false
        type: ALLOW
        block_types:
          - GRASS_BLOCK
          - DIRT
        block_tags:
          - base_stone_nether
        oraxen_blocks:
          - chair
          - ruby_ore
```

The `block_tags` can be found at [this page](https://minecraft.fandom.com/wiki/Tag#Block_tags). Useful if you want to allow/deny a group of blocks.  
The `block_types` are materials. Useful if you want to allow/deny a specific list block.  
The `oraxen_blocks` are blocks defined in the oraxen configuration.  
This allows all custom blocks and furniture in here, but furniture requires a barrier-hitbox.

# Storage
This is a sub-mechanic for furniture and noteblock mechanics, that let you make a custom storage container.\
Essentially a chest, closet or whatever you might want.

There's a few different types: _STORAGE, PERSONAL, ENDERCHEST & DISPOSAL_.\
**STORAGE** is similar to a normal chest. Anyone can open it and view the content of it.\
**PERSONAL** is essentially a custom enderchest, letting you edit the row-count and so on.\
**ENDERCHEST** is literally just the enderchest inventory, but letting you make a custom block/furniture to access it.\
**DISPOSAL** is a custom trashcan, letting you throw items in it, and they will be deleted when closed.\

```yaml
Mechanics:
  furniture:
    barrier: true
    storage:
      type: STORAGE
      rows: 5                             # Default: 6
      title: "<red>My Storage"            # Default: "Storage"
      open_sound: entity.shulker.open     # Default: entity.chest.open
      close_sound: entity.shulker.close   # Default: entity.chest.close
```
{% hint style="info" %}
This mechanic requires a barrier(s) if used with furniture!
{% endhint %}

## Light

You can configure your furniture so it produces light. To do so you need to install this plugin: [LightAPI](https://www.spigotmc.org/resources/lightapi.4510/).

This allows you to use a new option: light. This option corresponds to light intensity and must be between 1 and 15.

```yaml
Mechanics:
  furniture:
    facing: UP
    barrier: true
    light: 5
    drop: # useless if you are not using a barrier
      silktouch: false
      loots:
        - { oraxen_item: table, probability: 1.0 }
```

### Video Tutorial

{% embed url="https://www.youtube.com/watch?t=329s&v=ch4Fufti5Rg" %}
