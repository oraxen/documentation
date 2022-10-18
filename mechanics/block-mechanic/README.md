---
description: How to add your own blocks to the game
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966827878706708560/unknown.png
coverY: 0
---

# Block mechanic

## How does it work?

Unlike items, blocks cannot be added to the game using predicates in a model, in fact it is not really possible to add new blocks ...at least the game wasn't made for that. But there are still some hacked-up techniques to do it anyway. Oraxen allows you to do this in two different ways. Blockstates (the json file which contains all the informations needed by Minecraft in order to render the block) can be used to attribute block models according to the characteristics of particular blocks. The oldest method  relies on the blockfacing of the base block. Basically it uses the variations of a vanilla blocks which can have different blockfacing: the mushroom stem block. Only one variation is used in vanilla minecraft maps for this block, there are 6 faces on a block so we have 2^6 - 1 = 63 possible variations.

The most recent (and recommended) method is to use noteblocks and assign them different models depending on their instrument, their note and whether they are activated or not. This makes 800 possibilities (but 25 are reserved so that the vanilla noteblocks still work).

{% hint style="info" %}
The `block (`mushroom block ) and `noteblock` ( noteblock ) mechanics have the same configuration. To switch from one to the other you just have to rename the `block` section to `noteblock` and vice versa.
{% endhint %}

## Global configuration

This global configuration has to be used in order to define the hierarchy of between your multiple tool\_types. You can put the normal types + new types you just invented.

```yaml
noteblock:
  tool_types:
    - WOODEN
    - STONE
    - IRON
    - GOLDEN
    - DIAMOND
    - NETHERITE
  enabled: true
```

## How to create a simple block?

### Oraxen item and Pack configuration

The oraxen item root configuration is the same as for any item (you can use any material like a diamond for example) and set a displayname, etc. For the pack section you can use your own model or generate one. To generate a block model juste tell to oraxen that the parent model  is "block/cube\_all", then add your block texture (one face) inside your oraxen/pack/textures folder.

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
The `type` specifies if it should only be allowed on or denied on specific blocks.  
If type is `ALLOW` the block can only be placed on the given blocks.  
If the type is `DENY` can be placed on all blocks not matching the given blocks.  
```yaml
amethyst_ore:
  Mechanics:
    noteblock:
      limited_placing:
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

### Produce Light

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
You need Light Api for this
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
