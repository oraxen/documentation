---
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966827878706708560/unknown.png
coverY: 0
---

# Directional mechanic

### What is this?

This mechanic allows you to place blocks and have them change their texture depending on the direction in which they are placed, like for example logs.  
There are 3 types of directional blocks: `LOG`, `FURNACE` and `DROPPER`.  
`LOG` takes up 3 custom block variations, `FURNACE` takes 4 and `DROPPER` takes 6.  

{% hint style="info" %}
Every sub-block can have a `model` property, which Oraxen will use to determine what to display.  
If there is no `model` property on the sub-block, Oraxen will use the model from the parent-block.  
{% endhint %}

{% hint style="info" %}
Models are also automatically rotated depending on the direction in which the block is placed.  
This means you can use the same model, and it will be rotated accordingly.  
If the sub-block has a model defined, it will not be rotated, allowing you to use different models for different directions.
{% endhint %}

{% embed url="https://user-images.githubusercontent.com/62521371/167680557-750dac77-b4c4-4804-9513-184d776a012d.mp4" %}

### Configuration

### Parent-Block example:

```yaml
mainBlock:
  displayname: "<white>Frozen Mushroom Stem"
  material: PAPER
  Pack:
    generate_model: false
    model: mainBlockModel
  Mechanics:
    noteblock:
      model: mainBlockModel
      custom_variation: 1
      directional:
        # Valid values are LOG, FURNACE and DROPPER
        directional_type: LOG
        # LOG
        y_block: mainBlockY
        x_block: mainBlockX
        z_block: mainBlockZ
        # FURNACE and DROPPER
        north_block: mainBlockNorth
        east_block: mainBlockEast
        south_block: mainBlockSouth
        west_block: mainBlockWest
        # DROPPER needs these aswell
        up_block: mainBlockUp
        down_block: mainBlockDown
      hardness: 1
      drop:
        minimal_type: WOOD
        best_tools:
          - AXE
        silktouch: false
        loots:
          - {oraxen_item: mainBlock, probability: 1.0}
```

#### LOG-type example:
```yaml
#This doesn't include the parent block from the above example
mainBlockY:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      custom_variation: 1
      directional:
        parent_block: mainBlock #base block which will give drop
      
mainBlockX:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      custom_variation: 2
      directional:
        parent_block: mainBlock #base block which will give drop

mainBlockZ:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      custom_variation: 3
      directional:
        parent_block: mainBlock #base block which will give drop
```

#### FURNACE-type example:
```yaml
#This doesn't include the parent block from the above example
mainBlockNorth:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      model: mainBlockModel
      custom_variation: 1
      directional:
        parent_block: mainBlock #base block which will give drop
      
mainBlockSouth:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      model: mainBlockModel
      custom_variation: 2
      directional:
        parent_block: mainBlock #base block which will give drop

mainBlockWest:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      model: mainBlockModel
      custom_variation: 3
      directional:
        parent_block: mainBlock #base block which will give drop

mainBlockEast:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      model: mainBlockModel
      custom_variation: 4
      directional:
        parent_block: mainBlock #base block which will give drop
```

#### DROPPER-type example:
```yaml
#This doesn't include the parent block from the above example
mainBlockNorth:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      custom_variation: 1
      directional:
        parent_block: mainBlock #base block which will give drop
      
mainBlockSouth:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      custom_variation: 2
      directional:
        parent_block: mainBlock #base block which will give drop

mainBlockWest:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      custom_variation: 3
      directional:
        parent_block: mainBlock #base block which will give drop

mainBlockEast:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      custom_variation: 4
      directional:
        parent_block: mainBlock #base block which will give drop

mainBlockUp:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      model: mainBlockModel_vertical
      custom_variation: 5
      directional:
        parent_block: mainBlock #base block which will give drop

mainBlockDown:
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Mechanics:
    noteblock:
      model: mainBlockModel_vertical
      custom_variation: 6
      directional:
        parent_block: mainBlock #base block which will give drop
```
