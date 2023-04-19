---
description: >-
  The different mechanics available by default and their configurations sorted
  by category
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966825489098489856/unknown.png
coverY: 0
---

# All mechanics

## Miscellaneous

### Custom Food
This mechanic allows you to set food-related properties for any food item.  
This means you can create foods which refill different amounts of hunger and saturation.  
It also lets you set a replacement item for when the food has been consumed.  

Below is a config example of the mechanic-part for a custom food:

```yaml
Mechanics:
  food:
    hunger: 10
    saturation: 10
    replacement:
      oraxen_item: any_oraxen_itemid      # Can also be minecraft_type or crucible_item
    effect_probability: 0.35              # The probability of the effect being applied, default is 1.0 / 100%
    effects:
      hunger:                             # Must be a valid potion effect, can find a list https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionEffectType.html 
        amplifier: 1                      # If not set, defaults to 0
        duration: 20                      # Duration in seconds. If not set, defaults to 1 second
        is_ambient: true                  # If not set, defaults to true
        has_particles: true               # If not set, defaults to true
        has_icon: true                    # If not set, defaults to true
      night_vision:
        duration: 60
```

### Backpack
This allows you to turn any item into a backpack.\

{% hint style="info" %}
This mechanic might cause duplication issues!\
If you find any please open a [bug-report](https://github.com/oraxen/oraxen/issues/new?assignees=&labels=bug&template=bug-report.yml&title=%5BBUG%5D+%3Cname+for+bug%3E) and we will fix them as soon as possible!\
{% endhint %}
{% hint style="warning" %}
There is currently a known dupe, if your backpack is using a stackable material like paper.\
Make sure to specify that the item should be unstackable, like shown below.\
{% endhint %}
#### Per item configuration
```yml
backpack:
  displayname: backpack
  material: PAPER
  unstackable: true #Recommend making it unstackable to avoid abovementioned dupe
  Mechanics:
    backpack:
      rows: 4
      title: "<red>Backpack"                      #Optional, Default: "Backpack"
      open_sound: "entity.shulker.open"       #Optional, Default: "entity.shulker.open"
      close_sound: "entity.shulker.close"     #Optional, Default: "entity.shulker.close"
```

### Music Disc
This allows you to make custom music discs with custom sounds.\
To add a sound simply follow the default example by adding it into `Oraxen/sound.yml`\
{% hint style="warning" %}
Any stereo sounds will not play at a specific position or following an entity.\
If you want this you need to make sure your .ogg sound-file is in mono sound format.
{% endhint %}

`song` is the namespace:sound.name as you defined it in `sound.yml`.\
If your sound.yml entry looks like this:
```yml
sounds:
  my_music_disc_song.mysong:
    category: record
    sound: mysong.ogg
```
This means your .ogg file is in the path `Oraxen/sounds/mysong.ogg`,
and your sound-ID is `my_music_disc_song.mysong` with the namespace minecraft.\
If you are importing sounds.json into another namespace, the namespace would naturally not be minecraft
```yml
Mechanics:
  music_disc:
    song: "minecraft:my_music_disc_song.mysong"
```

### Durability

This allows you to change the durability of an item created with Oraxen. Minecraft vanilla wasn't made to handle that kind of modifications, this is why this system is not perfect. You'll not see the good  durability on your item, it will just work as a percentage. What that means is that if for example you create a pickaxe based off the wooden pickaxe (which has 59 of durability by default) and you change it to 5900, you'll still see 59 of durability on your item. But you'll need to break 100 blocks in order to lose of one durability. The cool thing is that the displayed bar will be updated correctly.

#### Per item configuration

There are two options available : ratio and fixed\_amount. You can put only one of these two options on the same item. Ratio allows you to repair a percentage of your item (0.15 will repair 15% of maximum durability while 1.0 will repair it to 100%). Fixe amount repairs a fixed amount of your item durability (put 10 if you want to add 10 durability points to your item for example).

```yaml
durability:
  value: 5000 #diamond sword is 1561 by default
```

### Repair

This mechanic allows you to use an item to repair another one (which uses vanilla durability or oraxen custom). By default this mechanic is binded to iron, gold and diamond cogs. To use them you just need to click on the item you want to repair.

#### Per item configuration

```yaml
repair:
  ratio: 0.10 # 10%
  fixed_amount: 10 # or 10 durability points
```

#### Global configuration

If you enable oraxen\_durability\_only, this mechanic will only work with items using oraxen Durability mechanic.

```yaml
repair:
  enabled: true
  oraxen_durability_only: false
```

### Commands

This allows you to execute commands (as the console, a player or op player). If this option is not often the most elegant it has the merit of simplifying a lot of things. You can create a cooldown between usages, check if the player has a specific permission and use the item (understand decrease its amount by one when the command is performed).

#### Per item configuration

```yaml
commands:
  cooldown: 5 # example cooldown in seconds. This is optional
  permission: "my.awesome.perm" # required permission. This is optional
  one_usage: true # should the amount decrease when used? Default: false
  console:
    # e.g. to kill the player
    - "kill %p%"
  player:
    # e.g. the player performs /spawn
    - "spawn"
  opped_player:
    # e.g. the player gives himself a diamond sword
    - "give diamond_sword 1"
```

### PotionEffects

This allows you to bind a Potion Effect to an armor (or a hat) so that when you equip it you'll get the effect.

#### Per item configuration

[Here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/potion/PotionEffectType.html) is a list of all potion effect types available.

```yaml
armorpotioneffects:
  night_vision: # the potion effect type
    amplifier: 0
    ambient: true # Makes potion effect produce more, translucent, particles.
    particles: true # whether this effect has particles or not
    icon: true # whether this effect has an icon or not
```

### Block and NoteBlock

These mechanic allows you to use an item as block. Since these are quite special mechanics, they have a [dedicated tutorial page](../noteblock-mechanic/).

### clickAction

This mechanic allows you to run various events when a player clicks a block or furniture. It is very customizable, so it also has a [dedicated tutorial page](clickaction-mechanic.md).

### Aura

Do you want to show a cool particle effect when a player holds your item? The Aura mechanic is your way  to go. You can find a list of available particles here: [https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html)

#### Per item configuration (easy)

```yaml
aura:
  type: simple # available types: [ simple, ring, helix ]
  particle: PORTAL
```

### Hat

Do you want to create a hat? Use this mechanic so that you'll be able to put any item on your head.

#### Per item configuration (easy)

```yaml
hat:
  enabled: true
```

### Skinnable

With this mechanic, you can change the texture of an item using an item with Skin mechanic.

#### Per item configuration

```yaml
skinnable: {}
```

### ItemType

With this mechanic, you can change the item type detected by OraxenBlocks. Make sure to use a type declared [inside the block mechanic](../noteblock-mechanic/#global-configuration).&#x20;

#### Per item configuration

```yaml
itemtype:
  value: SUPER_MATERIAL # your itemType
```

### Soulbound

With this mechanic, you can avoid the players to lose their item when they die.

#### Per item configuration

```yaml
soulbound:
  lose_chance: 0
```

### Custom mechanic

This mechanic allows you to customize events, conditions and actions. Since it is a quite rspecial mechanic, it has its [dedicated tutorial page](custom-mechanic.md).

### Skin

This mechanic will allow the item to be a skin for Skinnable mechanic, skin and Skinnable item must have the same material to apply the texture.

#### Per item configuration

```yaml
skin: 
  consume: true #consume 1 skin item
```

## Combat

### Thor

Have you ever dreamed of being able to throw lightning bolts? This is for you.

#### Per item configuration

```yaml
 thor:
   lightning_bolts_amount: 5
   random_location_variation: 1.5
   delay: 20000 # in milliseconds (20000ms = 20s)
```

* **lightning\_bolts\_amount**: how many lightning bolts will be spawned?
* **random\_location\_variation**: the random variation range between bolts (in blocks)
* **delay**: delay between usage in milliseconds (1000ms = 1s)

### Lifeleech

Want to steal hearts to your opponents when you hit them?

#### Per item configuration

```yaml
lifeleech:
  amount: 2 # the amount of 1/2 hearts that you'll steal to your opponents
```

### EnergyBlast

EnergyBlast is a very cool mechanic that creates a cone of particles to attack entities.

#### Per item configuration

```yaml
energyblast:
  delay: 20000
  length: 5
  damage: 10.0
  particle:
    type: REDSTONE #Only REDSTONE particle can change size and color.
    size: 1
    color:
      red: 0
      green: 255
      blue: 255
```

### Witherskull

Send wither skulls when right clicking!

#### Per item configuration

```yaml
witherskull:
  charged: false # a charged skull can break blocks
  delay: 3000 # in milliseconds (3000ms = 3s)
```

## Farming

### Harvesting

Harvesting allows you to recolt and replant automatically wheat in a certain radius.

#### Per item configuration

```yaml
harvesting:
  cooldown: 10000 # 10 seconds between usages
  radius: 5 # blocks surrounding the clicked block
  height: 3 # high
```

### BigMining

Bigmining allows you to mine different blocks at the same time. By default this mechanic is used on the hammers and allows you to mine 3x3 square and more.

#### Per item configuration

```yaml
bigmining:
  radius: 1 # blocks surrounding the broken block
  depth: 1
```

### Smelting

Smelting allows you to instantly melt iron and gold ores when you mine them. This supports fortune and silktouch.

#### Per item configuration

```yaml
smelting:
  enabled: true
  play_sound: true
```

### BottledExp

This allows to transform your experience into bottles of experience with a right click. You can configure a loss percentage.

#### Per item configuration

The ratio corresponds to the quantity of exp transformed into a bottle for one exp.

```yaml
bottledexp:
  ratio: 0.95 # So you'll lose 1/20 of your exp by converting it
```

#### Global configuration

```yaml
bottledexp:
  enabled: true
  durability_cost: 1
```

### BedrockBreak

{% hint style="danger" %}
This mechanic depends on ProtocolLib, if you can't use ProtocolLib, you need to disable it
{% endhint %}

#### Per item configuration

The hardness is the amount of ticks between breaking animation switch and probability is the percentage of chance to get the bedrock (0.10 for 10%, 0.5 for 50% or 1.0 for 100%).

```yaml
bedrockbreak:
  hardness: 10
  probability: 1
```

#### Global configuration

If you set disable\_on\_first\_layer to true, your players will no longer be able to break the ground (layer 0), the durability\_cost is the amount of durability the item you've set bedrockbreak

```yaml
bedrockbreak:
  enabled: true
  disable_on_first_layer: false
  durability_cost: 500
```
