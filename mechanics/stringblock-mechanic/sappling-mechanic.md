---
cover: https://i.pinimg.com/originals/d4/77/45/d47745d48330de3e7fec0691ef0b32b9.jpg
coverY: 0
---

# Sappling Mechanic

{% hint style="info" %}
only for 1.136.0+
{% endhint %}

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
    sapling_growth_check_delay: 4000
    enabled: true
```

## How do I create a decoration?

### Oraxen item and Pack configuration

```yaml
sapling:
  displayname: "Sapling"
  material: PAPER
  Pack:
    generate_model: false
    custom_model_data: 415
    model: flowers/maricold_tall
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
      break_sound: block.grass.break
      place_sound: block.grass.place
      custom_variation: 23
      model: flowers/maricold_tall
      hardness: 2
      drop:
        silktouch: false
        loots:
        - oraxen_item: sapling
          probability: 1.0
```

{% embed url="https://cdn.discordapp.com/attachments/743544047733440582/985657454400532580/2022-06-12_16-29-55.mp4" %}

