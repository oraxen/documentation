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
Supported parent\_models for block are:\
`block/cube_all`, `block/cross`, `block/orientable`, `block/orientable_vertical` and `block/cube_column`.

```yaml
my_block:
  displayname: "My block"
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

<pre class="language-yaml"><code class="lang-yaml">my_block:
<strong>  Mechanics:
</strong>    custom_block:
      type: NOTEBLOCK
      custom_variation: 2
      model: my_block
      drop:
        silktouch: false 
        minimal_type: STONE
        loots:
          - {oraxen_item: caveblock, probability: 1.0}
</code></pre>

### Customize the breaking speed

You can customize the breaking speed and the most suitable tools with the hardness subsection.\
`drop.best_tool` dictates the "preferred tool" for this block which further tweaks the speed

```yaml
my_block:
  Mechanics:
    custom_block:
      type: NOTEBLOCK
      custom_variation: 2
      model: my_block
      hardness: 20 # this makes it really hard to mine
      drop:
        silktouch: false 
        minimal_type: STONE
        best_tool: PICKAXE
        loots:
          - {oraxen_item: caveblock, probability: 1.0}
```

### Limited placing

You can customize what blocks a custom block/furniture can be placed on with `limited_placing` subsection. You can use the `roof`, `floor` and `wall` options to dictate where a block can be placed. By default, all are set to `true`.\
The `type` specifies if it should only be allowed on or denied on specific blocks.\
If type is `ALLOW` the block can only be placed on the given blocks.\
If the type is `DENY` can be placed on all blocks not matching the given blocks.

```yaml
amethyst_ore:
  Mechanics:
    custom_block:
      type: NOTEBLOCK
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

The `block_tags` can be found at [this page](https://minecraft.fandom.com/wiki/Tag#Block\_tags). Useful if you want to allow/deny a group of blocks.\
The `block_types` are materials. Useful if you want to allow/deny a specific list block.\
The `oraxen_blocks` are blocks defined in the oraxen configuration.\
This allows all custom blocks and furniture in here, but furniture requires a barrier-hitbox.

### Beacon Base

You can also make a custom block work in beacons with the following:

{% code lineNumbers="true" %}
```yaml
my_block:
  Mechanics:
    custom_block:
      type: NOTEBLOCK
      beacon_base_block: true
```
{% endcode %}

{% hint style="info" %}
A beacon will "activate" if any noteblock is in the pyramid, but the effect is only given when said noteblock(s) are base\_beacon\_blocks\
This is because it requires a Datapack that adds noteblocks to the given Tag, but it does not support individual blockstates
{% endhint %}

### Light Emitting Blocks

You can use the option **light** so that your block emits light.

{% code lineNumbers="true" %}
```yaml
my_block:
  Mechanics:
    custom_block:
      type: NOTEBLOCK
      light: 5
```
{% endcode %}

### BlockLocker

You can use this to allow protection via [BlockLocker](https://www.spigotmc.org/resources/blocklocker.3268/) Valid protectionTypes are CONTAINER, DOOR, ATTACHABLE

```yaml
my_block:
  Mechanics:
    custom_block:
      type: NOTEBLOCK
      blocklocker:
        can_protect: true
        protection_type: CONTAINER
```

### Storage

This is a sub-mechanic for furniture and noteblock mechanics, that let you make a custom storage container.\
Essentially a chest, closet or whatever you might want.

There's a few different types: _STORAGE, PERSONAL, ENDERCHEST & DISPOSAL_.\
**STORAGE** is similar to a normal chest. Anyone can open it and view the content of it.\
**PERSONAL** is essentially a custom enderchest, letting you edit the row-count and so on.\
**ENDERCHEST** is literally just the enderchest inventory, but letting you make a custom block/furniture to access it.\
**DISPOSAL** is a custom trashcan, letting you throw items in it, and they will be deleted when closed.\\

```yaml
my_block:
  Mechanics:
    custom_block:
      type: NOTEBLOCK
      storage:
        type: STORAGE
        rows: 5                             # Default: 6
        title: "<red>My Storage"            # Default: "Storage"
        open_sound: entity.shulker.open     # Default: entity.chest.open
        close_sound: entity.shulker.close   # Default: entity.chest.close
```

### Falling Blocks

This is a sub-mechanic that mimics sand & gravel for your custom block. Placing it next to another block, with no block beneath, will make it fall

```yaml
my_block:
  Mechanics:
    custom_block:
      type: NOTEBLOCK
      is_falling: true # Default to false if unspecified
```
