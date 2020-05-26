---
description: Aka how to give superpowers to your items
---

# Mechanics

## Introduction

It's easy to make very nice items on oraxen and change their abilities but how about doing a lot more? The mechanics allow you to assign special abilities with a specific configuration to each item. It's easy to make very nice items on oraxen and change their abilities but how about doing a lot more? The mechanics allow you to assign special abilities with a specific configuration to each item. For example you can create a pickaxe than can mine bedrock or a sword which steals hearts from your opponents.

## How to add a mechanic to an item?

### Items dedicated configurations

As you've seen in the [dedicated part of the beginner tutorial](create-your-first-item.md#4-lets-improve-our-item-with-mechanics), you just need to add a new section called mechanics which will contain all your wanted mechanics in subsections.

```yaml
example_item:
  material: DIAMOND_AXE
  Mechanics:
    # Your mechanics go here

    example_mechanic:
      example_option: true
    
    another_example_mechanic:
      another_option: "example text"
```

Each subsection of a mechanic inside an item configuration allows you to change various settings of your mechanic, and only for this item. What that means is that if for example you add bigmining mechanic to a pickaxe and you configure it to mine 5\*5 blocs, you can also use it on another item and configure this other item to mine only 3\*3 blocs.

### Global configurations

These settings are saved into the file `mechanics.yml` at the root of your Oraxen folder. They allow you to change global parameters for all item using this mechanic. You won't need it often but it can be useful. For example for the bedrockbreak mechanic which allows you to break bedrock. Most of servers don't want their player to break the ground of the world : the last layer of bedrock. In the global configuration of bedrockbreak mechanic you can change toggle this \(and this will get applied to all your items using this mechanic\).

```yaml
bedrockbreak:
  enabled: true
  disable_on_first_layer: false # this
  durability_cost: 500
```

