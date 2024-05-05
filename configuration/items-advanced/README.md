---
description: All the subtleties of item creation
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966824770651967498/unknown.png
coverY: 0
---

# Items (advanced)

## Vanilla options

### ItemTemplate
This allows you to easily copy properties from a template-item onto other items.\
In the template item:
```yml
template_item:
  template: true
  material: DIAMOND_SWORD
  ...
```

In the item you want to copy the properties to:
```yml
template_item1:
  template: template_item
  displayname: Template Item 1

template_item2:
  template: template_item
  displayname: Template Item 2
  material: CLOCK
```

### DisplayName

This allows you to change the name displayed on the top of an item.

```yaml
my_item:
  displayname: "<red><bold>Example" #example name
```

### Material

This allows you to change the item type

```yaml
my_item:
  material: WOODEN_SWORD
```

### Color

This allows you to change the color of an item made of a supported material (e.g. leather armor).

```yaml
my_item:
  color: 3, 252, 136 #rgb
```

### Lore

This allows you to add lines of text under the item name.

```yaml
my_item:
  lore:
  - "One line"
  - "<green>Another line"
```

### injectID

This allows Oraxen to know recognise the item, it is by default set to true and you should not have to change it. If you do it anyway, the mechanics of the items will no longer work.

```yaml
my_item:
  injectID: false
```

### Disable Enchanting
This options allows you to prevent an item from being enchanted via anvils or enchantment tables.\
This does not prevent enchantments from being applied in the config.\
```yaml
my_item:
  disable_enchanting: true
```

### excludeFromInventory

This option allows you to exclude an item from the oraxen inventory. It will no longer be displayed but you can still get it using [oraxen give command](../../usage/commands.md#get-the-items). It is useful for items used in  other plugins like inventory icons.

```yaml
  excludeFromInventory: true
```

### durability

This allows you to change the number of damage of a item (not very useful)\
{% hint style="info" %}
As of Oraxen 1.174.0 this has been removed for all servers below 1.20.5.\
It instead now defines the max-durability of an item when server is 1.20.5+
{% endhint %}
```yaml
my_item:
  durability: 10
```

### unbreakable

This will make your item unbreakable (for real, using minecraft dedicated property).

```yaml
my_item:
  unbreakable: true
```

### Unstackable
This will make your item unstackable. Useful for backpacks and other custom items that you want to be unique.
```yaml
my_item:
  unstackable: true
```

### ItemFlags

This allows you to set ItemFlags to an item, get the list of available flags [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/inventory/ItemFlag.html).

```yaml
my_item:
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
my_item:
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
my_item:
  AttributeModifiers:
    # - attribute: Get the list here: https://hub.spigotmc.org/javadocs/spigot/org/bukkit/attribute/Attribute.html
    # - operations: 0 for ADD_NUMBER, 1 for ADD_SCALAR, 2 for MULTIPLY_SCALAR_1;
    # - slot: HAND, OFF_HAND, FEET, LEGS, CHEST or HEAD
    - {
       attribute: GENERIC_MOVEMENT_SPEED, 
       amount: 0.1, 
       operation: 0, 
       slot: HAND
      }
```

### Enchantments

If you want to enchant your item (even with non vanilla levels like for example sharpness 15), you can do it with this section.

```yaml
my_item:
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

### 1.20.5 Specific Properties
`max_stack_size` - Sets the maximum slot-size of an OraxenItem\
`enchantment_glint_override` - Sets an override-state for the enchantment glint\
`fire_resistant` - Sets whether this OraxenItem is immune to fire and lava\
`durability` - Sets the durability of this OraxenItem\
`hide_tooltips` - Hides all tooltips from the given OraxenItem on hover\
`food` - Makes this item consumable with several different properties

Example of all the above properties:
```yaml
my_item:
  #itemname is also allowed
  displayname: <gradient:#4B36B1:#6699FF>My Item
  material: IRON_PICKAXE
  enchantment_glint_override: false
  durability: 10
  # if the material above isnt a normal tool, but say PAPER
  # The item will not have its durability lowered by actions by default
  # Example of making the tool lower its durability from hitting entities and breaking blocks
  #durability:
  #  value: 10
  #  damage_block_break: true
  # damage_entity_hit: true
  max_stack_size: 10
  fire_resistant: true
  hide_tooltips: true
  food:
    nutrition: 2
    saturation: 2
    can_always_eat: true
    eat_seconds: 1.6
    effects:
      mining_fatigue:
        duration: 10
        amplifier: 1
        ambient: false
        show_icon: true
        show_particles: true
        probability: 50
```

### How do I set a specific Custom Model Data?

```yaml
my_item:
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
