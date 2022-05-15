---
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966827878706708560/unknown.png
coverY: 0
---

# Directional mechanic

### What is this?

This mechanic allows you to place blocks and have them change their texture depending on the position in which they are placed, like the normal minecraft logs but now with custom blocks.

{% embed url="https://user-images.githubusercontent.com/62521371/167680557-750dac77-b4c4-4804-9513-184d776a012d.mp4" %}

### Configuration

```yaml
#This is simply meant to be a "hub" item
mainBlock:
  displayname: "<white>Frozen Mushroom Stem"
  material: PAPER
  Pack:
    generate_model: false
    model: mainBlockModel
    custom_model_data: 411
  Mechanics:
    noteblock:
      model: mainBlockModel
      custom_variation: 1
      directional:
        yBlock: mainBlockY #Y position of the block
        xBlock: mainBlockX #X position of the block
        zBlock: mainBlockZ #Z position of the block
      hardness: 1
      drop:
        minimal_type: WOOD
        best_tools:
          - AXE
        silktouch: false
        loots:
          - {oraxen_item: mainBlock, probability: 1.0}

mainBlockY:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      model: mainBlockModel
      custom_variation: 1
      directional:
        parentBlock: mainBlock #base block which will give drop
      
mainBlockX:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      model: mainBlockModel
      custom_variation: 2
      directional:
        parentBlock: mainBlock #base block which will give drop

mainBlockZ:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      model: mainBlockModel
      custom_variation: 3
      directional:
        parentBlock: mainBlock #base block which will give drop
```
