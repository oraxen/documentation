---
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966830020419014666/unknown.png
coverY: 0
---

# StringBlock Mechanic

{% hint style="info" %}
only for 1.123.0+
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
  enabled: true
```

## How do I create a decoration?

### Oraxen item and Pack configuration

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

To use this mechanic you need to tell oraxen which model to use (to use the generated one, just put the id name of your item). Then you need to use custom\_variation that is not already used by another decoration (since by default 1 is used by brunnera, you can for example use 2). This example of drop settings allows you to get the drop when you mine it with a stone pickaxe.

```yaml
  Mechanics:
    stringblock:
      custom_variation: 2
      model: jasmine_flower
      hardness: 2
      drop:
        silktouch: false
        loots:
          - { oraxen_item: jasmine_flower, probability: 1.0 }
```

The other mechanics are almost the same as the custom blocks, please read their category for more information and not all of them should work correctly, just use the ones on this page.

### How do I create a decoration with my own model?

```yaml
oak_log_mini:
  displayname: "<white>oak_log_mini"
  material: PAPER
  Pack:
    generate_model: false
    model: custom/furniture/oak_log_mini
  Mechanics:
    stringblock:
      custom_variation: 3
      model: custom/furniture/oak_log_mini
      hardness: 2
      drop:
        silktouch: false
        loots:
          - { oraxen_item: oak_log_mini, probability: 1.0 }
```

![](https://cdn.discordapp.com/attachments/958524021035647046/961424759718047784/unknown.png)
