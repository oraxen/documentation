---
description: How to add your own blocks to the game
cover: >-
  https://cdn.discordapp.com/attachments/896841661580185620/969663283445510214/Screenshot_20220429_131532.jpg
coverY: 0
---

# Farmblock Mechanic

## How does it work?

This is a block system for custom plants and crops where you have your own watering system to make the plant grow.

## Global configuration

The global configuration has to be used to activate or deactivate this mechanism.

```yaml
noteblock:
  tool_types:
    - WOODEN
    - STONE
    - IRON
    - GOLDEN
    - DIAMOND
    - NETHERITE
  farmblock_check_delay: 1000 # ticks between each check for dryout
  enabled: true

harvesting:
  enabled: true

watering:
  enabled: true
```

## How to create a simple farmblock?

### Oraxen item and Pack configuration

In this case you cannot create blocks using this mechanics without having a pre-made model, and you have to create 2 models for each item, one with water and one without

```yaml
epic_box_dry:
  displayname: "<white>Epic Box"
  material: PAPER
  Pack:
    generate_model: false
    model: epic_box_dry
    custom_model_data: 83
  Mechanics:
    noteblock:
      custom_variation: 49
      model: epic_box_dry
      hardness: 5
      farmblock:
        moistFarmBlockPath: epic_box_wet
        farmBlockDryOutTime: 30000 # in milliseconds (30000ms = 30s)

epic_box_wet:
  displayname: "<white>Epic Box Wet"
  excludeFromInventory: true # Makes inventory only contain base-block
  material: PAPER
  Pack:
    generate_model: false
    model: epic_box_wet
    custom_model_data: 84
  Mechanics:
    noteblock:
      custom_variation: 48
      hardness: 5
      model: epic_box_wet
      farmblock:
        farmBlockPath: epic_box_dry
        farmBlockDryOutTime: 30000 # in milliseconds (30000ms = 30s)
```

In this example there are 2 blocks configured separately\
epic\_box\_dry is the Farmblock dry and \
epic\_box\_wet is the model with water.

farmBlockPath is the Oraxen item to be transformed into if it has no water \
moistFarmBlockPath is the Oraxen item it will become if it has water. \
farmBlockDryOutTime the time in which the water will run out\


### How do I water my blocks?

Oraxen has a watering can system that allows with a custom item to water a Farmblock and this also requires 2 models, one with water and one without, this is an example.

```yaml
epic_watering_vacuum:
  displayname: '<white>Epic Watering Vacuum'
  material: LEATHER_HORSE_ARMOR
  Mechanics:
    watering:
      filledCanItem: epic_watering_full #Item to replace when can is filled
  Pack:
    generate_model: false
    model: items/epic_watering_vacuum
    custom_model_data: 499

epic_watering_full:
  displayname: '<white>Epic Watering Full'
  material: LEATHER_HORSE_ARMOR
  Mechanics:
    watering:
      emptyCanItem: epic_watering_vacuum #Item to replace when can is empty
  Pack:
    generate_model: false
    model: custom/plants/epic_watering_full
    custom_model_data: 500
```



### Do you want to know how to make custom plants? [Click here](../furniture-mechanic/farming-mechanic.md)
