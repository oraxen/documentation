---
description: All the subtleties of item creation
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966824770651967498/unknown.png
coverY: 0
---

# Items (advanced)

## Vanilla options

### Components

{% tabs %}
{% tab title="1.21.2+" %}
`max_stack_size` - Sets the maximum slot-size of an OraxenItem\
`enchantment_glint_override` - Sets an override-state for the enchantment glint\
`fire_resistant` - Sets whether this OraxenItem is immune to fire and lava\
`durability` - Sets the durability of this OraxenItem\
`hide_tooltip` - Hides all tooltips from the given OraxenItem on hover\
`food` - Makes this item consumable with several different properties\
`jukebox_playable` - Lets this item be inserted into a Jukebox and play a given song

* `show_in_tooltip` - Show song-info in Item-Tooltip
* `song_key` - The key of the song (Custom songs requires datapacks)

`equippable` - Make this item equippable like armor\
`damage_resistant` - Specify a damage-type this item is invulnerable to

* If you want to do multiple damage-types, you need a datapack with a new custom tag
* All available damage-types can be found [here](https://minecraft.wiki/w/Tag#Damage\_type\_tags)&#x20;

`enchantable` - Set the maximum enchantment-cost for this item in an enchanting table\
`glider` - Allows the player to glide, like with elytra, when equipped\
`item_model` - The base-model for this item, can replace custom\_model\_data

* References model in `assets/<namespace>/models/item/<model>` -> `item_model: namespace:model`&#x20;

`tooltip_style` - Style of the items tooltip

* References custom sprite-background at `assets/<namespace>/textures/gui/sprites/tooltip/<id>_background`
* References custom sprite-frame at `assets/<namespace>/textures/gui/sprites/tooltip/<id>_frame`
* Can be customized & animated using mcmeta [Wiki](https://minecraft.wiki/w/Resource\_pack#Animation#Gui)&#x20;

`use_cooldown` - Applies a cooldown to all matching items when used\
`use_remainder` - Replaces the item with a remainder item if its stack count has decreased after use



Example of all the above properties:

{% code fullWidth="true" %}
```yaml
my_item:
  itemname: <gradient:#4B36B1:#6699FF>My Item
  Components:
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
    hide_tooltip: true
    tool:
      #damage_per_block:                       # Optional, defaults to 1
      #default_mining_speed:                   # Optional, defaults to 1.0
      rules:
        - speed: 1.0
          correct_for_drops: true             # If mining the given blocks should drop or not
          material: DIAMOND_BLOCK             # The material this rule applies to, also supports list format
          #materials:
          #  - DIAMOND_BLOCK
          #  - NETHERITE_BLOCK
          # List of all tags can be found at https://minecraft.wiki/w/Tag#Block_tags_2
          tag: minecraft:mineable/axe         # The block-tag this rule applies to, also supports list format
          #tags:
          #  - minecraft:mineable/axe
          #  - minecraft:mineable/shovel
    food:
      nutrition: 2
      saturation: 2 
      #can_always_eat: false                   # Optional, default is false
    damage_resistant: is_fire
    enchantable: 1
    glider: true
    item_model: minecraft:example         #`assets/minecraft/models/item/example.json`
    tooltip_style: minecraft:example      #`assets/minecraft/textures/gui/sprites/tooltip/example_(background & frame)`
    use_remainder:
      #minecraft_type: DIAMOND
      #crucible_item: crucibleid
      #eco_item: ecoid
      #mmoitems_id: id
      #mmoitems_type: type
      oraxen_item: itemid
    use_cooldown:
      seconds: 1.2                        #Default is 1.0
      group: oraxen:example               #Default is `oraxen:itemid`, set to ""-blank to affect by material
    equippable:
      slot: HEAD
      #model: minecraft:example           Optional, primarily useful for Custom-Armor
      #camera_overlay: minecraft:example  Optional, used by carved_pumpkin etc, example; `assets/minecraft/textures/example.png`
      #equip_sound: item.armor.equip_chain
      #allowed_entities:                  Optional, defaults to all entities
      #  - PLAYER
      #  - SKELETON
      #dispensable: true                  Optional, default is true
      #swappable: true                    Optional, default is true
      #damage_on_hurt: true               Optional, default is true
```
{% endcode %}
{% endtab %}

{% tab title="1.21" %}
`max_stack_size` - Sets the maximum slot-size of an OraxenItem\
`enchantment_glint_override` - Sets an override-state for the enchantment glint\
`fire_resistant` - Sets whether this OraxenItem is immune to fire and lava\
`durability` - Sets the durability of this OraxenItem\
`hide_tooltip` - Hides all tooltips from the given OraxenItem on hover\
`food` - Makes this item consumable with several different properties\
`jukebox_playable` - Lets this item be inserted into a Jukebox and play a given song

* `show_in_tooltip` - Show song-info in Item-Tooltip
* `song_key` - The key of the song (Custom songs requires datapacks)

Example of all the above properties:

```yaml
my_item:
  itemname: <gradient:#4B36B1:#6699FF>My Item
  Components:
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
    hide_tooltip: true
    tool:
      damage_per_block:                       # Optional, defaults to 1
      default_mining_speed:                   # Optional, defaults to 1.0
      rules:
        - speed: 1.0
          correct_for_drops: true             # If mining the given blocks should drop or not
          material: DIAMOND_BLOCK             # The material this rule applies to, also supports list format
          #materials:
          #  - DIAMOND_BLOCK
          #  - NETHERITE_BLOCK
          # List of all tags can be found at https://minecraft.wiki/w/Tag#Block_tags_2
          tag: minecraft:mineable/axe         # The block-tag this rule applies to, also supports list format
          #tags:
          #  - minecraft:mineable/axe
          #  - minecraft:mineable/shovel
    food:
      nutrition: 2
      saturation: 2 
      can_always_eat: false                   # Optional, default is false
      eat_seconds: 1.6                        # Optional, default is 1.6
      replacement:                            # Optional, 1.21+ only, null if not specified (aka no replacement)
        #minecraft_type: DIAMOND
        #crucible_item: crucibleid
        #eco_item: ecoid
        #mmoitems_id: id
        #mmoitems_type: type
        oraxen_item: itemid
      effects:
        mining_fatigue:
          duration: 10                        # In seconds, default is 20
          amplifier: 1
          ambient: false
          show_icon: true
          show_particles: true
          probability: 50
      jukebox_playable:
        show_in_tooltip: true
        song_key: mysong.id
```
{% endtab %}

{% tab title="1.20.5" %}
`max_stack_size` - Sets the maximum slot-size of an OraxenItem\
`enchantment_glint_override` - Sets an override-state for the enchantment glint\
`fire_resistant` - Sets whether this OraxenItem is immune to fire and lava\
`durability` - Sets the durability of this OraxenItem\
`hide_tooltip` - Hides all tooltips from the given OraxenItem on hover\
`food` - Makes this item consumable with several different properties

Example of all the above properties:

```yaml
my_item:
  itemname: <gradient:#4B36B1:#6699FF>My Item
  Components:
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
    hide_tooltip: true
    tool:
      damage_per_block:                       # Optional, defaults to 1
      default_mining_speed:                   # Optional, defaults to 1.0
      rules:
        - speed: 1.0
          correct_for_drops: true             # If mining the given blocks should drop or not
          material: DIAMOND_BLOCK             # The material this rule applies to, also supports list format
          #materials:
          #  - DIAMOND_BLOCK
          #  - NETHERITE_BLOCK
          # List of all tags can be found at https://minecraft.wiki/w/Tag#Block_tags_2
          tag: minecraft:mineable/axe         # The block-tag this rule applies to, also supports list format
          #tags:
          #  - minecraft:mineable/axe
          #  - minecraft:mineable/shovel
    food:
      nutrition: 2
      saturation: 2 
      can_always_eat: false                   # Optional, default is false
      eat_seconds: 1.6                        # Optional, default is 1.6
      replacement:                            # Optional, 1.21+ only, null if not specified (aka no replacement)
        #minecraft_type: DIAMOND
        #crucible_item: crucibleid
        #eco_item: ecoid
        #mmoitems_id: id
        #mmoitems_type: type
        oraxen_item: itemid
      effects:
        mining_fatigue:
          duration: 10                        # In seconds, default is 20
          amplifier: 1
          ambient: false
          show_icon: true
          show_particles: true
          probability: 50
```
{% endtab %}
{% endtabs %}

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

### Custom Name

This allows you to change the name displayed on the top of an item.

{% tabs %}
{% tab title="1.20.5+" %}
```yaml
my_item:
  itemname: "<red><bold>Example" #example name
  #customname: "example" #Should only be used for legacy-compatibility
```
{% endtab %}

{% tab title="1.18-1.20.4" %}
```yaml
my_item:
  displayname: "<red><bold>Example" #example name
```
{% endtab %}
{% endtabs %}

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
This does not prevent enchantments from being applied in the config.

```yaml
my_item:
  disable_enchanting: true
```

### excludeFromInventory

This option allows you to exclude an item from the oraxen inventory. It will no longer be displayed but you can still get it using [oraxen give command](../../usage/commands.md#get-the-items). It is useful for items used in other plugins like inventory icons.

```yaml
  excludeFromInventory: true
```

### unbreakable

This will make your item unbreakable (for real, using minecraft dedicated property).

```yaml
my_item:
  unbreakable: true
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
    -  attribute: GENERIC_MOVEMENT_SPEED, 
       amount: 0.1, 
       operation: 0, 
       slot: HAND
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
