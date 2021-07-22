---
description: How to add non cubic blocs to the game
---

# Furniture Mechanic

## How does it work?

Oraxen uses invisible item frames to add non cubic blocks to the game. This avoids some lags causes by armorstands You can then activate a transparent block \(barrier\) on top to act as a hitbox.

![Example furniture](../.gitbook/assets/image%20%283%29.png)

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

