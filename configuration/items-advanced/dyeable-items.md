---
cover: >-
  https://cdn.discordapp.com/attachments/896841738621177896/966834695058890772/unknown.png
coverY: 0
---

# Dyeable Items

### Introduction

Oraxen allows you to create paintable items and furtniture based on `POTION` and `LEATHER_HORSE_ARMOR`, so let's first see how to do it in BlockBench!

### How do I do this?

#### First step open your Blockbench model

![](https://cdn.discordapp.com/attachments/896841738621177896/966749278615764992/IMG\_20220421\_121428.png)

#### Select the face to be painted

![](https://cdn.discordapp.com/attachments/896841738621177896/966749278850670592/IMG\_20220421\_121444.png)

#### Activate the `tint` option

{% hint style="info" %}
Use white to paint better
{% endhint %}

![](https://cdn.discordapp.com/attachments/896841738621177896/966749279102308413/IMG\_20220421\_121505.png)

![](https://cdn.discordapp.com/attachments/896841738621177896/966749279349776424/IMG\_20220421\_121543.png)

#### And select all the faces of your model with the option!

{% embed url="https://cdn.discordapp.com/attachments/896841738621177896/966749279584649287/IMG_20220421_121603.png" %}

```yaml
clock:
  displayname: "<white>Clock"
  material: LEATHER_HORSE_ARMOR
  color: 255, 255, 255 #rgb
  Mechanics:
    furniture:
      barrier: false
      drop: # useless if you are not using a barrier
        silktouch: false
        loots:
          - { oraxen_item: clock, probability: 1.0 }
  Pack:
    generate_model: false
    model: custom/furniture/clock
```
