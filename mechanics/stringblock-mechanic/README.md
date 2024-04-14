---
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966830020419014666/unknown.png
coverY: 0
---

# StringBlock Mechanic

## How does it work?

This is a type of CustomBlock best aimed at plants, rocks and other foliage.\
It uses the vanilla TripWire block and therefore will disable all normal behaviour TripWires might have.\
This allows for up to 127 custom block slots of this type.\
Another quirk with this CustomBlock is that it has 2 different hitbox-states\
All variations after 64 will have a smaller hitbox than those before.

## How do I create a stringblock?

### Oraxen Pack configuration

Below is an example of how to configure the model/texture to use.\
`block/cross` is what normal vanilla plants use and allows for converting a 2d-texture into a block.\
If you want an example, look at RoseBushes in-game.

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

To use this mechanic you need to tell oraxen which model to use (to use the generated one, just put the id name of your item).\
Then you need to use custom\_variation that is not already used by another decoration.\
You can also configure the hardness of the block, which specifies how long a block should take to break.\
`drop.best_tool` allows you to specify which tool should be best.\
An example would be PICKAXE for a small stone

```yaml
jasmine_flower:
  Mechanics:
    custom_block:
      type: STRINGBLOCK
      custom_variation: 2
      model: jasmine_flower
      hardness: 2
      drop:
        silktouch: false
        loots:
          - { oraxen_item: jasmine_flower, probability: 1.0 }
```

## Minor sub-mechanics

Stringblocks also have some additional properties.\
`placeable_on_water`allows you to place it on water like Lilypads\
`is_tall` makes the customblock have a double hitbox, much like Tall Grass\
`random_place` takes a list of strings representing other stringblock-mechanics. \
This will then place a random one of these when the "parent" is placed

## Sapling

```yaml
sapling:
  Mechanics:
    custom_block:
      type: STRINGBLOCK
      sapling:
        grows_naturally: true # if you want only the player can grow it
        natural_growth_time: 6000 #in ticks
        grows_from_bonemeal: true
        bonemeal_growth_speedup: 1250
        grow_sound: block.grass.break
        min_light_level: 4
        requires_water_source: false #if you want it to need water
        schematic: schemTest #structure that will put
        replace_blocks: false
        copy_biomes: false
        copy_entities: false
```

You can also add some randomness to the growth, or just increase the delay between checks.\
Go into `mechanics.yml` and under stringblock-mechanic, adjust `sapling_growth_check_delay`\
This is in ticks, so 20 = 1 second.

## BlockLocker

You can use this to allow protection via [BlockLocker](https://www.spigotmc.org/resources/blocklocker.3268/)\
Valid protectionTypes are CONTAINER, DOOR, ATTACHABLE

```yaml
Mechanics:
  custom_block:
    type: STRINGBLOCK
    blocklocker:
      can_protect: true
      protection_type: CONTAINER
```

![](https://cdn.discordapp.com/attachments/958524021035647046/961424759718047784/unknown.png)
