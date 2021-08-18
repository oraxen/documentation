---
description: How to add non cubic blocs to the game
---

# Furniture Mechanic

## How does it work?

Oraxen uses invisible item frames to add non cubic blocks to the game. This avoids some lags causes by armorstands You can then activate a transparent block \(barrier\) on top to act as a hitbox.

![Example furniture](.gitbook/assets/image%20%283%29.png)

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

## Light

You can configure your furniture so it produces light. To do so you need to install this plugin: [Light API \(fork\)](https://www.spigotmc.org/resources/lightapi-fork.48247/)

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

