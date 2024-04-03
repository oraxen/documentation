---
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966830020419014666/unknown.png
coverY: 0
---

# StringBlock Mechanic

## How does it work?

This is a variable of the custom blocks, but now you have to have a thread-based hitbox that allows you to make small decorative objects that can be traversed and are more optimized than furniture and the custom\_variation is different from that of the blocks.

### Global Configuration

```yaml
stringblock:
  tool_types:
    - WOODEN
    - STONE
    - IRON
    - GOLDEN
    - DIAMOND
    - NETHERITE
  enabled: true
```

## How do I create a decoration?

### Oraxen item and Pack configuration

```yaml
jasmine_flower:
  displayname: "<white>Jasmine Flower"
  material: PAPER
  Pack:
    generate_model: true
    parent_model: "block/cross"
    textures:
      - custom/flowers/jasmine_flower.png # .png extension is not mandatory
```

### StringBlock Mechanic Configuration

To use this mechanic you need to tell oraxen which model to use (to use the generated one, just put the id name of your item). Then you need to use custom\_variation that is not already used by another decoration (since by default 1 is used by brunnera, you can for example use 2). This example of drop settings allows you to get the drop when you mine it with a stone pickaxe.

```yaml
  Mechanics:
    stringblock:
      custom_variation: 2
      model: jasmine_flower
      hardness: 2
      drop:
        silktouch: false
        loots:
          - { oraxen_item: jasmine_flower, probability: 1.0 }
```

## Sapling

```yaml
sapling:
  Mechanics:
    stringblock:
      sapling:
        canGrowNaturally: true # if you want only the player can grow it
        naturalGrowthTime: 6000 #in ticks
        canGrowFromBoneMeal: true
        boneMealGrowChance: 50
        growSound: block.grass.break
        minLightLevel: 4
        requiresWaterSource: false #if you want it to need water
        schematicName: schemTest #structure that will put
```

You can also add some randomness to the growth, or just increase the delay between checks.\
Go into `mechanics.yml` and under stringblock-mechanic, adjust `sapling_growth_check_delay`\
This is in ticks, so 20 = 1 second.

## BlockLocker

You can use this to allow protection via [BlockLocker](https://www.spigotmc.org/resources/blocklocker.3268/)\
Valid protectionTypes are CONTAINER, DOOR, ATTACHABLE

```yaml
Mechanics:
  furniture:
    blocklocker:
      can_protect: true
      protection_type: CONTAINER
```

![](https://cdn.discordapp.com/attachments/958524021035647046/961424759718047784/unknown.png)
