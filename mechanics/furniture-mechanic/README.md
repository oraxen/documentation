---
description: How to add non cubic blocs to the game
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966828778028417125/unknown.png
coverY: 0
---

# 🪑 Furniture Mechanic

## Furniture Mechanic

### Example configuration per item

```yaml
table:
  displayname: "<gray>Table"
  material: DIAMOND
  Pack:
    generate_model: false
    model: default/table
  Mechanics:
    furniture:
      type: DISPLAY_ENTITY #Valid types are ITEM_FRAME, DISPLAY_ENTITY & GLOWING_ITEM_FRAME
      block_sounds:
        place_sound: block.stone.place
        break_sound: block.stone.break
        hit_sound: my.custom.hitsound     # Custom sound as defined in Oraxen/sound.yml
        step_sound: my.custom.stepsound   # Requires a sound-file in the Oraxen/pack-folder aswell
        fall_sound: my.custom.fallsound
      hitbox:
        barrierHitboxes:
          - 0,0,0
      drop:
        silktouch: false
        loots:
          - { oraxen_item: table, probability: 1.0 }
```

### Custom Sounds

Furniture, like custom blocks, can have custom sounds

```yaml
Mechanics:
  furniture:
    block_sounds:
      place_sound: block.stone.place
      break_sound: block.stone.break
      hit_sound: my.custom.hitsound     # Custom sound as defined in Oraxen/sound.yml
      step_sound: my.custom.stepsound   # Requires a sound-file in the Oraxen/pack-folder aswell
      fall_sound: my.custom.fallsound
```

All the volume and pitch values are set to be what Minecraft uses for blocks normally.\
If you want to change the volume or pitch, you can do so by using the format below.\
Keep in mind these two formats are compatible with eachother.\
We recommend just use the default one, but the option is there if you want to change it.

```yaml
Mechanics:
  furniture:
    block_sounds:
      place:
        sound: block.stone.place
        volume: 1.0
        pitch: 0.2
      break_sound: block.stone.break
      hit_sound: my.custom.hitsound     # Custom sound as defined in Oraxen/sound.yml
      step_sound: my.custom.stepsound   # Requires a sound-file in the Oraxen/pack-folder aswell
      fall_sound: my.custom.fallsound
```

### Rotatable

To make a furniture rotatable, simply add the following to your item's config.

```yaml
Mechanics:
  furniture:
    rotatable: true
```

### Hitboxes

Furnitures can have two types of hitboxes, with or without collision.\
Collision hitboxes are barrier-blocks, whilst non-solid ones are interaction-entities.\
Below are examples of how to use both.\
\
**Barrier** hitboxes can be formatted at a given offset from the furniture.

```yaml
Mechanics:
  furniture:
    hitbox:
      barrierHitboxes:
        - 0,0,0
        - 0,0,1
        - 0,0,2
        - 1,0,0
        - 1,0,1
        - 1,0,2
```

\
**Interaction-Entity Hitboxes** use the Interaction-entity added in 1.19.4.\
This of course means that 1.19-1.19.3 servers will not be able to use this..\
Each interaction-hitbox takes a **width**, **height** and an **offset**

```yaml
Mechanics:
  furniture:
    hitbox:
      interactionHitboxes:
        - 1 1 0,0,0
        - 1 2.0 1,0,0
        - 1 2.2 -1,0,0
```

### ModelEngine Furniture

To make use of a ModelEngine model as your furniture, simply add the following to your item's config:

```yaml
Mechanics:
  furniture:
    modelengine_id: name_of_your_bbmodel_file
```

### Jukebox

Lets this furniture accept music discs and custom music discs which will be played.\
You can tweak the `volume` and `pitch` of the music from the jukebox.\
There is also a `permission` field, which can be used if you only want certain players to be able to play music from the jukebox.\
By default permission is blank, which means anyone can play music from the jukebox.

```yaml
Mechanics:
  furniture:
    jukebox:
      volume: 1.0
      pitch: 1.0
      permission: "oraxen.jukebox.play"
```

### Seats

Seats can be configured to spawn with a given offset from the base furniture, like below

```yaml
Mechanics:
  furniture:
    seats:
      - 0,0.5,0
```

### Restrict Rotation

You can restrict the amount of rotation-facings a furniture has with `restricted_rotation`.\
It can be set to STRICT or VERY\_STRICT, with 8 and 4 facings respectively.\\

```yaml
chair:
  Mechanics:
    furniture:
      restricted_rotation: VERY_STRICT #STRICT is default if unspecified
```

### Limited placing

You can customize what blocks a custom block/furniture can be placed on with `limited_placing` subsection. You can use the `roof`, `floor` and `wall` options to dictate where a block can be placed. By default, all are set to `true`.\
The `type` specifies if it should only be allowed on or denied on specific blocks.\
If type is `ALLOW` the block can only be placed on the given blocks.\
If the type is `DENY` can be placed on all blocks not matching the given blocks.\
There is also a `radius_limitation` option, which allows you to limit the amount of a certain furniture within a radius.

```yaml
chair:
  Mechanics:
    furniture:
      limited_placing:
        radius_limitation:
          radius: 20
          amount: 10
        roof: false
        floor: true
        wall: false
        type: ALLOW
        block_types:
          - GRASS_BLOCK
          - DIRT
        block_tags:
          - base_stone_nether
        oraxen_blocks:
          - chair
          - ruby_ore
```

The `block_tags` can be found at [this page](https://minecraft.fandom.com/wiki/Tag#Block\_tags). Useful if you want to allow/deny a group of blocks.\
The `block_types` are materials. Useful if you want to allow/deny a specific list block.\
The `oraxen_blocks` are blocks defined in the oraxen configuration.\
This allows all custom blocks and furniture in here, but furniture requires a barrier-hitbox.

### Storage

This is a sub-mechanic for furniture and noteblock mechanics, that let you make a custom storage container.\
Essentially a chest, closet or whatever you might want.

There's a few different types: _STORAGE, PERSONAL, ENDERCHEST & DISPOSAL_.\
**STORAGE** is similar to a normal chest. Anyone can open it and view the content of it.\
**PERSONAL** is essentially a custom enderchest, letting you edit the row-count and so on.\
**ENDERCHEST** is literally just the enderchest inventory, but letting you make a custom block/furniture to access it.\
**DISPOSAL** is a custom trashcan, letting you throw items in it, and they will be deleted when closed.\\

```yaml
Mechanics:
  furniture:
    barrier: true
    storage:
      type: STORAGE
      rows: 5                             # Default: 6
      title: "<red>My Storage"            # Default: "Storage"
      open_sound: entity.shulker.open     # Default: entity.chest.open
      close_sound: entity.shulker.close   # Default: entity.chest.close
```

{% hint style="info" %}
This mechanic requires a barrier(s) if used with furniture!
{% endhint %}

### Light

You can configure your furniture so it emits light. This option corresponds to light intensity and must be between 1 and 15.

```yaml
Mechanics:
  furniture:
    light: 5
    drop:
      silktouch: false
      loots:
        - { oraxen_item: table, probability: 1.0 }
```

### BlockLocker

You can use this to allow protection via [BlockLocker](https://www.spigotmc.org/resources/blocklocker.3268/)\
Valid protectionTypes are CONTAINER, DOOR, ATTACHABLE

```yaml
Mechanics:
  furniture:
    blocklocker:
      can_protect: true
      protection_type: CONTAINER
```
