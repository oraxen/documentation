---
description: >-
  MythicMobs allows you to create custom mobs and bosses with advanced skills
  and attributes
---

# MythicMobs - custom mobs

This feature is provided to you by [yzl210](https://github.com/yzl210), don't hesitate to thank him!

## How to use an oraxen item for the drops?

### Usage

`oraxen [oraxen item name] [amount to drop(number or region)] [chance to drop(0-1)]`

### Example

`oraxen custom_material 3-4 0.75`  
This means that it has **75** percent chance to drop **3 to 4 custom\_material** items.

## How to equip your mob with an oraxen item?

### Usage

`oraxen [slot] [oraxen item(equipment) name]`

#### Slots

* 0, mainhand, weapon
* 1, boots, shoes
* 2, leggings, pants
* 3, chestpiece, chestplate, body
* 4, helmet, helm
* 5, shield

_5 is OffHand, but you can't put **offhand**, because MythicMobs's Author didn't put the alias._

### Example

`oraxen mainhand custom_sword`  
It means that you put a **custom\_sword** item in **MainHand**.  
`oraxen 3 custom_chestplate`  
It means that you put a **custom\_chestplate** item in **ChestPlate** slot \(as an armor\)

