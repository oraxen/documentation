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
      rotation: NONE
      facing: UP
      barrier: true
      drop: # useless if you are not using a barrier
        silktouch: false
        loots:
          - { oraxen_item: table, probability: 1.0 }
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

### Limited placing
You can customize what blocks a custom block/furniture can be placed on with `limited_placing` subsection.  
There is both an `allow_on` and a `deny_on` subsection of this.

If there is no `allow_on` or `deny_on` section, then the block can be placed on everything.  
If there is both `allow_on` and `deny_on` sections, then it only takes `allow_on` into account.

If there is an `allow_on` section, but no `deny_on` section, the block can only be placed on blocks in `allow_on` section.
```yaml
Mechanics:
  furniture:
    limited_placing:
      allow_on:
        block_types:
          - GRASS_BLOCK
          - STONE
        block_tags:
          - wool
        oraxen_blocks:
          - my_block
```
If there is no `allow_on` section, but there is a `deny_on`, the block can be placed on anything not in `deny_on` section.
```yaml
Mechanics:
  furniture:
    limited_placing:
      deny_on:
        block_types:
          - GRASS_BLOCK
          - STONE
        block_tags:
          - wool
        oraxen_blocks:
          - my_block
```
The `block_tags` can be found at [this page](https://minecraft.fandom.com/wiki/Tag#Block_tags). Useful if you want to allow/deny a group of blocks.  
The `block_types` are materials. Useful if you want to allow/deny a specific list block.  
The `oraxen_blocks` are blocks defined in the oraxen configuration.  
This allows all custom blocks and furniture in here, but furniture requires a barrier-hitbox.

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
