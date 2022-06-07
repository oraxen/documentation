---
description: All the subtleties of item creation
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966824770651967498/unknown.png
coverY: 0
---

# Items (advanced)

## Vanilla options

### displayname

This allows you to change the name displayed on the top of an item.

```yaml
  displayname: "&c&lExample" #example name
```

### material

This allows you to change the item type

```yaml
  material: WOODEN_SWORD
```

### color

This allows you to change the color of an item made of a supported material (e.g. leather armor).

```yaml
  color: 3, 252, 136 #rgb
```

### lore

This allows you to add lines of text under the item name.

```yaml
lore:
  - "One line"
  - "&aAnother line"
```

### injectID

This allows Oraxen to know recognise the item, it is by default set to true and you should not have to change it. If you do it anyway, the mechanics of the items will no longer work.

```yaml
  injectID: false
```

### excludeFromInventory

This option allows you to exclude an item from the oraxen inventory. It will no longer be displayed but you can still get it using [oraxen give command](../../usage/commands.md#get-the-items). It is useful for items used in  other plugins like inventory icons.

```yaml
  excludeFromInventory: true
```

### durability

This allows you to change the number of damage of a item (not very useful)

```yaml
  durability: 10
```

### unbreakable

This will make your item unbreakable (for real, using minecraft dedicated property).

```yaml
unbreakable: true
```

### ItemFlags

This allows you to set ItemFlags to an item, get the list of available flags [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html).

```yaml
  ItemFlags:
    - HIDE_ENCHANTS
    - HIDE_ATTRIBUTES
    - HIDE_UNBREAKABLE
    - HIDE_DESTROYS
    - HIDE_PLACED_ON
    - HIDE_POTION_EFFECTS
```

### PotionEffects

This allows you to add custom Potion Effects to your potion. Get the list of available effects [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionEffectType.html).

```yaml
  PotionEffects:
    # - type: Get the list here: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionEffectType.html
    # - duration: in ticks
    # - amplifier: potion effects level
    # - ambient: true/false, makes potion effect produce more, translucent, particles.
    # - particles: true/false, whether this effect has particles or not
    # - icon: true/false, whether this effect has an icon or not
    - { type: WITHER,
        duration: 200,
        amplifier: 2,
        ambient: false,
        particles: true,
        icon: true }
```

### AttributeModifiers

This allows you to add minecraft attributes to your item. They are very powerful and allow you to make an item that adds hearts, increases the player's speed, etc. Get the list of available attributes [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/attribute/Attribute.html).

```yaml
  AttributeModifiers:
    # - name: You don't really care about the name but it can be useful for some developers
    # - attribute: Get the list here: https://hub.spigotmc.org/javadocs/spigot/org/bukkit/attribute/Attribute.html
    # - operations: 0 for ADD_NUMBER, 1 for ADD_SCALAR, 2 for MULTIPLY_SCALAR_1;
    # - uuid: put a random uuid, generate one here: https://www.uuidgenerator.net/
    # - slot: HAND, OFF_HAND, FEET, LEGS, CHEST or HEAD
    - {name: "oraxen_speed", 
       attribute: GENERIC_MOVEMENT_SPEED, 
       amount: 0.1, 
       operation: 0, 
       uuid: 3a25f0b5-dbda-4e38-b097-9e75e37ae464, 
       slot: HAND}
```

### Enchantments

If you want to enchant your item (even with non vanilla levels like for example sharpness 15), you can do it with this section.

```yaml
  Enchantments:
    protection: 4
    flame: 34
    sharpness: 18
```

Here is a list of enchants available in minecraft vanilla:

```
protection
fire_protection
feather_falling
blast_protection
projectile_protection
respiration
aqua_affinity
thorns
depth_strider
frost_walker
binding_curse
sharpness
smite
bane_of_arthropods
knockback
fire_aspect
looting
sweeping
efficiency
silk_touch
unbreaking
fortune
power
punch
flame
infinity
luck_of_the_sea
lure
loyalty
impaling
riptide
channeling
multishot
quick_charge
piercing
mending
vanishing_curse
soul_speed
```

### How do I set a specific Custom Model Data?

```yaml
  Pack:
    generate_model: true
    parent_model: "custom/items/generated_elite"
    textures:
      - custom/items/elite_zombie_walk
    custom_model_data: 452
```

## Pack options

This part has a dedicated page, you can consult it [here](../item-appearance.md).

## Mechanics options

This part has a dedicated page, you can consult it [here](../../mechanics/mechanics-introduction.md).
