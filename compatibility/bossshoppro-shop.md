---
description: Allows the creation of every kind of Chest GUI menu or shop.
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966831560231886868/unknown.png
coverY: 0
---

# BossShopPro - shop

This feature is provided to you by [yzl210](https://github.com/yzl210), don't hesitate to thank him!\
Spigot link: [https://www.spigotmc.org/resources/bossshoppro.222/](https://www.spigotmc.org/resources/bossshoppro-the-most-powerful-chest-gui-shop-menu-plugin.222/)

## Menu Item

### Usage

```
OraxenTest:
    MenuItem:
      oraxen: <oraxen item name>
      amount: <item amount(optional, default is 1)>
```

### Example

```
OraxenTest:
    MenuItem:
      oraxen: oraxen_icon_test
```

## Reward

### Usage: (It has the same format as ITEM)

```
OraxenTest:
    RewardType: ORAXEN(you can also use ORAXEN-ITEM and ITEM-ORAXEN)
    Reward:
    - - type: <oraxen item name>
      - amount: <item amount(optional, default is 1)>
```

You can add many items as you want, just put`- -` to start a new item.

### Example

```
OraxenTest:
    RewardType: ORAXEN
    Reward:
    - - type: oraxen_item_1
      - amount: 5
    - - type: oraxen_item_2
      - amount: 10
```

## Price

### Usage: (It has the same format as ITEM)

```
OraxenTest:
    PriceType: ORAXEN(you can also use ORAXEN-ITEM and ITEM-ORAXEN)
    Price:
    - - type: <oraxen item name>
      - amount: <item amount(optional, default is 1)>
```

You can add many items as you want, just put`- -` to start a new item.

### Example

```
OraxenTest:
    PriceType: ORAXEN
    Price:
    - - type: oraxen_item_1
      - amount: 5
    - - type: oraxen_item_2
      - amount: 10
```
