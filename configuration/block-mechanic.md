---
description: How to add your own blocks to the game
---

# Block mechanic

## How does it work?

Unlike items, blocks cannot be added to the game using predicates in a model, in fact it is not really possible to add new blocks ...at least the game wasn't made for that. But there are still some hacked-up techniques to do it anyway. Oraxen is using blockstates to attribute block models \(the json file which contains all the informations needed by Minecraft in order to render the block\) depending of the blockfacing of the base block. Basically it uses the variations of a vanilla blocks which can have different blockfacing: the mushroom stem block. Only one variation is used in vanilla minecraft maps for this block, there are 6 faces on a block so we have 2^6 - 1 = 63 possible variations.

## Global configuration

This global configuration has to be used in order to define the hierarchy of between your multiple tool\_types. You can put the normal types + new types you just invented.

```yaml
block:
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

The oraxen item root configuration is the same as for any item \(you can use any material like a diamond for example\) and set a displayname, etc. For the pack section you can use your own model or generate one. To generate a block model juste tell to oraxen that the parent model  is "block/cube\_all", then add your block texture \(one face\) inside your oraxen/pack/textures folder.

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

To use this mechanic you need to tell to oraxen which model to use \(to use the generated one, just put the name id of your item\). You then need to use custom\_variation which is not already used by another block \(since by default 1 is used by caveblock, you can for example use 2\). This example drop configurations allows you to get the drop when you mine it with a stone pickaxe.

```yaml
  Mechanics:
    block:
      custom_variation: 2
      model: my_block
      drop:
        silktouch: false 
        minimal_type: STONE
        loots:
          - {oraxen_item: caveblock, probability: 1.0}
```

### Ores

This example configuration shows you how to create ores that support fortune and silktouch.

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
    block:
      custom_variation: 2
      model: amethyst_ore
      drop:
        silktouch: true
        fortune: true
        minimal_type: IRON
        loots:
          - {oraxen_item: amethyst, probability: 1.0}
```



