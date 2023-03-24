---
description: How to add your own blocks to the game
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966827878706708560/unknown.png
coverY: 0
---

# NoteBlock Mechanic

## How to create a simple block?

### Parent Models

The oraxen item root configuration is the same as for any item (you can use any material like a diamond for example) and set a displayname, etc.\
For the pack section you can use your own model or generated one.\
To generate a block model just specify the parent model your block should use.\
Supported parent_models for block are:\
`block/cube_all`, `block/cross`, `block/orientable`, `block/orientable_vertical` and `block/cube_column`.

```yaml
my_block:
  displayname: "&My block"
  material: DIAMOND
  Pack:
    generate_model: true
    parent_model: "block/cube_all"
    textures:
      - my_block_texture.png
```
Each of these parent models take a different amount of textures.\
`block/cube_all` takes 1 texture, `block/cube_column` takes 2, `block/cross` takes 1, `block/orientable` takes 3 and `block/orientable_vertical` takes 2.\
For example, if you want to make a log block using the Directional Block mechanic, you should use `block/cube_column`.

### Block Mechanic configuration

To use this mechanic you need to tell to oraxen which model to use (to use the generated one, just put the name id of your item). You then need to use custom\_variation which is not already used by another block (since by default 1 is used by caveblock, you can for example use 2). This example drop configurations allows you to get the drop when you mine it with a stone pickaxe.

```yaml
Mechanics:
  noteblock:
    custom_variation: 2
    model: my_block
    drop:
      silktouch: false 
      minimal_type: STONE
      loots:
        - {oraxen_item: caveblock, probability: 1.0}
```

### Customize the breaking speed

You can customize the breaking speed and the most suitable tools with the hardness subsection.

```yaml
Mechanics:
  noteblock:
    custom_variation: 2
    model: my_block
    hardness: 20 # this makes it really hard to mine
    drop:
      silktouch: false 
      minimal_type: STONE
      best_tools:
        - PICKAXE # and it's faster using a pickaxe
      loots:
        - {oraxen_item: caveblock, probability: 1.0}
```

### Limited placing
You can customize what blocks a custom block/furniture can be placed on with `limited_placing` subsection.
You can use the `roof`, `floor` and `wall` options to dictate where a block can be placed. By default, all are set to `true`.\
The `type` specifies if it should only be allowed on or denied on specific blocks.  
If type is `ALLOW` the block can only be placed on the given blocks.  
If the type is `DENY` can be placed on all blocks not matching the given blocks.  
```yaml
amethyst_ore:
  Mechanics:
    noteblock:
      limited_placing:
        roof: true
        floor: true
        wall: true
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

### Light Emitting Blocks

You can use the option **light** so that your block emits light.&#x20;

```yaml
Mechanics:
  noteblock:
    custom_variation: 2
    model: my_block
    light: 5
    drop:
      silktouch: false 
      loots:
        - {oraxen_item: my_custom_item, probability: 1.0}
```

{% hint style="info" %}
You need LightAPI for this, but will not work on any modern version of Paper due to chunk and lighting changes in Paper.\
You can find a fork of the original plugin [here](https://github.com/IPECTER/LighterAPI/releases/tag/5.4.0-SNAPSHOT)\
This should work on any modern version of Spigot and Paper.\
{% endhint %}

{% embed url="https://www.spigotmc.org/resources/lightapi.4510" %}

### Storage
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
{% hint style="info" %}\
This mechanic can also be used with the furniture mechanic!\
{% endhint %}

### Ores

This example configuration shows you how to create ores that support fortune and silktouch with a normal hardness.

```yaml
amethyst_ore:
  displayname: "&dAmethyst Ore"
  material: DIAMOND
  Pack:
    generate_model: true
    parent_model: "block/cube_all"
    textures:
      - amethyst_ore
  Mechanics:
    noteblock:
      block_sounds:
        place_sound: block.stone.place
        break_sound: block.stone.break
        hit_sound: my.custom.hitsound     # Custom sound as defined in Oraxen/sound.yml
        step_sound: my.custom.stepsound   # Requires a sound-file in the Oraxen/pack-folder aswell
        fall_sound: my.custom.fallsound
        volume: 0.8                      # Default: 0.8
        pitch: 0.8                       # Default: 0.8
      custom_variation: 1
      model: amethyst_ore
      hardness: 6
      drop:
        silktouch: true
        fortune: true
        minimal_type: IRON
        best_tools:
          - PICKAXE
        loots:
          - oraxen_item: amethyst
            probability: 1.0
```

{% hint style="info" %}
This does not actually spawn ores throughout your world.\
Look into one of the WorldGenerator plugins in [World Generators](../../compatibility/world-generators/README.md) for that.\
{% endhint %}

### Custom blocks with Custom Model

```yaml
box_block:
  displayname: "<white>box"
  material: PAPER
  Pack:
    generate_model: false # because this is a block, a 2nd model pointing to specified one will be generated anyway
    model: custom/furniture/caja
  Mechanics:
    noteblock:
      custom_variation: 3
      model: custom/furniture/caja
      hardness: 6
      drop:
        silktouch: false 
        best_tools:
          - AXE
        loots:
          - { oraxen_item: box_block, probability: 1.0 }
```

![](https://cdn.discordapp.com/attachments/958524021035647046/961362589735088178/unknown.png)

{% hint style="info" %}
This feature does not support borders that are less than 16x16x16.
{% endhint %}
