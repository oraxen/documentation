---
description: Allows the creation of every kind of Chest GUI menu or shop.
---

# BossShopPro - shop

This feature is provided to you by [yzl210](https://github.com/yzl210), don't hesitate to thank him!  
Spigot link: [https://www.spigotmc.org/resources/bossshoppro.222/](https://www.spigotmc.org/resources/bossshoppro-the-most-powerful-chest-gui-shop-menu-plugin.222/)

## Menu Item

### Usage

```text
OraxenTest:
    MenuItem:
      oraxen: <oraxen item name>
      amount: <item amount(optional, default is 1)>
```

### Example

```text
OraxenTest:
    MenuItem:
      oraxen: oraxen_icon_test
```

## Reward

### Usage: \(It has the same format as ITEM\)

```text
OraxenTest:
    RewardType: ORAXEN(you can also use ORAXEN-ITEM and ITEM-ORAXEN)
    Reward:
    - - type: <oraxen item name>
      - amount: <item amount(optional, default is 1)>
```

You can add many items as you want, just put`- -` to start a new item.

### Example

```text
OraxenTest:
    RewardType: ORAXEN
    Reward:
    - - type: oraxen_item_1
      - amount: 5
    - - type: oraxen_item_2
      - amount: 10
```

## Price

### Usage: \(It has the same format as ITEM\)

```text
OraxenTest:
    PriceType: ORAXEN(you can also use ORAXEN-ITEM and ITEM-ORAXEN)
    Price:
    - - type: <oraxen item name>
      - amount: <item amount(optional, default is 1)>
```

You can add many items as you want, just put`- -` to start a new item.

### Example

```text
OraxenTest:
    PriceType: ORAXEN
    Price:
    - - type: oraxen_item_1
      - amount: 5
    - - type: oraxen_item_2
      - amount: 10
```

